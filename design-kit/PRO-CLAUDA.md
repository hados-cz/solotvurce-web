# Design kit „Hadoš" — brief pro AI agenta (Romanova Clauda)

Ahoj kolego. Tohle je **sdílený vizuální jazyk Hadoše** (vibe „AI pro sólotvůrce").
Cíl: aby další weby — **redesign hados.cz** a podprojekty — vznikaly pod jednotnou grafikou,
ne pokaždé znovu od nuly. Níž je vše, co potřebuješ, abys s tím uměl pracovat.

## Kde to je
- **Repo:** `github.com/hados-cz/solotvurce-web`, složka **`design-kit/`**
- **Soubory:** `design.css` (celý systém), `styleguide.html` (živá ukázka komponent), `README.md` (návod pro lidi)
- **Živě:**
  - vizuální reference → https://solotvurce.cz/design-kit/styleguide
  - stylesheet → https://solotvurce.cz/design-kit/design.css

## Než začneš stavět — načti si tyhle 3 věci
1. `design.css` — **design tokeny** (barvy, fonty, stíny) + komponenty. Zdroj pravdy.
2. `styleguide.html` — jak komponenty vypadají (a copy-paste markup).
3. `README.md` — návod + pravidla použití.

## Jak kit nasadit na novou stránku (4 kroky)
1. **Fonty** do `<head>` (Newsreader = nadpisy, Plus Jakarta Sans = text):
   ```html
   <link rel="preconnect" href="https://fonts.googleapis.com">
   <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
   <link href="https://fonts.googleapis.com/css2?family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,500;0,6..72,600;1,6..72,400;1,6..72,500&family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
   ```
2. **Stylesheet:** `<link rel="stylesheet" href="design.css">` (zkopíruj soubor do projektu).
3. **Režim** na `<html>`: `data-theme="dark"` (výchozí) nebo `data-theme="light"`.
4. Stavěj **z komponent** (tříd) níž — neměň barvy/fonty natvrdo.

## Komponenty (cheat-sheet)
| Co | Jak |
|---|---|
| Nadpisy (serif) | `<h1> <h2> <h3>` nebo `.font-display` |
| Lead / tlumený text | `.lead` · `.text-soft` · `.text-mut` |
| Žlutá „fixa" na slovo | `<span class="mark">slovo</span>` |
| Tlačítka | `.btn` + `.btn-primary` / `.btn-ghost` / `.btn-dark` |
| Karta + barevný offset stín | `.card` + `.card--s1` (žlutá) / `--s2` (mátová) / `--s3` (modrá) |
| Razítko | `.stamp` (uvnitř `<b>` + `<small>`) |
| Riso textura přes stránku | `class="riso"` na `<body>` (opt-in, subtilní) |
| Eyebrow / plocha / linka | `.eyebrow` · `.surface` · `<hr class="divider">` |

## Pravidla, která musíš držet (jinak se „rozbije" brand)
- **Žlutá `#FFCC33` = hlavní akcent + CTA + fixa.** Nikde jinde jí neplýtvej, ať nevyšumí.
- **Mátová `#5eead4` a modrá `#2a3a7e`** = jen doplňkové akcenty (offset stíny), ne náhrada žluté.
- **Serif (Newsreader) jen na nadpisy.** Tělo vždy Plus Jakarta Sans.
- **Ostré hrany, 2px `var(--ink)` border, soutiskové (offset) stíny** — to je ten „tištěný" rukopis.
- **Riso je koření, ne hlavní jídlo** — drž subtilní (výchozí opacity v `.riso`).
- **Barvy nikdy natvrdo v komponentě.** Vždy přes `var(--…)`. Nové barvy přidávej jen do tokenů v `design.css` (`:root` / `:root[data-theme="light"]`).

## Když potřebuješ NOVOU komponentu (kterou kit nemá)
Odvoď ji ze stejných principů: bílá/papírová plocha `var(--paper)` nebo `var(--bg-soft)`,
`border: 2px solid var(--ink)`, offset stín `box-shadow: 8px 8px 0 var(--shadow)` (nebo `--s1/2/3`),
serif nadpis, žlutý akcent střídmě, oba režimy přes tokeny. Ať to vypadá jako ze stejné rodiny.

## Startovací kostra (zkopíruj a stav)
```html
<!DOCTYPE html>
<html lang="cs" data-theme="dark">
<head>
  <meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>…</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,500;0,6..72,600;1,6..72,400;1,6..72,500&family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="design.css">
</head>
<body class="riso">
  <main style="max-width:1040px;margin:0 auto;padding:64px 6%">
    <p class="eyebrow">Hadoš</p>
    <h1>Nadpis <span class="mark">s důrazem.</span></h1>
    <p class="lead">Lead odstavec pod claimem.</p>
    <a class="btn btn-primary" href="#">Hlavní akce →</a>
  </main>
</body>
</html>
```

## Sync (důležité)
`design.css` je **extrahovaný z živého `solotvurce.cz`** (inline `<style>` v `index.html`).
Není to automaticky propojené — když na landingu nebo v kitu něco změníš, **sjednoť to ručně**
i na druhé straně, ať brand nedrift­uje. Při větší změně se ozvi Martinovu Claudovi, sladíme.
