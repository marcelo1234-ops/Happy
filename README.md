<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Happy birthday, Wes!</title>
<style>
  :root {
    --bg: #3b1f6b;
    --env: #5a34a0;
    --env-front: #6a41b5;
    --env-flap: #7a50c6;
    --paper: #fbf6ea;
    --ink: #3b1f6b;
    --muted: #c9b8e8;
  }
  * { box-sizing: border-box; margin: 0; }
  body {
    min-height: 100vh;
    background:
      radial-gradient(circle at 15% 12%, rgba(255, 111, 165, .30), transparent 38%),
      radial-gradient(circle at 88% 85%, rgba(255, 209, 102, .22), transparent 40%),
      radial-gradient(circle at 85% 20%, rgba(53, 208, 186, .18), transparent 35%),
      radial-gradient(rgba(255, 255, 255, .13) 2px, transparent 2.6px) 0 0 / 30px 30px,
      var(--bg);
    color: var(--ink);
    font-family: Georgia, "Times New Roman", serif;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 24px;
    overflow-x: hidden;
  }
  main { position: relative; z-index: 1; width: 100%; max-width: 420px; }

  /* ---------- Decoração de aniversário ---------- */
  .bunting { position: absolute; top: 0; left: 0; width: 100%; height: 50px; pointer-events: none; z-index: 0; }
  .balao {
    position: fixed; bottom: -150px; z-index: 0; pointer-events: none;
    width: 54px; height: 68px;
    border-radius: 50% 50% 48% 48% / 55% 55% 45% 45%;
    background:
      radial-gradient(circle at 32% 28%, rgba(255, 255, 255, .55) 0 9%, transparent 10%),
      var(--c);
    opacity: .85;
    animation: sobe var(--d) linear var(--delay) infinite;
  }
  .balao::before {
    content: ""; position: absolute; left: 50%; bottom: -5px;
    width: 9px; height: 9px; background: var(--c);
    transform: translateX(-50%) rotate(45deg);
  }
  .balao::after {
    content: ""; position: absolute; left: 50%; top: 100%;
    width: 1.5px; height: 70px; background: rgba(255, 255, 255, .5);
  }
  @keyframes sobe {
    0%   { transform: translate(0, 0) rotate(-4deg); }
    50%  { transform: translate(16px, -65vh) rotate(4deg); }
    100% { transform: translate(-8px, -135vh) rotate(-4deg); }
  }
  .confete { position: fixed; inset: 0; pointer-events: none; z-index: 20; overflow: hidden; }
  .confete i { position: absolute; display: block; }

  /* ---------- Envelope ---------- */
  .stage { position: relative; padding-top: 25%; }
  .envelope {
    position: relative;
    width: 100%;
    aspect-ratio: 3 / 2;
    background: repeating-linear-gradient(135deg, #3d2270 0 6px, #46287d 6px 12px);
    border-radius: 6px;
    box-shadow: 0 18px 40px rgba(10, 0, 30, .45);
  }

  /* ---------- Folha ---------- */
  .letter {
    position: absolute;
    left: 7%; right: 7%; top: 8%; height: 80%;
    background:
      repeating-linear-gradient(90deg, #ff6fa5 0 14px, #ffd166 14px 28px, #35d0ba 28px 42px, #b79cff 42px 56px) top / 100% 6px no-repeat,
      radial-gradient(circle at 9% 22%, #ff6fa5 0 3px, transparent 3.6px),
      radial-gradient(circle at 91% 30%, #35d0ba 0 3px, transparent 3.6px),
      radial-gradient(circle at 84% 14%, #ffd166 0 4px, transparent 4.6px),
      radial-gradient(circle at 14% 40%, #b79cff 0 3px, transparent 3.6px),
      var(--paper);
    border-radius: 4px;
    z-index: 2;
    padding: 20px 16px;
    overflow: hidden;
    text-align: center;
    box-shadow: 0 2px 8px rgba(10, 0, 30, .3);
  }
  .letter::after {
    content: ""; position: absolute; left: 0; right: 0; bottom: 0; height: 45%;
    background: linear-gradient(to top, var(--paper) 20%, rgba(251, 246, 234, 0));
    pointer-events: none;
  }
  .open.full .letter::after { display: none; }
  .letter h2 { font-size: clamp(1.3rem, 6vw, 1.8rem); line-height: 1.15; color: #c2185b; }
  .letter p { margin-top: 10px; font-size: .95rem; line-height: 1.45; }

  .open .letter { cursor: pointer; animation: papel 1.6s ease-out .6s both; }
  @keyframes papel {
    0%   { transform: translateY(0) rotate(0); }
    70%  { transform: translateY(-62%) rotate(-2deg); }
    100% { transform: translateY(-58%) rotate(0); }
  }

  /* ---------- Dica de toque: bolinha pulsando com dedo ---------- */
  .hint {
    position: absolute; left: 50%; bottom: 10px;
    width: 56px; height: 56px; margin-left: -28px;
    pointer-events: none;
    opacity: 0;
    z-index: 1;
  }
  .open .hint { animation: hintIn .5s ease 2.3s forwards; }
  .open.full .hint { display: none; }
  /* Dica no selo: primeiro toque */
  .hint-selo {
    position: absolute; left: 50%; top: 55%;
    width: 56px; height: 56px; margin: -28px 0 0 -28px;
    pointer-events: none; z-index: 7;
    opacity: 0;
    animation: hintIn .5s ease 1s forwards;
  }
  .open .hint-selo { display: none; }
  @keyframes hintIn { to { opacity: 1; } }
  .ring {
    position: absolute; inset: 0;
    border-radius: 50%;
    background: rgba(255, 111, 165, .30);
    border: 2px solid rgba(214, 51, 108, .6);
    animation: pulso 1.6s ease-in-out infinite;
  }
  @keyframes pulso {
    0%, 100% { transform: scale(.75); opacity: .9; }
    50%      { transform: scale(1.25); opacity: .35; }
  }
  .dedo {
    position: absolute; left: 50%; top: 50%;
    font-size: 1.7rem; line-height: 1;
    transform: translate(-50%, -12%);
    animation: toque 1.6s ease-in-out infinite;
  }
  @keyframes toque {
    0%, 100% { transform: translate(-50%, -12%); }
    50%      { transform: translate(-50%, -2%) scale(.92); }
  }

  /* Folha completa: ocupa a tela, com rolagem se o texto for grande */
  .open.full .letter {
    position: fixed; inset: 0; margin: auto;
    width: min(92vw, 460px);
    height: fit-content;
    max-height: 88vh;
    overflow-y: auto;
    z-index: 7;
    padding: 32px 24px;
    animation: none;
    transform: none;
    cursor: default;
    box-shadow: 0 0 0 100vmax rgba(10, 0, 30, .6), 0 14px 34px rgba(0, 0, 0, .4);
  }
  .open.full .letter h2 { font-size: clamp(1.7rem, 8vw, 2.2rem); }
  .open.full .letter p { font-size: 1.05rem; }

  /* ---------- Frente, aba e selo ---------- */
  /* ---------- Páginas e setinha ---------- */
  .pagina-2, .nav { display: none; }
  .open.full .nav {
    display: flex; justify-content: flex-end;
    position: sticky; bottom: 0; margin-top: 14px;
    pointer-events: none;
  }
  .open.full.p2 .nav { justify-content: flex-start; }
  .open.full.p2 .pagina-1 { display: none; }
  .open.full.p2 .pagina-2 { display: block; animation: folheia .45s ease both; }
  .open.full.voltou:not(.p2) .pagina-1 { animation: folheia .45s ease both; }
  @keyframes folheia {
    from { opacity: 0; transform: translateX(14px); }
    to   { opacity: 1; transform: none; }
  }
  .seta {
    pointer-events: auto;
    width: 44px; height: 44px; border-radius: 50%;
    border: 0; cursor: pointer;
    background: #d6336c;
    display: grid; place-items: center;
    box-shadow: 0 3px 10px rgba(10, 0, 30, .35);
  }
  .p2 .seta { transform: scaleX(-1); }
  .seta svg { animation: bob 1.4s ease-in-out infinite; }
  @keyframes bob {
    0%, 100% { transform: translateX(-1px); }
    50%      { transform: translateX(3px); }
  }

  .edge-shadow, .creases {
    position: absolute; inset: 0; width: 100%; height: 100%;
    pointer-events: none;
  }
  .edge-shadow { z-index: 2; filter: blur(5px); opacity: .45; clip-path: inset(0 round 6px); }
  .creases { z-index: 3; }

  .front {
    position: absolute; inset: 0;
    background: linear-gradient(160deg, var(--env-front), var(--env));
    clip-path: polygon(0 0, 50% 55%, 100% 0, 100% 100%, 0 100%);
    border-radius: 6px;
    z-index: 3;
  }
  .flap {
    position: absolute; top: 0; left: 0; width: 100%; height: 55%;
    transform-origin: top center;
    transform: perspective(900px) rotateX(0deg);
    transform-style: preserve-3d;
    z-index: 4;
    transition: transform .6s ease, z-index 0s .3s;
  }
  .flap i {
    position: absolute; inset: 0;
    clip-path: polygon(0 0, 100% 0, 50% 100%);
    backface-visibility: hidden;
  }
  .f-front { background: linear-gradient(180deg, #8359cf, var(--env-flap)); }
  .f-back {
    background: repeating-linear-gradient(135deg, #4f2f8f 0 6px, #583699 6px 12px);
    transform: rotateY(180deg);
  }
  .seal {
    border: 0; padding: 0; cursor: pointer; font-family: inherit;
    position: absolute; left: 50%; top: 55%;
    width: 15%; aspect-ratio: 1;
    transform: translate(-50%, -50%);
    border-radius: 50%;
    background: radial-gradient(circle at 35% 30%, #ffe08a, #e0a526 70%);
    box-shadow: 0 3px 8px rgba(0,0,0,.35);
    z-index: 6;
    display: grid; place-items: center;
    color: #8a5a00; font-weight: 700; font-size: clamp(.8rem, 4vw, 1.1rem);
    transition: opacity .3s;
  }
  .open .flap { transform: perspective(900px) rotateX(180deg); z-index: 1; }
  .seal::after { content: ""; position: absolute; inset: -12px; border-radius: 50%; }
  .open .seal { opacity: 0; pointer-events: none; }

  /* ---------- Bonequinho ---------- */
  .doll {
    position: absolute; left: 50%; top: 55%;
    width: 14%; margin-left: -7%;
    transform-origin: 50% 0;
    z-index: 5;
    animation: swing 3.2s ease-in-out infinite;
  }
  .doll svg { display: block; width: 100%; height: auto; overflow: visible; }
  @keyframes swing {
    0%, 100% { transform: rotate(-9deg); }
    50%      { transform: rotate(9deg); }
  }
  .open .doll { animation: cair .9s cubic-bezier(.5,0,1,.6) forwards; }
  @keyframes cair {
    0%   { transform: rotate(0) translateY(0); opacity: 1; }
    15%  { transform: rotate(-6deg) translateY(0); opacity: 1; }
    100% { transform: rotate(35deg) translateY(340px); opacity: 0; }
  }
  .gone { display: none; }

  :focus-visible { outline: 3px solid #ffd166; outline-offset: 3px; }

  @media (prefers-reduced-motion: reduce) {
    .flap, .seal { transition: none; }
    .doll { animation: none; }
    .open .doll { opacity: 0; }
    .balao { animation: none; bottom: 8%; }
    .ring, .dedo, .seta svg { animation: none; }
    .open.full.p2 .pagina-2, .open.full.voltou:not(.p2) .pagina-1 { animation: none; }
    .open .hint { animation: none; opacity: 1; }
    .hint-selo { animation: none; opacity: 1; }
    .open:not(.full) .letter { animation: none; transform: translateY(-58%); }
  }
</style>
</head>
<body>
<svg class="bunting" aria-hidden="true">
  <defs>
    <pattern id="flags" width="168" height="50" patternUnits="userSpaceOnUse">
      <path d="M0,2 Q42,26 84,2 Q126,26 168,2" fill="none" stroke="rgba(255,255,255,.55)" stroke-width="1.4"/>
      <polygon points="12,10.5 30,10.5 21,28" fill="#ff6fa5"/>
      <polygon points="33,13.5 51,13.5 42,31" fill="#ffd166"/>
      <polygon points="54,10.5 72,10.5 63,28" fill="#35d0ba"/>
      <polygon points="96,10.5 114,10.5 105,28" fill="#ff9f5a"/>
      <polygon points="117,13.5 135,13.5 126,31" fill="#b79cff"/>
      <polygon points="138,10.5 156,10.5 147,28" fill="#ffd166"/>
    </pattern>
  </defs>
  <rect width="100%" height="50" fill="url(#flags)"/>
</svg>
<span class="balao" style="left:5%;  --c:#ff6fa5; --d:19s; --delay:-4s"></span>
<span class="balao" style="left:24%; --c:#ffd166; --d:23s; --delay:-14s"></span>
<span class="balao" style="left:50%; --c:#35d0ba; --d:21s; --delay:-9s"></span>
<span class="balao" style="left:72%; --c:#b79cff; --d:25s; --delay:-18s"></span>
<span class="balao" style="left:89%; --c:#ff9f5a; --d:20s; --delay:-1s"></span>
<main id="app">
  <div class="stage">
    <div class="envelope">
      <div class="letter" id="folha" tabindex="-1" aria-label="Open the letter">
        <div class="pagina pagina-1">
        <h2>Happy birthday, Wes!</h2>
        <p lang="ru">Сегодня твой день, очень особенный день.</p>
        <p lang="ja">あなたはまた一つ年を重ねましたね。</p>
        <p lang="es">Aunque ya no estemos juntos y estemos lejos, me importas.</p>
        <p lang="zh">你曾经是我生命中的一部分，</p>
        <p lang="hi">वह समय मेरे जीवन का सबसे अच्छा समय था,</p>
        <p lang="tr">ve bu hediyenin karşılığını sana nasıl vereceğimi bilmiyorum.</p>
        <p lang="fr">Je n’ai pas grand-chose à offrir,</p>
        <p lang="de">deshalb habe ich mir etwas Zeit genommen, um diese kleine Website zu erstellen,</p>
        <p lang="it">per ricordarti che puoi contare su di me,</p>
        <p lang="ko">우리가 이야기하기 어려울 때도요.</p>
        <p lang="ar" dir="rtl">عناق لك، واعلم أنك شخص لطيف، ولا تتوقف أبدًا عن كونك كذلك.</p>
        </div>
        <div class="pagina pagina-2" lang="pt-BR">
          <h2>Tradução</h2>
          <p>Hoje é o seu dia, um dia muito especial.</p>
          <p>Você completou mais um ano de vida.</p>
          <p>Mesmo que já não estejamos juntos e estejamos distantes, eu me importo com você.</p>
          <p>Você já foi uma parte da minha vida,</p>
          <p>aquele tempo foi o melhor da minha vida,</p>
          <p>e não sei como retribuir este presente.</p>
          <p>Não tenho muito a oferecer,</p>
          <p>então reservei um tempo para criar este pequeno site,</p>
          <p>para te lembrar de que você pode contar comigo,</p>
          <p>até mesmo quando é difícil conversarmos.</p>
          <p>Um abraço para você, e saiba que você é uma pessoa gentil, e nunca deixe de ser.</p>
        </div>
        <div class="nav">
          <button class="seta" id="seta" type="button" aria-label="Próxima página: tradução">
            <svg viewBox="0 0 24 24" width="22" height="22" aria-hidden="true"><path d="M9 5l7 7-7 7" fill="none" stroke="#fbf6ea" stroke-width="2.6" stroke-linecap="round" stroke-linejoin="round"/></svg>
          </button>
        </div>
        <span class="hint" aria-hidden="true"><i class="ring"></i><span class="dedo">👆</span></span>
      </div>
      <svg class="edge-shadow" viewBox="0 0 300 200" preserveAspectRatio="none" aria-hidden="true">
        <polygon points="0,0 150,110 300,0 300,200 0,200" fill="#14052e"/>
      </svg>
      <div class="front"></div>
      <svg class="creases" viewBox="0 0 300 200" preserveAspectRatio="none" aria-hidden="true">
        <g stroke="rgba(255,255,255,.16)" stroke-width="1" fill="none" vector-effect="non-scaling-stroke">
          <line x1="0" y1="0" x2="150" y2="110" vector-effect="non-scaling-stroke"/>
          <line x1="300" y1="0" x2="150" y2="110" vector-effect="non-scaling-stroke"/>
          <line x1="0" y1="200" x2="150" y2="110" vector-effect="non-scaling-stroke"/>
          <line x1="300" y1="200" x2="150" y2="110" vector-effect="non-scaling-stroke"/>
        </g>
      </svg>
      <div class="flap"><i class="f-front"></i><i class="f-back"></i></div>
      <div class="doll" aria-hidden="true">
        <svg viewBox="0 0 60 100" xmlns="http://www.w3.org/2000/svg">
          <line x1="30" y1="0" x2="30" y2="22" stroke="#f6f0ff" stroke-width="1.6"/>
          <g stroke="#fbf6ea" stroke-width="4.5" stroke-linecap="round" fill="none">
            <line x1="22" y1="52" x2="9" y2="64"/>
            <line x1="38" y1="52" x2="51" y2="64"/>
            <line x1="25" y1="72" x2="23" y2="92"/>
            <line x1="35" y1="72" x2="37" y2="92"/>
          </g>
          <rect x="19" y="45" width="22" height="28" rx="9" fill="#ffd166"/>
          <circle cx="30" cy="34" r="13" fill="#fbf6ea"/>
          <circle cx="25.5" cy="32" r="1.8" fill="#3b1f6b"/>
          <circle cx="34.5" cy="32" r="1.8" fill="#3b1f6b"/>
          <path d="M25 38 Q30 43 35 38" stroke="#3b1f6b" stroke-width="1.8" fill="none" stroke-linecap="round"/>
          <circle cx="22" cy="37" r="2" fill="#f4a6c0" opacity=".8"/>
          <circle cx="38" cy="37" r="2" fill="#f4a6c0" opacity=".8"/>
        </svg>
      </div>
      <button class="seal" id="selo" type="button" aria-label="Abrir o envelope">★</button>
      <span class="hint-selo" aria-hidden="true"><i class="ring"></i><span class="dedo">👆</span></span>
    </div>
  </div>
</main>


<script>
  const app = document.getElementById("app");
  const folha = document.getElementById("folha");

  // Confete quando o envelope abre
  function confete() {
    if (matchMedia("(prefers-reduced-motion: reduce)").matches) return;
    const r = app.querySelector(".envelope").getBoundingClientRect();
    const cx = r.left + r.width / 2, cy = r.top + r.height * 0.2;
    const cores = ["#ff6fa5", "#ffd166", "#35d0ba", "#ff9f5a", "#b79cff", "#ffffff"];
    const box = document.createElement("div");
    box.className = "confete";
    document.body.appendChild(box);
    for (let i = 0; i < 70; i++) {
      const p = document.createElement("i");
      const w = 6 + Math.random() * 6, h = w * (0.4 + Math.random() * 0.8);
      p.style.cssText = `left:${cx}px;top:${cy}px;width:${w}px;height:${h}px;background:${cores[i % cores.length]};border-radius:${Math.random() < .3 ? "50%" : "1px"}`;
      box.appendChild(p);
      const ang = -Math.PI / 2 + (Math.random() - .5) * Math.PI * 1.1;
      const v = 120 + Math.random() * 220;
      const dx = Math.cos(ang) * v, dy = Math.sin(ang) * v;
      const queda = window.innerHeight + 100 - cy;
      const rot = (Math.random() - .5) * 900;
      p.animate([
        { transform: "translate(0,0) rotate(0deg)", easing: "cubic-bezier(.1,.7,.3,1)" },
        { transform: `translate(${dx}px,${dy}px) rotate(${rot * .4}deg)`, easing: "cubic-bezier(.5,0,.9,.6)", offset: .3 },
        { transform: `translate(${dx * 1.3}px,${queda}px) rotate(${rot}deg)` }
      ], { duration: 2200 + Math.random() * 1400, delay: Math.random() * 150, fill: "forwards" });
    }
    setTimeout(() => box.remove(), 4200);
  }

  // Música calma de piano suave (criada no código, sem arquivo)
  const BPM = 62, B = 60 / BPM;
  // [baixo, acorde (4 notas), melodia [freq, início em tempos, duração em tempos]]
  const COMPASSOS = [
    [110.00, [220.00, 261.63, 329.63, 392.00], [[659.25,0,3],[587.33,3,1]]],
    [87.31,  [174.61, 220.00, 261.63, 329.63], [[523.25,0,2],[440.00,2,2]]],
    [130.81, [261.63, 329.63, 392.00, 493.88], [[659.25,0,3],[587.33,3,1]]],
    [98.00,  [196.00, 246.94, 293.66, 392.00], [[587.33,0,2],[493.88,2,2]]],
    [110.00, [220.00, 261.63, 329.63, 392.00], [[523.25,0,2],[659.25,2,2]]],
    [87.31,  [174.61, 220.00, 261.63, 329.63], [[440.00,0,2],[523.25,2,2]]],
    [130.81, [261.63, 329.63, 392.00, 493.88], [[659.25,0,2],[783.99,2,1],[659.25,3,1]]],
    [98.00,  [196.00, 246.94, 293.66, 392.00], [[587.33,0,4]]]
  ];
  const DURACAO_LOOP = 34 * B; // 8 compassos de 4 tempos + 2 de pausa
  const PIANO = [[1, 1], [2, .35], [3, .12]];
  let audioCtx = null, master = null, bus = null;
  let musicaIniciada = false, musicaLigada = false;

  function criarAudio() {
    const AC = window.AudioContext || window.webkitAudioContext;
    if (!AC) return false;
    if (audioCtx) return true;
    audioCtx = new AC();
    master = audioCtx.createGain(); master.gain.value = 0; master.connect(audioCtx.destination);
    bus = audioCtx.createGain();
    const quente = audioCtx.createBiquadFilter(); quente.type = "lowpass"; quente.frequency.value = 1800;
    bus.connect(quente); quente.connect(master);
    // eco suave
    const eco = audioCtx.createDelay(); eco.delayTime.value = .5;
    const fb = audioCtx.createGain(); fb.gain.value = .38;
    const lp = audioCtx.createBiquadFilter(); lp.type = "lowpass"; lp.frequency.value = 1500;
    bus.connect(eco); eco.connect(lp); lp.connect(fb); fb.connect(eco); lp.connect(master);
    return true;
  }
  function nota(freq, t, dur, vol, parciais) {
    const g = audioCtx.createGain();
    g.gain.setValueAtTime(0, t);
    g.gain.linearRampToValueAtTime(vol, t + .02);
    g.gain.exponentialRampToValueAtTime(.0001, t + dur);
    g.connect(bus);
    parciais.forEach(([mult, amp]) => {
      const o = audioCtx.createOscillator(), og = audioCtx.createGain();
      o.type = "sine"; o.frequency.value = freq * mult; og.gain.value = amp;
      o.connect(og); og.connect(g);
      o.start(t); o.stop(t + dur + .05);
    });
  }
  function loopMusica(t0) {
    const ordem = [0, 1, 2, 3, 2, 1, 2, 1]; // arpejo suave
    COMPASSOS.forEach(([baixo, acorde, melodia], i) => {
      const tb = t0 + i * 4 * B;
      nota(baixo, tb, 3.6, .2, PIANO);
      ordem.forEach((idx, k) => nota(acorde[idx], tb + k * B / 2, 1.6, .075, PIANO));
      melodia.forEach(([f, inicio, dur]) => nota(f, tb + inicio * B, dur * B + 1.2, .15, PIANO));
    });
    const proximo = t0 + DURACAO_LOOP;
    setTimeout(() => loopMusica(proximo), Math.max(0, (proximo - audioCtx.currentTime - 2) * 1000));
  }
  function ligarMusica() {
    musicaLigada = true;
    master.gain.setTargetAtTime(.35, audioCtx.currentTime, .4);
    if (!musicaIniciada) { musicaIniciada = true; loopMusica(audioCtx.currentTime + .15); }
  }
  // O navegador só libera som depois de um toque; se estiver bloqueado, começa no primeiro toque na folha
  function tentarMusica(gesto) {
    if (musicaIniciada || !criarAudio()) return;
    if (audioCtx.state === "running") ligarMusica();
    else if (gesto) audioCtx.resume().then(ligarMusica);
  }

  // Toque 1: o selo abre o envelope (toque 2: a folha sai; toque 3: a setinha vira a página)
  const selo = document.getElementById("selo");
  function abrir() {
    if (app.classList.contains("open")) return;
    app.classList.add("open");
    folha.tabIndex = 0;
    folha.setAttribute("role", "button");
    tentarMusica(true);
    setTimeout(confete, 400);
    // Depois que o bonequinho cai, ele é removido da página
    setTimeout(() => app.querySelector(".doll").classList.add("gone"), 1300);
  }
  selo.addEventListener("click", abrir);


  // Ao tocar na folha, ela sai completa do envelope
  function tirar() {
    if (!app.classList.contains("open") || app.classList.contains("full")) return;
    const a = folha.getBoundingClientRect();
    app.classList.add("full");
    folha.removeAttribute("role");
    folha.removeAttribute("tabindex");
    const b = folha.getBoundingClientRect();
    if (!matchMedia("(prefers-reduced-motion: reduce)").matches) {
      folha.animate([
        { transformOrigin: "top left", transform: `translate(${a.left - b.left}px, ${a.top - b.top}px) scale(${a.width / b.width})` },
        { transformOrigin: "top left", transform: "none" }
      ], { duration: 700, easing: "cubic-bezier(.2,.8,.2,1)" });
    }
  }
  folha.addEventListener("click", () => { tentarMusica(true); tirar(); });
  folha.addEventListener("keydown", e => {
    if (e.target === folha && (e.key === "Enter" || e.key === " ")) { e.preventDefault(); tentarMusica(true); tirar(); }
  });

  // Setinha no canto: vai para a tradução e volta
  const seta = document.getElementById("seta");
  seta.addEventListener("click", () => {
    const p2 = app.classList.toggle("p2");
    if (!p2) app.classList.add("voltou");
    folha.scrollTop = 0;
    seta.setAttribute("aria-label", p2 ? "Voltar para a carta" : "Próxima página: tradução");
  });
</script>
</body>
</html>
