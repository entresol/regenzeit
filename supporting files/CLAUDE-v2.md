# CLAUDE.md — Regenzeit Website Project
**Version 2 — Stand März 2026**

> Vollständiger Kontext für Claude Code. Vor jedem Task komplett lesen.
> Das Fundament (index.html v1) ist bereits live auf entresol.github.io/regenzeit
> Ab jetzt: nur noch gezielte Änderungen am bestehenden Code, kein Rewrite.

---

## 1. Projekt & Kontext

**Was ist die Regenzeit?**
Thai-Streetfood-Restaurant in Nürnberg-Gostenhof. Betrieben von Benno & Aey Bartels seit 2014.
Kult-Lokal: 4,9 Sterne bei 780+ Google-Rezensionen. Seit Januar 2025 neue Location: Hessestraße 4.
Kein kommerzieller Auftrag — Freundschaftsdienst von Stefan Lischka (entresol.de).

**Das Problem das diese Site löst:**
Null eigenständige Web-Präsenz trotz Kult-Status. Nur Facebook (ungepflegt), Instagram
(@regenzeit.goho, 37 Posts, stimmungsvoll), Google Maps (einzige Öffnungszeiten-Quelle).
Benno ist an Lovable gescheitert — er braucht keinen No-Code-Editor, er braucht jemanden
der die Arbeit macht.

**Hosting:** GitHub Pages `entresol/regenzeit` → https://entresol.github.io/regenzeit
**Spätere Domain:** `regenzeit-nuernberg.de` (noch nicht aktiv)

---

## 2. Was bereits live ist (nicht anfassen ohne Grund)

Die bestehende index.html hat folgendes bereits korrekt implementiert:
- Vollständiges Schema.org JSON-LD (Restaurant + FoodEstablishment)
- Open Graph + Twitter Card Meta-Tags
- DSGVO-konformes Google Maps Click-to-Load
- Impressum + Datenschutz als `<dialog>`-Modals
- Mobile Navigation Toggle (Vanilla JS)
- Bunny Fonts (DSGVO-konform, EU-Server) mit Playfair Display + Inter
- Sektionsstruktur: Hero → Über uns → Speisekarte → Besuch planen → Footer
- robots.txt + llms.txt Grundstruktur

**Was NICHT stimmt und geändert werden muss:** → siehe Abschnitt 5

---

## 3. Fakten (verifiziert)

| | |
|---|---|
| Adresse | Hessestraße 4, 90443 Nürnberg-Gostenhof |
| Telefon | 0911 18099765 |
| Geo | 49.44550670, 11.05773220 |
| Instagram | @regenzeit.goho |
| Facebook | regenzeit.goho |
| Küche | Authentisch Thai, Bangkok-Streetfood-Stil |
| Preis | € (7–12 EUR) |
| Rating | 4,9 / 5 (780+ Rezensionen) |
| Betrieben seit | 2014 (erst Willstraße 5, seit Jan 2025 Hessestraße 4) |

**Gerichte** (ggf. mit Benno/Aey aktualisieren):
- Lek Haeng — warmes Gemüse, Kräuter, selbstgeröstete Erdnüsse (vegan/Huhn/Ente, 9–11,50€)
- Curry Nudeln — Kokosmilch, Erdnüsse, Röstzwiebeln, Gemüse, Kräuter (vegan/Huhn, 9,50–10,50€)
- Tom Yam — Glasnudeln, Fisch, Muscheln, Garnelen, Surimi, Pilze (12€)
- Khao Gluck — warmer Reis mit Gemüse, pikant (vegan)
- Klebreis mit Mango — Dessert
- Vegan-Basis: Gemüse, Tofu, Pilze, Erdnüsse (7€)

**Öffnungszeiten** (aus bestehendem Schema.org, mit Benno bestätigen):
Di–Sa: 11:30–14:30 und 17:00–22:00 | Mo + So: geschlossen

---

## 4. Das Logo — der Frosch

Das Regenzeit-Logo ist ein **handgemaltes Schild**: grüner Frosch auf braunem Blatt,
darunter "Regenzeit" in handgeschriebener Lettering-Schrift, aufgehängt an einer
Schnur vor gelbem Hintergrund. Das ist kein Zufall — das ist die gesamte Marken-DNA:
handgemacht, persönlich, ein bisschen schräg, lebendig.

**Datei vorhanden:** `assets/img/logo/frosch-original.jpeg` (Foto des Originals)

### Midjourney-Prompts für digitale Logo-Version

**Primär-Prompt (für Website-Integration auf dunklem BG):**
```
hand-painted illustration of a green tree frog sitting on a large tropical
monsoon leaf, folk art style, bold black outlines, warm earthy colors,
slightly imperfect brushwork, the word "Regenzeit" integrated as handwritten
lettering below the leaf, dark warm background (#1A1208),
the frog has character and personality,
NOT cute/kawaii — more like a weathered Thai market sign,
isolated on dark background, no white card/paper,
suitable as website logo, high contrast --ar 1:1 --style raw --v 6.1
```

**Variante Bangkok-Style:**
```
vintage Thai street food stall sign, green frog mascot on monsoon leaf,
hand-lettered "Regenzeit", worn paint texture, neon orange glow edge,
dark background, authentic market aesthetic, bold graphic --ar 1:1 --v 6.1
```

### Logo-Einsatz auf der Site
- Navigation: Logo-Bild statt reinem Text "Regenzeit" (mit Alt-Text)
- Hero: Logo groß, als zentrales Element über dem Slogan
- Footer: kleinere Version
- Als wiederkehrendes Motiv: kleiner Frosch als Section-Divider zwischen Sektionen
  statt `<hr>` — Unicode-Fallback: 🐸 oder ❋

**Technisch:** SVG bevorzugt (wenn aus Midjourney per Vectorizer.ai vektorisiert),
sonst WebP mit transparentem Hintergrund. Auf dunklem Site-Background testen.

---

## 5. Gezielte Änderungen am bestehenden index.html

Folgende Punkte sind am bestehenden Fundament zu ändern/ergänzen.
**Kein kompletter Rewrite** — gezielt patchen.

### 5.1 Slogan + Subline (Hero)

**Bisheriger Text (ersetzen):**
```
Thai-Streetfood wie in Bangkok. Mitten in Gostenhof.
```

**Neuer Slogan (primär, mit Neon-Glow):**
```
When it rains, it smells like Bangkok.
```

**Neue Subline (sekundär, kleiner):**
```
Thai-Nudelsuppen, die man nicht vergisst. Hessestraße 4, Gostenhof.
```

*Begründung Slogan:* Verbindet Regenzeit (wörtlich + Name), den stärksten
Review-Trigger (Geruch: "da riecht es wie in Thailand" — mehrfach in echten Reviews),
und Bangkok. Englisch ist bewusst — funktioniert idiomatisch, klingt authentischer
als deutsche Übersetzung. Spielt auf "when it rains it pours" an.

*Begründung Subline:* Das ist die echte Instagram-Headline von Benno/Aey —
"Thai-Nudelsuppen, die man nicht vergisst." Gekürzt auf den Kern.

### 5.2 Fonts (ersetzen)

**Bisherig (Bunny Fonts):** `playfair-display` + `inter`

**Neu (Bunny Fonts — DSGVO-konform bleiben):**
```css
Bebas Neue   — Headlines, Wortmarke, Slogan (Plakatcharakter)
Noto Serif Thai — Dish-Namen, Akzent-Labels (kulturelle Echtheit)
Inter        — bleibt für Fließtext, Öffnungszeiten, Prosa
```

Bunny Fonts URL prüfen ob Bebas Neue + Noto Serif Thai verfügbar.
Fallback: fonts.googleapis.com (dann Datenschutz-Dialog-Text anpassen).

### 5.3 Farbpalette + theme-color (ersetzen)

```css
:root {
  --color-bg:         #1A1208;
  --color-surface:    #261C0E;
  --color-surface-2:  #332510;
  --color-neon:       #FF8C00;
  --color-warm:       #E8C547;
  --color-heat:       #C0392B;
  --color-green:      #4A7C3F;
  --color-text:       #F5EDD8;
  --color-text-muted: #A89070;
}
```

`<meta name="theme-color" content="#FF8C00">` (war: #8B1A1A)
`<meta name="color-scheme" content="dark">` (war: light)

### 5.4 Neon-Glow auf Slogan

```css
.hero__slogan {
  color: var(--color-neon);
  text-shadow:
    0 0 20px rgba(255, 140, 0, 0.6),
    0 0 40px rgba(255, 140, 0, 0.3);
  font-family: var(--font-display);
  letter-spacing: 0.02em;
}
```

### 5.5 Video-Hero (neues Element)

Struktur im Hero-`<section>` ergänzen:

```html
<section class="hero" id="start">

  <!-- Video-Hintergrund -->
  <video
    class="hero__video"
    autoplay muted loop playsinline
    poster="assets/img/hero/hero-poster.jpg"
    aria-hidden="true"
  >
    <source src="assets/video/bangkok-reel.webm" type="video/webm">
    <source src="assets/video/bangkok-reel.mp4" type="video/mp4">
  </video>

  <div class="hero__overlay" aria-hidden="true"></div>

  <!-- Steam-Animation (CSS-only) -->
  <div class="hero__steam" aria-hidden="true">
    <span class="steam steam--1"></span>
    <span class="steam steam--2"></span>
    <span class="steam steam--3"></span>
  </div>

  <div class="hero__content">
    <img src="assets/img/logo/regenzeit-logo.png"
         alt="Regenzeit" class="hero__logo" width="200" height="200">

    <p class="hero__slogan">When it rains, it smells like Bangkok.</p>

    <p class="hero__tagline">
      Thai-Nudelsuppen, die man nicht vergisst.<br>
      Hessestraße 4, Gostenhof.
    </p>

    <div class="hero__actions">
      <a href="#visit" class="btn btn-primary">Öffnungszeiten</a>
      <a href="https://www.google.com/maps/search/?api=1&query=Regenzeit+Nürnberg+Hessestraße+4"
         target="_blank" rel="noopener noreferrer" class="btn btn-outline">Anfahrt</a>
    </div>
  </div>

  <span class="hero__scroll" aria-hidden="true">Entdecken ↓</span>
</section>
```

**CSS Video + Overlay:**
```css
.hero__video {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 0;
}
.hero__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    rgba(26,18,8,0.4) 0%,
    rgba(26,18,8,0.7) 60%,
    rgba(26,18,8,0.95) 100%
  );
  z-index: 1;
}
.hero { background: linear-gradient(135deg, #1A1208 0%, #261C0E 100%); }
```

**CSS Steam-Animation:**
```css
@keyframes steam-rise {
  0%   { transform: translateY(0) scaleX(1); opacity: 0.6; }
  50%  { transform: translateY(-60px) scaleX(1.3); opacity: 0.3; }
  100% { transform: translateY(-120px) scaleX(0.8); opacity: 0; }
}
.steam {
  position: absolute;
  bottom: 30%;
  width: 40px;
  height: 60px;
  background: radial-gradient(ellipse, rgba(255,255,255,0.15) 0%, transparent 70%);
  border-radius: 50%;
  animation: steam-rise 3s ease-out infinite;
}
.steam--1 { left: 30%; animation-delay: 0s; }
.steam--2 { left: 50%; animation-delay: 1s; }
.steam--3 { left: 70%; animation-delay: 2s; }

@media (prefers-reduced-motion: reduce) {
  .hero__video, .hero__steam { display: none; }
}
```

### 5.6 Parallax-Effekt (CSS, kein JS)

```css
.section--parallax {
  background-attachment: fixed;
  background-size: cover;
  background-position: center;
}
@media (max-width: 768px) {
  .section--parallax { background-attachment: scroll; }
}
```

Anwenden auf: `.about` + `.menu` mit jeweiligem Atmosphäre-/Food-Foto.
Nicht auf Hero (hat Video) und nicht auf Visit/Footer.

### 5.7 Review-Ticker (neuer Abschnitt, zwischen Menu und Visit)

```html
<section class="review-ticker" aria-label="Was Gäste sagen">
  <div class="review-ticker__track">
    <div class="review-ticker__inner">
      <span>⭐⭐⭐⭐⭐ &nbsp;"Da riecht es wie in Thailand." &nbsp;·&nbsp;</span>
      <span>⭐⭐⭐⭐⭐ &nbsp;"Nudelsuppen, die man nicht vergisst." &nbsp;·&nbsp;</span>
      <span>⭐⭐⭐⭐⭐ &nbsp;"Ohne Schnickschnack — ehrlich, authentisch, lecker." &nbsp;·&nbsp;</span>
      <span>⭐⭐⭐⭐⭐ &nbsp;"Als wärst du mitten in Bangkok." &nbsp;·&nbsp;</span>
      <span>⭐⭐⭐⭐⭐ &nbsp;"Mein absolutes Lieblingsrestaurant." &nbsp;·&nbsp;</span>
      <!-- Inhalt doppeln für nahtlosen Loop: -->
      <span>⭐⭐⭐⭐⭐ &nbsp;"Da riecht es wie in Thailand." &nbsp;·&nbsp;</span>
      <span>⭐⭐⭐⭐⭐ &nbsp;"Nudelsuppen, die man nicht vergisst." &nbsp;·&nbsp;</span>
      <span>⭐⭐⭐⭐⭐ &nbsp;"Ohne Schnickschnack — ehrlich, authentisch, lecker." &nbsp;·&nbsp;</span>
      <span>⭐⭐⭐⭐⭐ &nbsp;"Als wärst du mitten in Bangkok." &nbsp;·&nbsp;</span>
      <span>⭐⭐⭐⭐⭐ &nbsp;"Mein absolutes Lieblingsrestaurant." &nbsp;·&nbsp;</span>
    </div>
  </div>
</section>
```

```css
.review-ticker {
  background: var(--color-surface);
  border-top: 1px solid rgba(255,140,0,0.2);
  border-bottom: 1px solid rgba(255,140,0,0.2);
  overflow: hidden;
  padding: 1rem 0;
}
.review-ticker__inner {
  display: flex;
  white-space: nowrap;
  animation: ticker-scroll 30s linear infinite;
  color: var(--color-text-muted);
  font-size: 0.9rem;
}
@keyframes ticker-scroll {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}
@media (prefers-reduced-motion: reduce) {
  .review-ticker__inner { animation: none; }
}
```

### 5.8 AI-Badge im Footer

```html
<a href="/regenzeit/llms.txt" class="ai-badge"
   title="Diese Seite ist für KI-Assistenten optimiert">
  🤖 AI-ready
</a>
```

```css
.ai-badge {
  font-size: 0.75rem;
  color: var(--color-text-muted);
  text-decoration: none;
  opacity: 0.6;
  transition: opacity 0.2s;
}
.ai-badge:hover { opacity: 1; color: var(--color-neon); }
```

---

## 6. Bildmaterial — aktueller Stand

**Bilder liegen bereits im lokalen Verzeichnis.** Vor dem Einbauen WebP konvertieren.

| Priorität | Verwendung | Zieldateiname |
|-----------|------------|---------------|
| ★★★ | Video-Poster + Hero-Fallback-BG | `hero-poster.jpg` |
| ★★★ | Open Graph Social Preview (1200×630) | `og-image.jpg` |
| ★★★ | Frosch-Logo auf transparentem/dunklem BG | `regenzeit-logo.png` |
| ★★ | Lek Haeng / Curry Nudeln Nahaufnahme | `dish-lek-haeng.jpg` |
| ★★ | Tom Yam Brühe mit Einlagen | `dish-tom-yam.jpg` |
| ★★ | Raumatmosphäre: Dachluke, Pflanzen, Licht | `interior.jpg` |
| ★ | Klebreis mit Mango | `dish-dessert.jpg` |
| ★ | Benno & Aey (optional) | `team.jpg` |

**Technisch:** `loading="lazy"` überall außer Hero-Poster. `<picture>` mit WebP + JPEG-Fallback.
`width`/`height` immer setzen.

---

## 7. Bangkok Reel (Video-Hero)

**Workflow:** Midjourney (Einzelframes) → Runway/Kling (Animation, 5–8s Loop) → WebM + MP4

**Midjourney Prompt:**
```
Bangkok street food stall at night, steam rising from giant wok,
orange neon light reflections on wet street, close-up on soup bowl,
cinematic, shallow depth of field, 35mm film grain,
dark moody atmosphere --ar 16:9 --style raw --v 6.1
```

**Variante mit Frosch-Referenz:**
```
Thai street food night market, monsoon rain on hot pavement,
steaming bowl of noodle soup in foreground, warm orange lantern light,
green tropical plants framing the scene, Bangkok authenticity,
cinematic food photography style --ar 16:9 --style raw --v 6.1
```

**Komprimierung (ffmpeg):**
```bash
ffmpeg -i input.mp4 -c:v libvpx-vp9 -b:v 0 -crf 35 -an output.webm
ffmpeg -i input.mp4 -c:v libx264 -crf 28 -an -movflags +faststart output-web.mp4
```

Zielgröße: WebM ~2–3MB, MP4 ~4–5MB. Kein Audio-Track.

---

## 8. Design-System

### Philosophie
**NICHT:** Europäisches Thai-Restaurant (hell, zen, curry-gelb auf weiß)
**JA:** Bangkok Nightmarket — dunkel, warm, handgemacht, leicht worn — aber immer
gefiltert durch die Regenzeit-DNA: der handgemalte Frosch, Benno & Aey, Gostenhof.
Authentizität kommt von innen, nicht von Klischees.

### Farbpalette
```css
:root {
  --color-bg:         #1A1208;
  --color-surface:    #261C0E;
  --color-surface-2:  #332510;
  --color-neon:       #FF8C00;
  --color-warm:       #E8C547;
  --color-heat:       #C0392B;
  --color-green:      #4A7C3F;
  --color-text:       #F5EDD8;
  --color-text-muted: #A89070;
}
```

### Typografie
```css
--font-display: 'Bebas Neue', Impact, sans-serif;   /* Headlines */
--font-thai:    'Noto Serif Thai', serif;            /* Dish-Namen */
--font-body:    'Inter', system-ui, sans-serif;      /* Fließtext */
```

### Details
- Cards: dunkle Fläche + `border-left: 3px solid var(--color-neon)` + Hover-Glow
- Divider: Frosch-Motiv (🐸) oder `·❋·` — kein `<hr>`
- Links: Neon-Orange, kein Blau
- Alle Animationen via CSS `@keyframes`, kein GSAP/ScrollMagic
- `prefers-reduced-motion`: Video, Steam, Ticker alle abschalten

---

## 9. Offene Punkte

- [ ] Logo: Midjourney-Ergebnis einbauen (Datei in `assets/img/logo/`)
- [ ] Video: Bangkok-Reel einbauen (Datei in `assets/video/`)
- [ ] Öffnungszeiten: mit Benno/Aey verifizieren
- [ ] E-Mail: `info@regenzeit-gostenhof.de` bestätigen lassen
- [ ] Impressum: vollständigen bürgerlichen Namen von Aey bestätigen
- [ ] OG-Image: als 1200×630px exportieren wenn Food-Shot bereit
- [ ] Domain: CNAME wenn `regenzeit-nuernberg.de` aktiviert wird
- [ ] Betreiber-Zitat: von Benno/Aey freigeben lassen

---

## 10. Reihenfolge der nächsten Build-Tasks

1. Fonts tauschen (Bebas Neue + Noto Serif Thai)
2. CSS-Variablen + theme-color + color-scheme updaten
3. Slogan + Subline updaten + Neon-Glow CSS
4. Logo einbauen (wenn Datei da, sonst Frosch-Emoji Placeholder)
5. Video-Hero HTML-Struktur + CSS (Video-Datei kommt nach)
6. Steam-Animation (CSS-only, sofort)
7. Review-Ticker einbauen
8. Parallax auf About + Menu
9. AI-Badge in Footer
10. Bilder einbauen + WebP konvertieren
