# DESIGN.md — Konoba Roki, Vodice · v5

register: brand
archetype: PRESET 1 — Fine Dining / Konoba (rustic-restraint mod)
mode: brand (Impeccable čita ovo i IZVODI; ne nameće svoj default)

---

## Karakter palete — "Bor, vapnenac i žar"

Izveden striktno iz OVOG objekta (ime → mjesto → kuhinja), namjerno **odmaknut od terakote**
koju su v1–v4 svi koristili (v1 je čak goli preset-1 default: pergament + terra + sage).

**Zašto ovaj karakter za Roki / Vodice:**
- **Vodice** leže na bijelom dalmatinskom **vapnencu** i uokvirene su gustim **alepskim borom**
  koji se spušta do uvala — pa je baza bijeli kamen, a **vodeći akcent bor-zelena** (ne terakota).
- Ime **"Vodice"** dolazi od *vodica* — izvora/bunara slatke vode koja izbija uz more; zato je
  dekorativni potpis "vodica" (koncentrični krug izvora), a najsvjetliji ton je hladni izvor-akvamarin.
- **"Roki"** je topao obiteljski nadimak (Sv. Roko) — toplina se nosi u **žar/vino** akcentu:
  konoba je riba i meso **s gradela na žaru**, uz domaći crni (babić-tip) s ovog dijela obale.

Rezultat: kamen (baza) + bor/mediteran (vodeći akcent) + žar/vino (topli CTA akcent).
Dvije konobe ≠ ista paleta: Roki v5 vodi bor-zelenom, ne terakotom.

### Izvedeni tokeni (Impeccable neka izvede u OKLCH, zadrži hue/karakter)

| Token | Hex | Odakle dolazi | Uloga |
|---|---|---|---|
| `--bg-base` | `#ECE6D8` | izbijeljeni dalmatinski vapnenac (paler & hladniji od v1 pergamenta) | baza |
| `--bg-alt` | `#E4DDCB` | osjenčani suhozid | alt sekcije |
| `--ink` | `#1C231D` | Jadran-bor u sumrak (near-black s zelenim podtonom) | tekst / dark sekcije |
| `--pine` | `#3B4A38` | alepski bor uz vodičke uvale — **VODEĆI akcent** | naslovi-akcent, linije |
| `--pine-soft` | `#59684F` | svjetliji bor | eyebrow/label (samo ≥18px; ne body) |
| `--ember` | `#9A4327` | žar s gradela + domaći crni | **topli CTA akcent** (rijetko) |
| `--stone` | `#8A8272` | muted vapnenac | dekorativno / hairline (NE body tekst — kontrast prenizak) |
| `--spring` | `#6E8E86` | izvor-akvamarin (ime "Vodice") | šapat: hover-tint / hairline, vrlo rijetko |

**Kontrast (tvrdo):** body je uvijek `--ink` na `--bg-base` (~13:1). `--pine` na bazi ~7:1 (ok za
naslove/istaknuti body). `--ember` gumb = ember bg + `#F5F1E6` tekst (~5.4:1). `--stone` i `--spring`
NIKAD kao body tekst (ispod 4.5:1) — samo dekor/large.

## Par fontova

**Display: EB Garamond** · **Body: Work Sans**
- Zašto: sve prethodne Roki verzije koriste Cormorant Garamond — mijenjamo obitelj (anti-klon).
  EB Garamond je mekši, "knjiškiji" — pristaje toploj **obiteljskoj** konobi s nadimkom.
  Work Sans (humanist sans) daje kontrast-os (serif + sans), a nije Inter/DM Sans (prethodne + overused)
  ni Fraunces (hook ga označava kao overused). Google Fonts, bez licence.
- Skala: H1 `clamp(48px, 7vw, 88px)` (≤6rem strop) · body `17px/1.7` · eyebrow uppercase `11px` `ls .18em`.

## Hero — 4-image editorial grid ("menu-kao-poster")

Rotacija: v1 = Fine Dining Dark (fullbleed tamni), v4 = Modern Minimal → v5 uzima **mirni editorial grid**
(riba / žar-gradele / terasa nad morem / kamen-priobalje). Miran "poster" dojam, sadržaj odmah vidljiv.
Nježni Ken-Burns breath na pločicama (CSS scale 1.0→1.045, bez JS/scrub).

## Set potpisnih interakcija (rustic-restraint, unutar perf budžeta)

1. EB Garamond naslovi — word-by-word reveal iza maske (non-scrub, onEnter).
2. Sekcije — fade + 18px translate na ulazu (non-scrub).
3. Galerija — topli vapnenac-sepia `sepia(.18) contrast(1.05) saturate(.92)` + bor-duotone na hover.
4. Hero pločice — spori CSS Ken-Burns breath (bez scruba).
5. "Vodica" divider crta svoj stroke jednom na ulazu + ember link-underline draw (CSS).

**Zabranjeno ovdje (rustic):** custom cursor s efektima, magnetic gumbi, horizontal scroll, particles,
scramble, kinetička tipografija, WebGL, agresivni scrub. Lenis `lerp:0.2` (scroll-fix iz memorije).

## Dekorativni potpis — INDIVIDUALIZIRAN (ne globalni default)

**"Vodica" znak:** ručno-inkani SVG od tri koncentrična polukruga (izvor koji izbija) prekrižena
jednom **borovom iglicom/grančicom**. Doslovno kodira ime *Vodice* (izvori) + bor.
Koristi se kao **divider sekcija** i uz logo. NEMA generičkog cursor-dota, NEMA generičke
maslinove grančice-divider, NEMA 01/02/03 brojčanih markera. Ovaj potpis se ne smije pojaviti
ni na jednoj drugoj stranici.

## Tvrda pravila koja Impeccable NE smije pregaziti

- **Keyless mapa** — samo `<iframe ...&output=embed>`; nikad Maps JS API / `key=`.
- **Bez tajni/ključeva** u kodu (S1). Forma = `mailto:`/`tel:` ili vanjski hosted; nikad ugrađen ključ.
- **"Stranica nikad prazna"** — sav copy stvarno napisan u glasu Rokija (topao, obiteljski,
  dalmatinski-neposredan, more+bor+žar senzorika); pretpostavke označene `TODO[klijent]`.
- **SEO/schema** — jedan H1, semantička hijerarhija, lokacija (Vodice) u naslovima/tekstu/kontaktu,
  alt tekstovi, `Restaurant` JSON-LD.
- **Individualizirana paleta** iznad — Impeccable je izvodi (OKLCH/kontrast), ne zamjenjuje.
