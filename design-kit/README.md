# Hadoš — Design kit

Znovupoužitelný vizuální jazyk „AI pro sólotvůrce" (editorial / „zin": serif nadpisy,
žlutá „fixa", offset stíny, riso textura, světlý/tmavý režim). Slouží jako **společná
štábní kultura** pro hados.cz a další podprojekty.

## Co je ve složce
- **`design.css`** — celý design systém: tokeny (barvy, fonty, stíny) + komponenty. Drop-in.
- **`styleguide.html`** — živá ukázka všeho na jednom místě (otevři v prohlížeči). Slouží i jako copy-paste zdroj.
- **`README.md`** — tenhle návod.

## Jak to použít (3 kroky)

**1) Připoj fonty** (Google Fonts — Newsreader na nadpisy, Plus Jakarta Sans na text):
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,500;0,6..72,600;1,6..72,400;1,6..72,500&family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
```

**2) Připoj stylesheet:**
```html
<link rel="stylesheet" href="design.css">
```

**3) Nastav režim** atributem na `<html>` (výchozí = tmavý):
```html
<html data-theme="light">   <!-- nebo data-theme="dark" -->
```
Přepínání za běhu: `document.documentElement.setAttribute('data-theme', 'light')`
(viz JS na konci `styleguide.html`).

## Komponenty (cheat-sheet)

| Co | Třída / značka |
|---|---|
| Nadpisy serif | `<h1>` `<h2>` `<h3>` nebo `.font-display` |
| Lead odstavec | `.lead` |
| Tlumený / nejtlumenější text | `.text-soft` / `.text-mut` |
| Žlutá „fixa" na slovo | `<span class="mark">slovo</span>` |
| Tlačítka | `.btn` + `.btn-primary` / `.btn-ghost` / `.btn-dark` |
| Karta | `.card` + barevný offset stín `.card--s1/s2/s3` (žlutá/mátová/modrá) |
| Razítko | `.stamp` (uvnitř `<b>` + `<small>`) |
| Riso textura přes stránku | `class="riso"` na `<body>` (opt-in) |
| Eyebrow / nadřádek | `.eyebrow` |
| Tlumená plocha / oddělovač | `.surface` / `<hr class="divider">` |

## Pravidla použití (důležité)
- **Žlutá `#FFCC33` = hlavní akcent a CTA.** Drž ji pro to nejdůležitější (tlačítka, fixa), ať „nevyšumí".
- **Mátová `#5eead4` a modrá** = doplňkové akcenty (např. offset stíny karet). Ne místo žluté.
- **Serif (Newsreader) jen na nadpisy**, tělo vždy Plus Jakarta Sans.
- **Riso** je jemné koření, ne hlavní jídlo — drž subtilní (výchozí opacity v `.riso`).
- Tokeny se mění jen v `design.css` v sekcích `:root` / `[data-theme="…"]` — neměň barvy natvrdo v komponentách.

## Pozn.
Stylesheet je extrahovaný z živého webu `solotvurci.cz` (inline `<style>` v `index.html`).
Když na landingu něco upravíš a chceš to i v kitu (nebo naopak), sjednoť ručně.
