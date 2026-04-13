# Monkeyacide
If u find this welp gg but there’s nothing to see here
<!DOCTYPE html>

<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Menu Sèche — 1740 kcal/j</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0e0f0c;
    --surface: #16180f;
    --card: #1c1f14;
    --accent: #c6f135;
    --accent2: #85b81a;
    --muted: #5a6040;
    --text: #e8ecd4;
    --text2: #9da882;
    --border: #2a2e1e;
    --red: #f0614a;
    --orange: #f0a84a;
  }

- { margin: 0; padding: 0; box-sizing: border-box; }

body {
background: var(–bg);
color: var(–text);
font-family: ‘Syne’, sans-serif;
min-height: 100vh;
overflow-x: hidden;
}

/* Noise texture overlay */
body::before {
content: ‘’;
position: fixed;
inset: 0;
background-image: url(“data:image/svg+xml,%3Csvg viewBox=‘0 0 200 200’ xmlns=‘http://www.w3.org/2000/svg’%3E%3Cfilter id=‘n’%3E%3CfeTurbulence type=‘fractalNoise’ baseFrequency=‘0.9’ numOctaves=‘4’ stitchTiles=‘stitch’/%3E%3C/filter%3E%3Crect width=‘100%25’ height=‘100%25’ filter=‘url(%23n)’ opacity=‘0.04’/%3E%3C/svg%3E”);
pointer-events: none;
z-index: 0;
}

.container {
max-width: 900px;
margin: 0 auto;
padding: 40px 20px 80px;
position: relative;
z-index: 1;
}

/* HEADER */
header {
margin-bottom: 48px;
}

.tag {
display: inline-block;
font-family: ‘Space Mono’, monospace;
font-size: 10px;
letter-spacing: 2px;
text-transform: uppercase;
color: var(–accent);
border: 1px solid var(–accent);
padding: 4px 10px;
margin-bottom: 16px;
}

h1 {
font-size: clamp(2.4rem, 7vw, 4.5rem);
font-weight: 800;
line-height: 1;
color: var(–text);
letter-spacing: -1px;
}

h1 span {
color: var(–accent);
}

.subtitle {
margin-top: 12px;
color: var(–text2);
font-size: 1rem;
font-weight: 400;
max-width: 440px;
line-height: 1.5;
}

/* MACROS SUMMARY */
.macros-bar {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 12px;
margin-bottom: 48px;
}

.macro-card {
background: var(–card);
border: 1px solid var(–border);
padding: 16px;
position: relative;
overflow: hidden;
}

.macro-card::after {
content: ‘’;
position: absolute;
bottom: 0; left: 0; right: 0;
height: 3px;
background: var(–accent);
transform: scaleX(0);
transform-origin: left;
transition: transform 0.3s ease;
}

.macro-card:hover::after { transform: scaleX(1); }

.macro-label {
font-family: ‘Space Mono’, monospace;
font-size: 9px;
letter-spacing: 2px;
text-transform: uppercase;
color: var(–muted);
margin-bottom: 6px;
}

.macro-value {
font-weight: 800;
font-size: 1.6rem;
color: var(–accent);
line-height: 1;
}

.macro-unit {
font-size: 0.75rem;
color: var(–text2);
margin-top: 2px;
}

/* TABS */
.tabs {
display: flex;
gap: 4px;
margin-bottom: 32px;
flex-wrap: wrap;
}

.tab {
font-family: ‘Space Mono’, monospace;
font-size: 11px;
letter-spacing: 1px;
padding: 8px 16px;
background: transparent;
border: 1px solid var(–border);
color: var(–muted);
cursor: pointer;
transition: all 0.2s;
text-transform: uppercase;
}

.tab:hover { border-color: var(–accent2); color: var(–text); }
.tab.active {
background: var(–accent);
border-color: var(–accent);
color: var(–bg);
font-weight: 700;
}

/* DAY PANEL */
.day-panel { display: none; }
.day-panel.active { display: block; animation: fadeIn 0.25s ease; }

@keyframes fadeIn {
from { opacity: 0; transform: translateY(6px); }
to { opacity: 1; transform: translateY(0); }
}

.day-header {
display: flex;
align-items: baseline;
gap: 16px;
margin-bottom: 24px;
}

.day-name {
font-size: 2rem;
font-weight: 800;
color: var(–text);
}

.day-kcal {
font-family: ‘Space Mono’, monospace;
font-size: 0.85rem;
color: var(–accent);
}

/* MEAL CARDS */
.meals {
display: grid;
gap: 16px;
}

.meal {
background: var(–card);
border: 1px solid var(–border);
padding: 20px 24px;
display: grid;
grid-template-columns: 100px 1fr auto;
gap: 16px;
align-items: start;
transition: border-color 0.2s;
}

.meal:hover { border-color: var(–accent2); }

.meal-time {
font-family: ‘Space Mono’, monospace;
font-size: 11px;
letter-spacing: 1px;
color: var(–muted);
text-transform: uppercase;
padding-top: 2px;
}

.meal-title {
font-weight: 600;
font-size: 1rem;
color: var(–text);
margin-bottom: 6px;
}

.meal-items {
list-style: none;
display: flex;
flex-direction: column;
gap: 2px;
}

.meal-items li {
font-size: 0.82rem;
color: var(–text2);
font-weight: 400;
display: flex;
align-items: center;
gap: 6px;
}

.meal-items li::before {
content: ‘—’;
color: var(–muted);
font-size: 10px;
}

.meal-kcal {
font-family: ‘Space Mono’, monospace;
font-size: 0.8rem;
font-weight: 700;
color: var(–accent);
white-space: nowrap;
text-align: right;
}

.meal-macros {
font-family: ‘Space Mono’, monospace;
font-size: 9px;
color: var(–muted);
margin-top: 4px;
text-align: right;
line-height: 1.6;
}

/* TIPS */
.tips {
margin-top: 48px;
border: 1px solid var(–border);
padding: 24px;
background: var(–surface);
}

.tips h3 {
font-weight: 700;
font-size: 0.9rem;
color: var(–accent);
letter-spacing: 1px;
text-transform: uppercase;
margin-bottom: 16px;
font-family: ‘Space Mono’, monospace;
}

.tips-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 12px;
}

.tip {
display: flex;
gap: 10px;
align-items: flex-start;
}

.tip-icon {
font-size: 1.1rem;
flex-shrink: 0;
}

.tip-text {
font-size: 0.82rem;
color: var(–text2);
line-height: 1.5;
}

/* SHOPPING LIST SECTION */
.shopping {
margin-top: 32px;
border: 1px solid var(–border);
padding: 24px;
}

.shopping h3 {
font-weight: 700;
font-size: 0.9rem;
color: var(–accent);
letter-spacing: 1px;
text-transform: uppercase;
margin-bottom: 16px;
font-family: ‘Space Mono’, monospace;
}

.shop-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 16px;
}

.shop-cat h4 {
font-size: 0.72rem;
font-family: ‘Space Mono’, monospace;
letter-spacing: 1px;
text-transform: uppercase;
color: var(–muted);
margin-bottom: 8px;
}

.shop-cat ul {
list-style: none;
display: flex;
flex-direction: column;
gap: 4px;
}

.shop-cat ul li {
font-size: 0.8rem;
color: var(–text2);
display: flex;
align-items: center;
gap: 6px;
}

.shop-cat ul li::before {
content: ‘●’;
color: var(–accent);
font-size: 6px;
}

@media (max-width: 600px) {
.macros-bar { grid-template-columns: repeat(2, 1fr); }
.meal { grid-template-columns: 1fr; gap: 8px; }
.meal-kcal { text-align: left; }
.tips-grid, .shop-grid { grid-template-columns: 1fr; }
.tabs .tab { font-size: 10px; padding: 6px 10px; }
}
</style>

</head>
<body>
<div class="container">

  <header>
    <div class="tag">Plan Nutritionnel</div>
    <h1>MENU<br><span>SÈCHE</span></h1>
    <p style="font-family:'Space Mono',monospace;font-size:11px;letter-spacing:2px;color:var(--accent);text-transform:uppercase;margin-bottom:8px;">@monkeyacide</p>
    <p class="subtitle">7 jours · 1740 kcal/j · Riche en protéines · Budget serré · Objectif perte de poids</p>
  </header>

  <div class="macros-bar">
    <div class="macro-card">
      <div class="macro-label">Calories</div>
      <div class="macro-value">1740</div>
      <div class="macro-unit">kcal / jour</div>
    </div>
    <div class="macro-card">
      <div class="macro-label">Protéines</div>
      <div class="macro-value">~150g</div>
      <div class="macro-unit">préserve le muscle</div>
    </div>
    <div class="macro-card">
      <div class="macro-label">Glucides</div>
      <div class="macro-value">~155g</div>
      <div class="macro-unit">énergie stable</div>
    </div>
    <div class="macro-card">
      <div class="macro-label">Lipides</div>
      <div class="macro-value">~55g</div>
      <div class="macro-unit">hormones & satiété</div>
    </div>
  </div>

  <div class="tabs" id="tabs">
    <button class="tab active" onclick="showDay(0)">Lun</button>
    <button class="tab" onclick="showDay(1)">Mar</button>
    <button class="tab" onclick="showDay(2)">Mer</button>
    <button class="tab" onclick="showDay(3)">Jeu</button>
    <button class="tab" onclick="showDay(4)">Ven</button>
    <button class="tab" onclick="showDay(5)">Sam</button>
    <button class="tab" onclick="showDay(6)">Dim</button>
  </div>

  <!-- LUNDI -->

  <div class="day-panel active" id="day-0">
    <div class="day-header">
      <div class="day-name">Lundi</div>
      <div class="day-kcal">≈ 1740 kcal</div>
    </div>
    <div class="meals">
      <div class="meal">
        <div class="meal-time">Petit-déj<br>7h–8h</div>
        <div>
          <div class="meal-title">Porridge protéiné</div>
          <ul class="meal-items">
            <li>80g flocons d'avoine</li>
            <li>300ml lait demi-écrémé</li>
            <li>1 banane</li>
            <li>Cannelle</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~480 kcal</div>
          <div class="meal-macros">P: 18g<br>G: 80g<br>L: 9g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Déjeuner<br>12h–13h</div>
        <div>
          <div class="meal-title">Poulet riz légumes</div>
          <ul class="meal-items">
            <li>150g blanc de poulet poêlé</li>
            <li>80g riz (sec) cuit à l'eau</li>
            <li>200g haricots verts surgelés</li>
            <li>1 c.s huile d'olive, épices</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~560 kcal</div>
          <div class="meal-macros">P: 47g<br>G: 60g<br>L: 10g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Collation<br>16h</div>
        <div>
          <div class="meal-title">Fromage blanc & fruits</div>
          <ul class="meal-items">
            <li>200g fromage blanc 0%</li>
            <li>100g pomme</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~150 kcal</div>
          <div class="meal-macros">P: 16g<br>G: 18g<br>L: 0g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Dîner<br>19h–20h</div>
        <div>
          <div class="meal-title">Omelette aux légumes</div>
          <ul class="meal-items">
            <li>3 œufs entiers</li>
            <li>100g champignons en boîte</li>
            <li>1 tomate</li>
            <li>30g gruyère râpé allégé</li>
            <li>Salade verte</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~550 kcal</div>
          <div class="meal-macros">P: 38g<br>G: 8g<br>L: 28g</div>
        </div>
      </div>
    </div>
  </div>

  <!-- MARDI -->

  <div class="day-panel" id="day-1">
    <div class="day-header">
      <div class="day-name">Mardi</div>
      <div class="day-kcal">≈ 1730 kcal</div>
    </div>
    <div class="meals">
      <div class="meal">
        <div class="meal-time">Petit-déj<br>7h–8h</div>
        <div>
          <div class="meal-title">Pain complet & œufs brouillés</div>
          <ul class="meal-items">
            <li>2 tranches pain complet</li>
            <li>2 œufs brouillés</li>
            <li>1 café ou thé sans sucre</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~380 kcal</div>
          <div class="meal-macros">P: 20g<br>G: 38g<br>L: 13g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Déjeuner<br>12h–13h</div>
        <div>
          <div class="meal-title">Lentilles au thon</div>
          <ul class="meal-items">
            <li>150g lentilles cuites (boîte)</li>
            <li>1 boîte thon au naturel (120g)</li>
            <li>1 carotte râpée</li>
            <li>Vinaigre, moutarde, persil</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~490 kcal</div>
          <div class="meal-macros">P: 46g<br>G: 45g<br>L: 7g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Collation<br>16h</div>
        <div>
          <div class="meal-title">Yaourt nature + noix</div>
          <ul class="meal-items">
            <li>2 yaourts nature (nature basique)</li>
            <li>15g noix (env. 3 cerneaux)</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~200 kcal</div>
          <div class="meal-macros">P: 10g<br>G: 14g<br>L: 11g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Dîner<br>19h–20h</div>
        <div>
          <div class="meal-title">Dos de cabillaud vapeur + patate douce</div>
          <ul class="meal-items">
            <li>200g cabillaud (surgelé)</li>
            <li>200g patate douce cuite</li>
            <li>200g courgettes poêlées</li>
            <li>1 c.c huile d'olive, citron</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~660 kcal</div>
          <div class="meal-macros">P: 42g<br>G: 52g<br>L: 8g</div>
        </div>
      </div>
    </div>
  </div>

  <!-- MERCREDI -->

  <div class="day-panel" id="day-2">
    <div class="day-header">
      <div class="day-name">Mercredi</div>
      <div class="day-kcal">≈ 1750 kcal</div>
    </div>
    <div class="meals">
      <div class="meal">
        <div class="meal-time">Petit-déj<br>7h–8h</div>
        <div>
          <div class="meal-title">Porridge avoine + œuf dur</div>
          <ul class="meal-items">
            <li>70g flocons d'avoine + eau</li>
            <li>1 c.c miel</li>
            <li>1 œuf dur</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~410 kcal</div>
          <div class="meal-macros">P: 17g<br>G: 64g<br>L: 8g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Déjeuner<br>12h–13h</div>
        <div>
          <div class="meal-title">Poêlée de dinde & pois chiches</div>
          <ul class="meal-items">
            <li>150g escalope de dinde</li>
            <li>150g pois chiches en boîte</li>
            <li>1 poivron surgelé</li>
            <li>Paprika, cumin, ail en poudre</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~560 kcal</div>
          <div class="meal-macros">P: 52g<br>G: 44g<br>L: 10g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Collation<br>16h</div>
        <div>
          <div class="meal-title">Fromage blanc & pomme</div>
          <ul class="meal-items">
            <li>150g fromage blanc 0%</li>
            <li>1 pomme moyenne</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~160 kcal</div>
          <div class="meal-macros">P: 12g<br>G: 22g<br>L: 0g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Dîner<br>19h–20h</div>
        <div>
          <div class="meal-title">Soupe lentilles corail + pain</div>
          <ul class="meal-items">
            <li>150g lentilles corail (sèches, mijotées)</li>
            <li>1 carotte + 1 oignon</li>
            <li>Curry, cumin</li>
            <li>1 tranche pain complet</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~620 kcal</div>
          <div class="meal-macros">P: 30g<br>G: 92g<br>L: 5g</div>
        </div>
      </div>
    </div>
  </div>

  <!-- JEUDI -->

  <div class="day-panel" id="day-3">
    <div class="day-header">
      <div class="day-name">Jeudi</div>
      <div class="day-kcal">≈ 1740 kcal</div>
    </div>
    <div class="meals">
      <div class="meal">
        <div class="meal-time">Petit-déj<br>7h–8h</div>
        <div>
          <div class="meal-title">Yaourt grec + flocons + fruit</div>
          <ul class="meal-items">
            <li>150g yaourt grec 0%</li>
            <li>40g flocons d'avoine</li>
            <li>1 banane</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~370 kcal</div>
          <div class="meal-macros">P: 16g<br>G: 60g<br>L: 3g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Déjeuner<br>12h–13h</div>
        <div>
          <div class="meal-title">Steak haché 5% + purée</div>
          <ul class="meal-items">
            <li>150g steak haché 5% MG</li>
            <li>250g pommes de terre en purée</li>
            <li>100ml lait demi-écrémé (pour purée)</li>
            <li>Haricots verts</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~580 kcal</div>
          <div class="meal-macros">P: 38g<br>G: 58g<br>L: 12g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Collation<br>16h</div>
        <div>
          <div class="meal-title">Boîte de thon + crackers</div>
          <ul class="meal-items">
            <li>1 petite boîte thon au naturel (80g)</li>
            <li>4 crackers au blé complet</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~200 kcal</div>
          <div class="meal-macros">P: 20g<br>G: 16g<br>L: 3g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Dîner<br>19h–20h</div>
        <div>
          <div class="meal-title">Salade de pâtes complètes</div>
          <ul class="meal-items">
            <li>80g pâtes complètes (sèches)</li>
            <li>2 œufs durs</li>
            <li>1 tomate, ½ concombre</li>
            <li>Vinaigrette légère (1 c.c huile)</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~590 kcal</div>
          <div class="meal-macros">P: 30g<br>G: 68g<br>L: 18g</div>
        </div>
      </div>
    </div>
  </div>

  <!-- VENDREDI -->

  <div class="day-panel" id="day-4">
    <div class="day-header">
      <div class="day-name">Vendredi</div>
      <div class="day-kcal">≈ 1720 kcal</div>
    </div>
    <div class="meals">
      <div class="meal">
        <div class="meal-time">Petit-déj<br>7h–8h</div>
        <div>
          <div class="meal-title">Œufs sur pain complet</div>
          <ul class="meal-items">
            <li>3 œufs (omelette ou brouillés)</li>
            <li>2 tranches pain complet</li>
            <li>Café/thé sans sucre</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~440 kcal</div>
          <div class="meal-macros">P: 26g<br>G: 34g<br>L: 18g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Déjeuner<br>12h–13h</div>
        <div>
          <div class="meal-title">Riz + poulet + brocoli</div>
          <ul class="meal-items">
            <li>150g blanc de poulet</li>
            <li>70g riz basmati (sec)</li>
            <li>200g brocoli surgelé à la vapeur</li>
            <li>Sauce soja, ail, gingembre</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~530 kcal</div>
          <div class="meal-macros">P: 48g<br>G: 58g<br>L: 7g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Collation<br>16h</div>
        <div>
          <div class="meal-title">Fromage blanc + flocons</div>
          <ul class="meal-items">
            <li>150g fromage blanc 0%</li>
            <li>25g flocons d'avoine</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~190 kcal</div>
          <div class="meal-macros">P: 14g<br>G: 26g<br>L: 1g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Dîner<br>19h–20h</div>
        <div>
          <div class="meal-title">Soupe de pois chiches + œuf poché</div>
          <ul class="meal-items">
            <li>200g pois chiches (boîte)</li>
            <li>1 oignon + 1 carotte</li>
            <li>2 œufs pochés</li>
            <li>Cumin, paprika</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~560 kcal</div>
          <div class="meal-macros">P: 36g<br>G: 58g<br>L: 14g</div>
        </div>
      </div>
    </div>
  </div>

  <!-- SAMEDI -->

  <div class="day-panel" id="day-5">
    <div class="day-header">
      <div class="day-name">Samedi</div>
      <div class="day-kcal">≈ 1760 kcal</div>
    </div>
    <div class="meals">
      <div class="meal">
        <div class="meal-time">Petit-déj<br>8h–9h</div>
        <div>
          <div class="meal-title">Pancakes avoine & banane</div>
          <ul class="meal-items">
            <li>80g flocons d'avoine mixés</li>
            <li>1 banane écrasée</li>
            <li>2 œufs</li>
            <li>Poêle anti-adhésive, sans huile</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~480 kcal</div>
          <div class="meal-macros">P: 22g<br>G: 68g<br>L: 12g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Déjeuner<br>13h</div>
        <div>
          <div class="meal-title">Chili con carne léger</div>
          <ul class="meal-items">
            <li>150g bœuf haché 5%</li>
            <li>150g haricots rouges (boîte)</li>
            <li>1 boîte tomates concassées</li>
            <li>Oignon, ail, cumin, chili</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~560 kcal</div>
          <div class="meal-macros">P: 44g<br>G: 38g<br>L: 14g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Collation<br>16h</div>
        <div>
          <div class="meal-title">Yaourt + fruit</div>
          <ul class="meal-items">
            <li>2 yaourts nature</li>
            <li>1 orange</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~170 kcal</div>
          <div class="meal-macros">P: 8g<br>G: 26g<br>L: 2g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Dîner<br>19h–20h</div>
        <div>
          <div class="meal-title">Saumon (boîte) + quinoa + épinards</div>
          <ul class="meal-items">
            <li>1 boîte saumon (155g)</li>
            <li>70g quinoa (sec)</li>
            <li>150g épinards surgelés</li>
            <li>Citron, ail</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~550 kcal</div>
          <div class="meal-macros">P: 42g<br>G: 46g<br>L: 14g</div>
        </div>
      </div>
    </div>
  </div>

  <!-- DIMANCHE -->

  <div class="day-panel" id="day-6">
    <div class="day-header">
      <div class="day-name">Dimanche</div>
      <div class="day-kcal">≈ 1730 kcal</div>
    </div>
    <div class="meals">
      <div class="meal">
        <div class="meal-time">Petit-déj<br>9h</div>
        <div>
          <div class="meal-title">Porridge gourmand</div>
          <ul class="meal-items">
            <li>90g flocons d'avoine</li>
            <li>300ml lait demi-écrémé</li>
            <li>1 c.c miel + cannelle</li>
            <li>1 pomme râpée</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~500 kcal</div>
          <div class="meal-macros">P: 18g<br>G: 84g<br>L: 10g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Déjeuner<br>13h</div>
        <div>
          <div class="meal-title">Poulet rôti + légumes four</div>
          <ul class="meal-items">
            <li>200g cuisse de poulet (sans peau)</li>
            <li>200g pommes de terre + 1 courgette</li>
            <li>1 c.s huile d'olive, herbes de Provence</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~580 kcal</div>
          <div class="meal-macros">P: 44g<br>G: 40g<br>L: 16g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Collation<br>16h</div>
        <div>
          <div class="meal-title">Fromage blanc + flocons</div>
          <ul class="meal-items">
            <li>200g fromage blanc 0%</li>
            <li>20g flocons d'avoine</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~180 kcal</div>
          <div class="meal-macros">P: 16g<br>G: 22g<br>L: 0g</div>
        </div>
      </div>
      <div class="meal">
        <div class="meal-time">Dîner<br>19h–20h</div>
        <div>
          <div class="meal-title">Salade niçoise économique</div>
          <ul class="meal-items">
            <li>2 œufs durs</li>
            <li>1 boîte thon au naturel</li>
            <li>Haricots verts, tomate, salade</li>
            <li>Vinaigrette légère (1 c.c huile)</li>
          </ul>
        </div>
        <div>
          <div class="meal-kcal">~470 kcal</div>
          <div class="meal-macros">P: 46g<br>G: 14g<br>L: 20g</div>
        </div>
      </div>
    </div>
  </div>

  <!-- SHOPPING LIST -->

  <div class="shopping">
    <h3>🛒 Liste de courses · Budget ~25–30€/semaine</h3>
    <div class="shop-grid">
      <div class="shop-cat">
        <h4>Protéines</h4>
        <ul>
          <li>Blancs de poulet (500g)</li>
          <li>Steak haché 5% (x2)</li>
          <li>Thon au naturel (x3 boîtes)</li>
          <li>Saumon en boîte (x1)</li>
          <li>Cabillaud surgelé</li>
          <li>Dinde escalopes (200g)</li>
          <li>Œufs (x12)</li>
        </ul>
      </div>
      <div class="shop-cat">
        <h4>Féculents & légumineuses</h4>
        <ul>
          <li>Flocons d'avoine (500g)</li>
          <li>Riz basmati (500g)</li>
          <li>Pâtes complètes (500g)</li>
          <li>Lentilles vertes (boîte)</li>
          <li>Lentilles corail (sèches 250g)</li>
          <li>Pois chiches (2 boîtes)</li>
          <li>Haricots rouges (boîte)</li>
          <li>Quinoa (250g)</li>
          <li>Pain complet</li>
        </ul>
      </div>
      <div class="shop-cat">
        <h4>Produits laitiers & légumes</h4>
        <ul>
          <li>Fromage blanc 0% (x2 pots 500g)</li>
          <li>Yaourts nature (x6)</li>
          <li>Lait demi-écrémé (1L)</li>
          <li>Haricots verts surgelés (500g)</li>
          <li>Brocoli surgelé (500g)</li>
          <li>Épinards surgelés (300g)</li>
          <li>Tomates, carottes, courgettes</li>
          <li>Pommes de terre, patate douce</li>
          <li>Bananes, pommes, orange</li>
        </ul>
      </div>
    </div>
  </div>

  <!-- TIPS -->

  <div class="tips">
    <h3>⚡ Conseils sèche</h3>
    <div class="tips-grid">
      <div class="tip">
        <div class="tip-icon">💧</div>
        <div class="tip-text"><strong>Boire 2–2,5L/jour</strong> — l'eau aide à contrôler l'appétit et à éliminer les déchets métaboliques liés à la perte de graisses.</div>
      </div>
      <div class="tip">
        <div class="tip-icon">🥩</div>
        <div class="tip-text"><strong>Protéines en priorité</strong> — viser 150g/j protège la masse musculaire. Les œufs, poulet, thon et légumineuses sont tes alliés pas chers.</div>
      </div>
      <div class="tip">
        <div class="tip-icon">🕐</div>
        <div class="tip-text"><strong>Éviter de sauter un repas</strong> — manger 4x/j stabilise la glycémie et réduit les fringales qui sabotent le déficit.</div>
      </div>
      <div class="tip">
        <div class="tip-icon">🥦</div>
        <div class="tip-text"><strong>Les légumes à volonté</strong> — haricots, brocoli, courgette, épinards → très peu caloriques, riches en fibres et vitamines.</div>
      </div>
      <div class="tip">
        <div class="tip-icon">🛒</div>
        <div class="tip-text"><strong>Acheter surgelé</strong> — brocoli, haricots, épinards surgelés sont aussi nutritifs que frais et 2 à 3x moins chers.</div>
      </div>
      <div class="tip">
        <div class="tip-icon">📊</div>
        <div class="tip-text"><strong>Peser ses aliments</strong> — pour rester précis sur les calories, surtout pour les féculents et matières grasses (huile = 90 kcal/c.s !).</div>
      </div>
    </div>
  </div>

</div>

<script>
  function showDay(index) {
    document.querySelectorAll('.day-panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    document.getElementById('day-' + index).classList.add('active');
    document.querySelectorAll('.tab')[index].classList.add('active');
  }
</script>

</body>
</html>
