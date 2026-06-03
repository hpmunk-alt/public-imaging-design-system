# public imaging — KI-Leitfaden

Diese Anleitung befähigt ein KI-System, **markenkonforme Präsentationen und Interfaces** für public imaging zu erzeugen. Wer diesen Leitfaden befolgt, produziert Ergebnisse, die auf den ersten Blick „public imaging" sind.

> **Die eine Grundregel:** Die Schrift ist **ausschließlich Urbanist**. Times New Roman wird **nicht** verwendet — weder für Headlines noch für Fließtext. Alles fußt auf der Urbanist-Familie (300 Light bis 800 ExtraBold).

---

## 1 · So nutzt du dieses System

Drei Dateien liefern alles:

| Datei | Zweck |
|---|---|
| `tokens/tokens.css` | Alle Design-Tokens als CSS-Variablen (`--pi-*`). In jedes HTML einbinden. |
| `css/design-system.css` | Web-Komponenten (Buttons, Formulare, Karten …). Lädt Urbanist automatisch. |
| `css/slides.css` | 16:9-Folien-Framework. |
| `ai/brand-dna.json` | Maschinenlesbare Markenidentität (Farben, Stimme, Bildwelt …). |
| `ai/tokens.json` | Tokens in JSON. |

**Standard-Einbindung (Web-UI):**
```html
<link rel="stylesheet" href="tokens/tokens.css">
<link rel="stylesheet" href="css/design-system.css">
```
**Für Folien zusätzlich:**
```html
<link rel="stylesheet" href="css/slides.css">
```

Niemals Farben oder Größen hartkodieren — immer die Tokens (`var(--pi-honig-gold)`) verwenden.

---

## 2 · Farbe

| Token | Hex | Einsatz |
|---|---|---|
| `--pi-elb-gruen` | `#15231E` | Dunkle Flächen, Headlines, Text auf Hell |
| `--pi-kontor-leinen` | `#F6F3ED` | **Dominante** Hintergrundfarbe (warmes Creme) |
| `--pi-honig-gold` | `#E6A23C` | Akzent — **max. 10 % Fläche** pro Ansicht |
| `--pi-speicher-grau` | `#6A6F6B` | Fließtext, sekundäre UI |
| `--pi-kuehler-salbei` | `#858C84` | Dekorative Flächen |
| `--pi-nardo-grau` | `#838484` | Captions, Metadaten |
| `--pi-pure-white` | `#FFFFFF` | Content-Karten, sparsam |

**Verhältnis (visuelle Gewichtung):** Kontor-Leinen 40 % · Elb-Grün 25 % · Weiß 15 % · Grautöne 12 % · Gold max. 8 %.

**Verboten:** reines `#000`, Neonfarben, Pastelltöne, Farbverläufe zwischen Markenfarben, Gradient-Text.

---

## 3 · Typografie (nur Urbanist)

Gewichte und ihr Einsatz:

| Gewicht | Einsatz |
|---|---|
| 300 Light | großer Lead-Text, Subtitles, Zitate |
| 400 Regular | Fließtext |
| 500 Medium | UI, Tags |
| 600 SemiBold | Overlines, Labels, Subheads |
| 700 Bold | H2 / H3 |
| 800 ExtraBold | Display, H1, große Zahlen, Wortmarke |

**Laufweite:** Headlines `-0.02em`, große Zahlen `-0.04em`, Labels/Overlines `0.2em` (Versalien), Buttons `0.12em` (Versalien), Wortmarke `-0.075em`.

**Regeln:** keine zweite Schrift · Overlines/Buttons immer Versalien mit Sperrung · lange Texte nie in Versalien.

Typo-Klassen: `.pi-display`, `.pi-h1`–`.pi-h4`, `.pi-lead`, `.pi-body`, `.pi-caption`, `.pi-kicker`.

---

## 4 · Web-Komponenten (Kurzreferenz)

```html
<!-- Buttons -->
<button class="pi-btn">Primär</button>
<button class="pi-btn pi-btn--accent">Akzent (Gold)</button>
<button class="pi-btn pi-btn--secondary">Sekundär (Outline)</button>
<button class="pi-btn pi-btn--ghost">Ghost</button>
<button class="pi-btn pi-btn--text">Text-Link</button>
<!-- Größen: pi-btn--sm / pi-btn--lg. Auf dunklem Grund: Eltern-Element .pi-on-dark -->

<!-- Overline / Kicker -->
<span class="pi-kicker">Brand Guideline</span>

<!-- Karte -->
<article class="pi-card pi-card--interactive">
  <span class="pi-kicker">01</span>
  <h4 class="pi-h4">Substanz</h4>
  <p class="pi-body">Text …</p>
</article>
<!-- Variante auf dunklem Grund: pi-card--dark -->

<!-- Formularfeld -->
<div class="pi-field">
  <label class="pi-label" for="name">Name</label>
  <input class="pi-input" id="name" placeholder="…">
</div>
<!-- Fehler: Eltern .pi-field--error + <span class="pi-error">…</span> -->

<!-- Checkbox / Radio -->
<label class="pi-check"><input type="checkbox"> Option</label>

<!-- Badge / Tag -->
<span class="pi-badge pi-badge--accent">Akzent</span>
<span class="pi-tag">Finanz-PR</span>

<!-- Hinweis (kein Side-Stripe — Gold-Hairline oben) -->
<div class="pi-note">
  <span class="pi-note__kicker">Regel</span>
  <p class="pi-note__body">…</p>
</div>

<!-- Trenner -->
<hr class="pi-divider">   <!-- kurze Gold-Linie -->
<hr class="pi-hairline">  <!-- volle dünne Linie -->
```

Tabs: `.pi-tabs` > `.pi-tab[role="tab"][aria-selected]`. Tabelle: `.pi-table`. Navigation: `.pi-nav` > `.pi-nav-link[aria-current]`.

---

## 5 · Folien-Templates (16:9)

Grundgerüst jeder Folie:
```html
<div class="pi-slide pi-slide--gruen pi-slide--accent">
  <div class="pi-slide__inner pi-on-dark">
    <span class="pi-slide-overline">Overline</span>
    <h2 class="pi-slide-title">Titel</h2>
  </div>
  <div class="pi-slide-footer pi-on-dark">
    <img class="pi-slide-footer__logo" src="assets/logo/pi-logo-weiss.png" alt="public imaging">
    <span class="pi-slide-footer__page">01</span>
  </div>
</div>
```

**Hintergründe:** `pi-slide--leinen` (hell), `pi-slide--gruen` (dunkel), `pi-slide--weiss`.
**Akzentlinie:** immer `pi-slide--accent` (Gold rechts).
**Auf dunklem Grund:** Inhalts-Container bekommt `pi-on-dark` (heller Text) und das Logo die weiße Variante.

Bausteine: `.pi-slide-title` (`--xl`, `--sm`), `.pi-slide-subtitle`, `.pi-slide-body`, `.pi-slide-lead`, `.pi-slide-stat` + `.pi-slide-stat-label`, `.pi-slide-quote` + `__mark`/`__cite`, `.pi-slide-list`, `.pi-slide-cols` (`--13`), `.pi-slide-stats`, `.pi-slide-chapter-no`, `.pi-slide-divider`, `.pi-slide-image` + `.pi-slide-scrim`.

Acht Standard-Layouts mit fertigem Markup: siehe **`examples/slides.html`**.

**Folien-Faustregeln:** max. drei Informationsblöcke pro Folie · große Zahlen in Gold · Fotos immer Schwarz-Weiß (`filter: grayscale(1)`) · Inhalt im sicheren Innenrand.

---

## 6 · Do &amp; Don't

**Do**
- Urbanist für alles. Gewichte für Hierarchie nutzen.
- Kontor-Leinen als Standardfläche, Elb-Grün für Kontrast-Folien.
- Gold sparsam, als Akzent (Linie, Zahl, Overline).
- Großzügiger Weißraum, ruhige Komposition.
- Fotos schwarz-weiß, editorial.

**Don't**
- ❌ Times New Roman oder irgendeine zweite Schrift.
- ❌ Reines Schwarz/Weiß als Markenfarbe (`#000`/grelles Weiß).
- ❌ Gold als große Fläche.
- ❌ Gradient-Text, Neon, Glassmorphismus, federnde Animationen.
- ❌ Seitliche Farbstreifen (`border-left`) als Deko.
- ❌ Ausrufezeichen und Superlative in der Sprache.

---

## 7 · Fertige Prompt-Vorlagen

**System-Prompt-Baustein (in jede KI-Session geben):**
```
Du gestaltest für public imaging, eine Hamburger Finanz-PR-Agentur.
Regeln:
- Schrift ausschließlich Urbanist (300–800). KEIN Times New Roman, keine zweite Schrift.
- Farben: Kontor-Leinen #F6F3ED (Standardfläche), Elb-Grün #15231E (Text/dunkle Flächen),
  Honig-Gold #E6A23C (Akzent, max. 10 % Fläche), Grautöne #6A6F6B/#858C84/#838484.
  Niemals reines Schwarz, kein Neon, keine Gradient-Texte.
- 2px Radius (kantig), subtile Schatten, filmische Bewegung (cubic-bezier(0.22,1,0.36,1)).
- Ton: klar, souverän, warm, präzise. Keine Ausrufezeichen, keine Superlative.
- Binde tokens.css + design-system.css (+ slides.css für Folien) ein und nutze die pi-* Klassen.
```

**Prompt — Präsentation:**
```
Erstelle eine [N]-Folien-Präsentation zum Thema [THEMA] für [MANDANT] im public-imaging-Look.
Nutze das Slide-Framework (css/slides.css), 16:9. Beginne mit einem Cover (Elb-Grün),
einem Kapitel-Trenner, Content-Folien mit Aufzählung, einer Daten-Folie mit großen Gold-Zahlen,
einem Zitat und einer Schluss-Folie mit Kontakt. Gold-Akzentlinie rechts auf jeder Folie.
Orientiere dich an examples/slides.html.
```

**Prompt — Web-UI / Komponente:**
```
Baue [KOMPONENTE/SEITE] im public-imaging-Design-System. Binde tokens.css + design-system.css ein,
verwende ausschließlich pi-* Klassen und Tokens. Urbanist, Kontor-Leinen-Fläche, Gold sparsam als
Akzent. Achte auf Button-States, Fokus-Ringe (Gold) und 44px-Touch-Targets.
```

---

*public imaging — Design System · Version 1.0 · Schrift: Urbanist*
