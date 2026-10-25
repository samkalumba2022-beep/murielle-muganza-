# <!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Pour Murielle</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=Nunito:wght@400;700&display=swap" rel="stylesheet">
<style>
:root{--bg:#fff1ee;--card:#ffffff;--ink:#4a1d33;--soft:#8a5a6e;--rose:#e8497a;--gold:#f2a65a;--line:#f3cfd6;color-scheme:light;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#2a0f22;--card:#3d1830;--ink:#ffe9ee;--soft:#d9a9bb;--rose:#ff6b97;--gold:#ffbe7a;--line:#5a2a45;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#2a0f22;--card:#3d1830;--ink:#ffe9ee;--soft:#d9a9bb;--rose:#ff6b97;--gold:#ffbe7a;--line:#5a2a45;color-scheme:dark}
*{box-sizing:border-box}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--ink);font-family:Nunito,system-ui,sans-serif;line-height:1.5;min-height:100vh;overflow-x:hidden}
main{max-width:480px;margin:0 auto;padding:28px 18px 60px}
h1,h2{font-family:"DM Serif Display",Georgia,serif;font-weight:400;margin:0}
h1{font-size:2.5rem;line-height:1.15;text-align:center;margin-top:14px}
.big{font-size:3.4rem;text-align:center;margin-top:10px}
.sub{text-align:center;color:var(--soft);margin:10px 0 26px}
.menu{display:grid;gap:12px}
.btn{font:inherit;font-weight:700;border:0;border-radius:18px;padding:16px 18px;background:var(--rose);color:#fff;cursor:pointer;width:100%;text-align:left;font-size:1.1rem}
.btn small{display:block;font-weight:400;opacity:.92}
.btn.alt{background:var(--card);color:var(--ink);border:2px solid var(--line)}
.btn:focus-visible,.cell:focus-visible,.gift:focus-visible,.petal:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
.back{background:none;border:0;color:var(--soft);font:inherit;cursor:pointer;padding:6px 0;margin-bottom:8px}
.panel{display:none}.panel.on{display:block}
.bar{text-align:center;color:var(--soft);font-weight:700;margin:12px 0 16px}
.grid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px}
.cell{aspect-ratio:1;border-radius:16px;border:2px solid var(--line);background:var(--card);font-size:2.2rem;cursor:pointer;display:grid;place-items:center;padding:0;color:var(--ink)}
.cell.hide{background:var(--rose);border-color:var(--rose);color:transparent}
.cell.done{background:var(--gold);border-color:var(--gold)}
.msg{text-align:center;padding:22px 8px}
.msg h2{font-size:1.8rem;margin-bottom:8px}
.flower{position:relative;width:280px;height:280px;margin:14px auto}
.center{position:absolute;left:105px;top:105px;width:70px;height:70px;border-radius:50%;background:var(--gold);display:grid;place-items:center;font-size:1.8rem}
.petal{position:absolute;left:115px;top:10px;width:50px;height:95px;border-radius:50% 50% 50% 50%/70% 70% 30% 30%;background:#fff;border:2px solid var(--line);cursor:pointer;transform-origin:25px 130px;padding:0;transition:transform .5s,opacity .5s}
.petal.gone{opacity:0;pointer-events:none}
.say{min-height:2.6em;text-align:center;font-family:"DM Serif Display",Georgia,serif;font-size:1.6rem;color:var(--rose)}
.gifts{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:16px 0}
.gift{aspect-ratio:1;font-size:3rem;background:var(--card);border:2px solid var(--line);border-radius:20px;cursor:pointer;padding:0}
.gift.open{background:var(--gold);border-color:var(--gold)}
.note{background:var(--card);border:2px solid var(--line);border-radius:18px;padding:20px;text-align:center;min-height:90px;display:grid;place-items:center}
.letter{background:var(--card);border:2px solid var(--line);border-radius:18px;padding:22px;margin-top:18px;white-space:pre-line}
@media (prefers-reduced-motion:reduce){.petal{transition:none}}
</style>
</head>
<body>
<main>
<section id="home" class="panel on">
  <div class="big">🧸</div>
  <h1>Pour Murielle</h1>
  <p class="sub">Trois petits jeux tout doux, faits avec amour.</p>
  <div class="menu">
    <button class="btn" data-go="flower">🌼 La marguerite<small>Effeuille-la pour voir</small></button>
    <button class="btn" data-go="gifts">🎁 Les cadeaux surprises<small>Ouvre-les un par un</small></button>
    <button class="btn" data-go="memo">🐻 Les petits animaux<small>Retrouve les paires</small></button>
    <button class="btn alt" data-go="letter">💌 Ma lettre pour toi</button>
  </div>
</section>

<section id="flower" class="panel">
  <button class="back" data-go="home">← Retour</button>
  <h2>La marguerite</h2>
  <p class="sub" style="margin:6px 0">Touche un pétale pour l’effeuiller.</p>
  <div class="flower" id="fl"><div class="center">💛</div></div>
  <div class="say" id="say" aria-live="polite"></div>
  <p style="text-align:center"><button class="btn" id="flAgain" style="width:auto;text-align:center">Recommencer</button></p>
</section>

<section id="gifts" class="panel">
  <button class="back" data-go="home">← Retour</button>
  <h2>Les cadeaux surprises</h2>
  <div class="gifts" id="gf"></div>
  <div class="note" id="note">Choisis un cadeau.</div>
</section>

<section id="memo" class="panel">
  <button class="back" data-go="home">← Retour</button>
  <h2>Les petits animaux</h2>
  <div class="bar">Coups : <b id="mMoves">0</b></div>
  <div class="grid" id="mGrid"></div>
  <div class="msg" id="mEnd" hidden><h2>Bravo Murielle ! 🎉</h2><p id="mEndTxt"></p><button class="btn" id="mAgain" style="text-align:center">Rejouer</button></div>
</section>

<section id="letter" class="panel">
  <button class="back" data-go="home">← Retour</button>
  <h2>Ma lettre pour toi</h2>
  <div class="letter" id="letterTxt"></div>
</section>
</main>

<script>
var NAME = "Murielle";
document.getElementById("letterTxt").textContent =
  "Pour " + NAME + ",\n\nTu rends mes journées plus douces et mes projets plus beaux. Merci d’être là, de me soutenir, et de me faire sourire même quand tout est compliqué.\n\nCes petits jeux sont ma façon de te dire que je pense à toi. Je t’aime, mon amour.";

function show(id){
  document.querySelectorAll(".panel").forEach(function(p){p.classList.toggle("on", p.id===id)});
  if(id==="flower") flowerStart();
  if(id==="gifts") giftsStart();
  if(id==="memo") memoStart();
  window.scrollTo(0,0);
}
document.addEventListener("click", function(e){
  var b = e.target.closest("[data-go]"); if(b) show(b.getAttribute("data-go"));
});

/* Marguerite */
var SAYS=["Je t’aime…","un peu…","beaucoup…","passionnément…","à la folie…","tendrement…","sans fin…","POUR TOUJOURS 💖"], fcount=0;
function flowerStart(){
  var fl=document.getElementById("fl");
  fl.querySelectorAll(".petal").forEach(function(p){p.remove()});
  fcount=0; document.getElementById("say").textContent="";
  for(var i=0;i<8;i++){
    var p=document.createElement("button"); p.className="petal"; p.setAttribute("aria-label","Pétale "+(i+1));
    p.style.transform="rotate("+(i*45)+"deg)";
    p.addEventListener("click", petalTap); fl.appendChild(p);
  }
}
function petalTap(e){
  var p=e.currentTarget; if(p.classList.contains("gone")) return;
  p.classList.add("gone");
  document.getElementById("say").textContent=SAYS[fcount]; fcount++;
}
document.getElementById("flAgain").addEventListener("click", flowerStart);

/* Cadeaux */
var GIFTS=["Tu es la plus belle chose qui me soit arrivée. 🌹","Ton sourire illumine toutes mes journées. ☀️","Avec toi, je me sens chez moi. 🏡"];
function giftsStart(){
  var g=document.getElementById("gf"); g.innerHTML=""; document.getElementById("note").textContent="Choisis un cadeau.";
  GIFTS.forEach(function(txt){
    var b=document.createElement("button"); b.className="gift"; b.textContent="🎁"; b.setAttribute("aria-label","Cadeau surprise");
    b.addEventListener("click", function(){b.classList.add("open");b.textContent="💝";document.getElementById("note").textContent=txt});
    g.appendChild(b);
  });
}

/* Mémoire */
var EMO=["🐻","🐰","🐱","🐼","🦊","🐥"], first=null, lock=false, moves=0, pairs=0;
function memoStart(){
  var deck=EMO.concat(EMO).sort(function(){return Math.random()-.5});
  var g=document.getElementById("mGrid"); g.innerHTML=""; moves=0; pairs=0; first=null; lock=false;
  document.getElementById("mMoves").textContent=0; document.getElementById("mEnd").hidden=true;
  deck.forEach(function(em){
    var c=document.createElement("button"); c.className="cell hide"; c.textContent=em; c.setAttribute("aria-label","Carte cachée");
    c.addEventListener("click", function(){flip(c)}); g.appendChild(c);
  });
}
function flip(c){
  if(lock||!c.classList.contains("hide")) return;
  c.classList.remove("hide");
  if(!first){first=c;return}
  moves++; document.getElementById("mMoves").textContent=moves;
  if(first.textContent===c.textContent){
    first.classList.add("done"); c.classList.add("done"); first=null; pairs++;
    if(pairs===EMO.length){document.getElementById("mEndTxt").textContent="Tout trouvé en "+moves+" coups.";document.getElementById("mEnd").hidden=false}
  } else {
    lock=true; var a=first; first=null;
    setTimeout(function(){a.classList.add("hide");c.classList.add("hide");lock=false},750);
  }
}
document.getElementById("mAgain").addEventListener("click", memoStart);
</script>
</body>
</html>
-muganza-