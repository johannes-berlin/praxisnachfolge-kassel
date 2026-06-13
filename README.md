# Praxisnachfolge · Großraum Kassel — Astro

Single-Page-Umsetzung der **v4**-Variante mit **Astro + Tailwind v4**.
Die Spacings wurden von der **warm**-Variante übernommen (durchgängig etwas
kompakter als v4), Farben, Typografie, Hero-Gradient und Hero-Asset bleiben
aus v4.

## Setup

```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # → dist/
npm run preview
```

## Struktur

```
src/
  pages/index.astro     # komplette Seite (Hero, Statement, Kennblatt,
                         # Highlights, Process, FAQ, CTA, Footer + JS)
  styles/global.css     # @theme-Tokens (Farben, Schrift, Fluid-Typo)
                         # + Hero-Gradient, FAQ-Akkordeon, Scroll-Reveal
public/
  hero-art.png          # aus dem v4-Base64 extrahiertes Hero-Motiv (Prototyp)
```

Daten (Kennblatt, Highlights, Prozess, FAQ) liegen als Arrays im Frontmatter
von `index.astro` und werden gemappt — leicht editierbar.

## Übernommene Spacings (warm → v4)

| Element        | v4 (alt)   | warm (neu)  |
| -------------- | ---------- | ----------- |
| `section`      | 82px       | **74px**    |
| `.sec-head` mb | 42px       | **40px**    |
| Statement gap  | 54px       | **50px**    |
| Kennblatt pad  | 16/44/32   | **14/40/30**|
| kb-row         | 215px·22px | **210px·20px** |
| kb-k pt        | 6px        | **5px**     |
| kb-note mt     | 26px       | **24px**    |
| colitem pad    | 32/32/8/0  | **30/30/30/0** |
| colitem .plus  | 22px       | **20px**    |
| card pad       | 32/30/34   | **30/28/32**|
| FAQ trigger    | 26px       | **24px**    |
| FAQ answer pb  | 28px       | **26px**    |
| CTA pad        | 60/56/64   | **56/56/60**|
| CTA h2/sub     | 16/0/36    | **h2 16/0/14 · sub mb 36** |
| Topbar pad     | 22px       | **26px**    |

Mobile (`max-[860px]:`) ebenfalls auf warm angeglichen (Statement-Gap 28px,
colitem 26px, CTA 40/26/44, Kennblatt 14/24/24).

## Theme-Tokens

In `global.css` als `@theme`-Custom-Properties — u. a.
`--color-sand/cream/gold/olive/olive-deep/ink`, Textstufen `--color-body/muted/faint`,
Linien `--color-line/line-soft`, sowie Fluid-Größen `--text-h1/h2/cta-h2`
(nutzbar als `text-h1` etc.).

## Hinweise

- **Schrift:** Fallback Helvetica Neue. Für Produktion **PP Neue Montreal**
  einbinden (`@font-face` in `global.css` + `--font-display` bleibt).
- **Hero-Asset:** Prototyp-Motiv. Für die echte Seite eigenes, rechtlich
  freies Bild in `public/` ablegen.
- **Formular:** sendet noch nichts. Anbindung wie geplant:
  Netlify Function → Notion-Lead-DB → Resend.
- `noindex, nofollow` ist gesetzt (Diskretion, solange anonym).
