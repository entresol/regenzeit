# CLAUDE.md — Regenzeit Website Project

> Dieses Dokument ist der vollständige Kontext für Claude Code.
> Es enthält: Projektherkunft, Recherche-Ergebnisse, Design-Entscheidungen und technischen Bauplan.
> Bitte vor dem ersten Task komplett lesen.

---

## 1. Projektherkunft & Auftrag

### Wer sind Benno & Aey Bartels?
Betreiber des Thai-Streetfood-Restaurants **Regenzeit** in Nürnberg-Gostenhof. Langjährige persönliche Freunde des Auftraggebers (Stefan Lischka, entresol.de). Das Projekt ist ein Freundschaftsdienst, kein kommerzieller Auftrag.

### Das Problem
Die Regenzeit ist ein Kult-Lokal mit 4,9 Sternen bei 630+ Google-Rezensionen — und hat trotzdem null eigenständige Web-Präsenz:
- Facebook-Seite: vorhanden, aber nicht gepflegt ("gruselig")
- Instagram-Account: stimmungsvoll, aktiv, aber kein Web-Ersatz
- Google Maps: einzige Quelle für Öffnungszeiten und Fakten
- Eigene Website: nicht vorhanden

Benno hat es mit Lovable (No-Code-Tool) versucht und ist gescheitert — nicht am Tool, sondern daran, dass er jemanden braucht, der die Arbeit einfach macht.

### Das Experiment
Ziel ist es zu zeigen, was heute technisch möglich ist: Aus öffentlich verfügbaren Quellen (Google Maps, Reviews, Instagram-Links) plus minimalem Input der Betreiber eine vollständige, moderne, zukunftsfähige Website bauen — inklusive llms.txt, Schema.org, SEO/GEO-Optimierung.

### Hosting
GitHub Pages: `entresol/regenzeit` → Interim-URL via `entresol.github.io/regenzeit`
Später: eigene Domain `regenzeit-nuernberg.de` (Wunsch, noch nicht bestätigt)

---

## 2. Recherche-Ergebnisse (verifiziert)

### Fakten
| Feld | Wert |
|------|------|
| Name | Regenzeit |
| Adresse | Hessestraße 4, 90443 Nürnberg |
| Stadtteil | Gostenhof |
| Telefon | 0911 18099765 |
| Küche | Authentisch Thai, Streetfood Bangkok-Stil |
| Preis | € (ca. 7–12 EUR pro Gericht) |
| Google Rating | 4,9 / 5 (630+ Rezensionen, Stand Jan 2025) |
| Öffnung neu | 24. Januar 2025 (neue Location) |
| Betrieben seit | 2014 (zuerst Willstraße 5, dann Hessestraße 4) |
| Vorgänger-Location | Willstraße 5, Gostenhof (geschlossen 20. Sep 2024) |
| Vorgänger-Mieter im neuen Gebäude | Naturkostladen Lotos (40 Jahre dort) |

### Gerichte (aus Speisekarte-Fragmenten, ggf. aktualisieren)
- **Lek Haeng** — warmes Gemüse, Kräuter, selbstgeröstete Erdnüsse (vegan/Huhn/Ente, 9–11,50 €)
- **Curry Nudeln** — Kokosmilchsauce, Erdnüsse, Röstzwiebeln, Gemüse, Kräuter (vegan/Huhn, 9,50–10,50 €)
- **Tom Yam** — Glasnudeln, Fisch, Muscheln, Garnelen, Surimi, Pilze (12 €)
- **Vegan** — Gemüse, Tofu, Pilze, Erdnüsse (7 €)
- **Klebreis mit Mango** — Dessert
- Alle Gerichte verfügbar: vegan, vegetarisch, mit Fleisch/Fisch

### Atmosphäre (aus Google/Tripadvisor-Reviews destilliert — kein direktes Zitat)
- Grüne Pflanzen, bunte Sofas, warmes Licht, leise Musik, Gemurmel
- Klein, persönlich, Retro-Möbel (alte Location) → neue Location: hell, großzügig, gläserne Dachluke
- Kinderspielecke, Free WLAN, gute Musik, entspannte Sessel
- LGBTQ+ freundlich
- Catering auf Anfrage
- Terrasse / Außenbereich vorhanden

### Zitate aus Reviews (Stimmungs-Referenz, nicht direkt verwenden)
> "Den der war gefüllt mit grünen Pflanzen, bunten Sofas, warmen Licht. Im Hintergrund leise Musik und Gemurmel."

> "Thai-Suppen wie sie sein sollen. Ohne SchnickSchnack, ehrlich, authentisch, lecker und variantenreich."

> "Geht zur Regenzeit, da riecht es wie in Thailand."

### Zitate der Betreiber (aus Facebook/Instagram-Posts)
> "Im neuen Jahr werden wir eine andere Gostenhofer Straße mit dem Duft der Thai-Nudelsuppen erfüllen."

> "Raum, Licht, Luft und Möglichkeiten — das neue Nest der Regenzeit."

> "Wir wollen mit den neuen Räumen mehr Unabhängigkeit von Aeys eigenem Einsatz."

---

## 3. Technische Entscheidungen (Begründungen)

### Warum kein Framework?
- Wartbarkeit: Benno soll später selbst Bilder tauschen können — kein Build-Step, kein npm
- Performance: Static HTML ist schneller als alles andere
- Hosting: GitHub Pages kann kein Node/Python — reines HTML/CSS/JS ist trivial
- Zukunftssicherheit: In 5 Jahren ist React X.Y veraltet, HTML nicht

### Warum kein Instagram-Embed (automatisch)?
Instagram Graph API erlaubt seit 2018 kein automatisches Pulling von Posts ohne Meta-App-Review. oEmbed (manuelle Einbettung einzelner Posts) ist erlaubt, aber keine dynamische Galerie. Lösung: Betreiber liefern Bilder manuell → sauber, kein ToS-Risiko.

### Warum llms.txt?
Standard im Entstehen (llmstxt.org). Ermöglicht KI-Assistenten strukturierten Zugriff auf Business-Informationen. Für ein Restaurant mit 4,9 Sternen ist Auffindbarkeit in KI-Antworten ("wo kann ich Thai-Suppen in Nürnberg essen?") relevanter als klassisches SEO.

### Warum Schema.org statt nur Meta-Tags?
Google nutzt strukturierte Daten für Rich Results (Sternebewertungen in SERPs, Öffnungszeiten direkt in der Suche, Knowledge Panel). Für ein lokales Restaurant ist das der größte SEO-Hebel überhaupt.

### Datenschutz
Kein Tracking, keine Cookies, kein Analytics → kein Cookie-Banner nötig. Google Maps als Click-to-Load (iframe wird erst nach Klick geladen) → DSGVO-konform.

---

## 4. Dateistruktur

```
/
├── index.html              ← Einseiter, alles drauf
├── llms.txt                ← KI-Lesbarkeit
├── robots.txt              ← Crawler-Steuerung
├── sitemap.xml             ← generiert nach finaler Domain
├── .nojekyll               ← PFLICHT für GitHub Pages (leere Datei)
└── assets/
    ├── css/
    │   └── style.css
    ├── img/
    │   ├── hero/           ← Placeholder bis Benno/Aey Fotos liefern
    │   │   └── hero-placeholder.jpg
    │   └── food/           ← Gerichte-Fotos
    └── fonts/              ← nur wenn self-hosted, sonst Google Fonts CDN
```

---

## 5. index.html — vollständige Spezifikation

### `<head>`
```html
<title>Regenzeit Nürnberg | Thai-Streetfood in Gostenhof</title>
<meta name="description" content="Authentisches Thai-Streetfood in Nürnberg-Gostenhof. Nudelsuppen, Reissalate und Currys wie in Bangkok. Vegan, vegetarisch und mit Fleisch. Hessestraße 4.">
<meta property="og:title" content="Regenzeit Nürnberg | Thai-Streetfood in Gostenhof">
<meta property="og:description" content="...">
<meta property="og:image" content="assets/img/hero/hero.jpg">
<meta property="og:url" content="https://entresol.github.io/regenzeit/">
<meta property="og:type" content="restaurant">
<meta name="twitter:card" content="summary_large_image">
<link rel="canonical" href="https://entresol.github.io/regenzeit/">
<meta name="theme-color" content="#8B1A1A">
```

### Schema.org JSON-LD (vollständig)
```json
{
  "@context": "https://schema.org",
  "@type": ["Restaurant", "FoodEstablishment"],
  "name": "Regenzeit",
  "description": "Authentisches Thai-Streetfood-Restaurant in Nürnberg-Gostenhof. Nudelsuppen, Reissalate und Currys im Bangkok-Stil.",
  "url": "https://entresol.github.io/regenzeit/",
  "telephone": "+4991118099765",
  "email": "PLACEHOLDER — von Benno erfragen",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Hessestraße 4",
    "postalCode": "90443",
    "addressLocality": "Nürnberg",
    "addressRegion": "Bayern",
    "addressCountry": "DE"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": "PLACEHOLDER — aus Google Maps",
    "longitude": "PLACEHOLDER — aus Google Maps"
  },
  "servesCuisine": ["Thai", "Streetfood", "Vegan", "Vegetarisch"],
  "priceRange": "€",
  "currenciesAccepted": "EUR",
  "paymentAccepted": "Cash, Credit Card",
  "hasMap": "https://maps.google.com/?q=Regenzeit+Nürnberg+Hessestraße+4",
  "openingHoursSpecification": [
    "PLACEHOLDER — aktuelle Zeiten von Benno"
  ],
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.9",
    "reviewCount": "630",
    "bestRating": "5"
  },
  "amenityFeature": [
    {"@type": "LocationFeatureSpecification", "name": "Vegan Options", "value": true},
    {"@type": "LocationFeatureSpecification", "name": "Vegetarian Options", "value": true},
    {"@type": "LocationFeatureSpecification", "name": "Takeaway", "value": true},
    {"@type": "LocationFeatureSpecification", "name": "Outdoor Seating", "value": true},
    {"@type": "LocationFeatureSpecification", "name": "Free WiFi", "value": true},
    {"@type": "LocationFeatureSpecification", "name": "Kids Area", "value": true},
    {"@type": "LocationFeatureSpecification", "name": "Catering", "value": true}
  ],
  "sameAs": [
    "PLACEHOLDER Instagram URL",
    "PLACEHOLDER Facebook URL",
    "PLACEHOLDER Google Maps URL"
  ]
}
```

### Sektionen (Reihenfolge im DOM)

**Hero**
- Vollbild-Hintergrundbild mit CSS-Gradient-Overlay als Fallback
- Wortmarke "Regenzeit" (groß, Serif)
- Subline: *"Thai-Streetfood wie in Bangkok. Mitten in Gostenhof."*
- Zwei CTAs: `[Öffnungszeiten]` (Anchor zu #visit) `[Anfahrt]` (Google Maps extern)

**Über uns**
- Geschichte: Seit 2014 in Gostenhof, Umzug Januar 2025 ins neue Nest
- Betreiber-Zitat (authentisch, von Benno/Aey freigeben lassen)
- 2-3 Atmosphäre-Bilder

**Speisekarte (Highlights)**
- Keine vollständige Karte — nur 4-6 Highlight-Dishes
- Kategorien: Suppen / Reis & Nudeln / Vegan / Dessert
- Disclaimer: "Speisekarte variiert je nach Saison und Verfügbarkeit"
- Link zu aktuellem Tagesangebot: Instagram

**Besuch planen**
- Öffnungszeiten (structured, auch für Schema.org)
- Adresse mit Click-to-Load Google Maps iframe
- Telefon (tel:-Link für Mobile)
- Catering-Hinweis mit Kontakt

**Footer**
- Instagram, Facebook (Icons + Links)
- © Regenzeit / Benno & Aey Bartels
- Impressum (Pflicht!)
- Datenschutz (minimal)

---

## 6. llms.txt (vollständig)

```
# Regenzeit Nürnberg

> Authentisches Thai-Streetfood-Restaurant in Nürnberg-Gostenhof

Betrieben von Benno und Aey Bartels seit 2014. Seit Januar 2025 in der
Hessestraße 4, 90443 Nürnberg. Inspiriertes Street-Food aus Bangkok —
Nudelsuppen, Reissalate, Currys. Alles auch vegan erhältlich.

## Gerichte
- Lek Haeng (warmes Gemüse, Kräuter, Erdnüsse)
- Curry Nudeln (Kokosmilch, Gemüse, Kräuter)
- Tom Yam (Glasnudeln, Meeresfrüchte, Pilze)
- Klebreis mit Mango (Dessert)
- Vegane Varianten aller Hauptgerichte verfügbar

## Besonderheiten
- Vegan, vegetarisch, mit Fleisch/Fisch
- Catering auf Anfrage
- Kinderspielecke
- Außenbereich
- Free WiFi
- LGBTQ+ freundlich

## Öffnungszeiten
PLACEHOLDER — aktuelle Zeiten von Betreibern erfragen

## Kontakt
Hessestraße 4, 90443 Nürnberg
Tel: 0911 18099765
Instagram: PLACEHOLDER
```

---

## 7. robots.txt

```
User-agent: *
Allow: /

# KI-Crawler explizit erlaubt
User-agent: GPTBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: anthropic-ai
Allow: /

Sitemap: https://entresol.github.io/regenzeit/sitemap.xml
```

---

## 8. Design-Spezifikation

### Farbpalette
```css
:root {
  --color-primary:    #8B1A1A;  /* Tiefes Thai-Rot */
  --color-secondary:  #C4832A;  /* Curry-Gelb/Orange */
  --color-accent:     #2D5016;  /* Tiefes Grün (Kräuter) */
  --color-bg:         #FAF6F0;  /* Warmes Off-White */
  --color-surface:    #FFFFFF;
  --color-text:       #1A1A1A;
  --color-text-muted: #6B5E52;
}
```

### Typografie
```css
/* Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Inter:wght@400;500&display=swap');

--font-display: 'Playfair Display', Georgia, serif;   /* Headlines */
--font-body:    'Inter', system-ui, sans-serif;        /* Fließtext */
```

### Grundregeln
- Mobile First — Breakpoint bei 768px
- Keine JavaScript-Frameworks — Vanilla JS nur für Maps Click-to-Load
- Bilder: `loading="lazy"`, `width`/`height` Attribute gesetzt (CLS vermeiden)
- WebP mit `<picture>` und JPEG-Fallback
- Keine Cookies, kein Tracking → kein Cookie-Banner

---

## 9. GitHub Pages Deployment

**Einfachster Weg (empfohlen):**
1. Repository Settings → Pages → Source: `Deploy from branch`
2. Branch: `main`, Folder: `/ (root)`
3. `.nojekyll` Datei im Root anlegen (leere Datei, verhindert Jekyll-Processing)

**Später bei eigener Domain:**
1. `CNAME` Datei mit `regenzeit-nuernberg.de` ins Root
2. DNS beim Provider: CNAME auf `entresol.github.io`
3. In GitHub Pages Settings "Enforce HTTPS" aktivieren

---

## 10. Offene Punkte — Input von Benno & Aey

Claude Code soll Platzhalter mit `<!-- TODO: ... -->` Kommentaren markieren:

- [ ] **Aktuelle Öffnungszeiten** (Google Maps könnte veraltet sein)
- [ ] **5–10 Fotos** Hero + Food (via WhatsApp oder WeTransfer)
- [ ] **Impressum-Daten** (vollständiger Name, Adresse — Pflicht DE)
- [ ] **Datenschutz-Verantwortliche/r** (vermutlich Benno Bartels)
- [ ] **E-Mail-Adresse** (Catering-Kontakt)
- [ ] **Social Media URLs** (Instagram + Facebook exakte Links)
- [ ] **Google Maps URL** (direkter Link zum Eintrag)
- [ ] **Wunsch-Domain** bestätigen (`regenzeit-nuernberg.de`?)
- [ ] **Betreiber-Zitat** freigeben (für Über-uns-Sektion)
- [ ] **Geo-Koordinaten** verifizieren (aus Google Maps ablesen)

---

## 11. Reihenfolge der Build-Tasks für Claude Code

1. Repo-Grundstruktur anlegen (alle Dateien/Ordner)
2. `.nojekyll` anlegen
3. `robots.txt` + `llms.txt` (mit Platzhaltern)
4. `style.css` (vollständiges Design-System, Mobile First)
5. `index.html` (vollständig, mit Schema.org JSON-LD, allen Platzhaltern)
6. Hero-Placeholder via CSS-Gradient (kein externes Bild nötig zum Start)
7. `sitemap.xml` (mit GitHub Pages URL als Basis)
8. README.md (kurze Doku für Benno: wie Bilder tauschen, wie Domain umstellen)

**Nicht jetzt:**
- Kontaktformular (braucht Backend oder Formspree — erst nach Domain-Entscheidung)
- Analytics (bewusst weggelassen)
- CMS-Integration (Benno braucht das nicht)
