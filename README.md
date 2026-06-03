# public imaging — Design System

Das markenkonforme Design-System von **public imaging**, einer Hamburger Finanz-PR-Agentur. Farb-Tokens, Web-Komponenten und 16:9-Folien-Templates — vollständig auf **Urbanist** aufgebaut.

Gemacht, damit Mensch und KI den Marken-Look jederzeit sauber reproduzieren können — von der Präsentation bis zum Interface.

**→ Live-Doku:** https://hpmunk-alt.github.io/public-imaging-design-system/

---

## Die eine Grundregel

Die Schrift ist **ausschließlich Urbanist** (300 Light – 800 ExtraBold). **Times New Roman wird nicht verwendet** — weder für Headlines noch für Fließtext.

---

## Was drin ist

| Bereich | Inhalt |
|---|---|
| **Tokens** | Farbe, Typografie, Abstand, Radius, Schatten, Bewegung — als CSS / JSON / SCSS |
| **Komponenten** | Buttons (alle States), Formulare, Karten, Badges/Tags, Nav, Tabs, Tabellen, Notes/Callouts, Trenner |
| **Folien** | Acht 16:9-Templates: Cover, Kapitel, Content, Daten, Zitat, Bild, Zwei-Spalten, Schluss |
| **Für KI** | `AI-GUIDE.md`, `brand-dna.json`, `tokens.json` + fertige Prompt-Vorlagen |

---

## Struktur

```
public-imaging-design-system/
├── index.html              # Live-Doku-Website (GitHub Pages)
├── tokens/
│   ├── tokens.css          # Design-Tokens als CSS-Variablen (--pi-*)
│   ├── tokens.json         # Tokens maschinenlesbar
│   └── tokens.scss         # Tokens als SCSS-Variablen
├── css/
│   ├── design-system.css   # Web-Komponenten + Foundations (lädt Urbanist)
│   └── slides.css          # 16:9-Folien-Framework
├── examples/
│   └── slides.html         # Alle 8 Folien-Templates gerendert
├── ai/
│   ├── AI-GUIDE.md          # KI-Leitfaden: Regeln, Komponenten, Prompts
│   ├── brand-dna.json       # Markenidentität (Urbanist-only)
│   └── tokens.json          # Tokens-Kopie für KI-Workflows
└── assets/
    ├── logo/                # Wortmarke (dunkel/hell) + Favicons
    └── img/                 # B&W-Beispielfotografie
```

---

## Schnellstart

**Web-UI:**
```html
<link rel="stylesheet" href="tokens/tokens.css">
<link rel="stylesheet" href="css/design-system.css">

<button class="pi-btn pi-btn--accent">Akzent</button>
<article class="pi-card"><h4 class="pi-h4">Titel</h4><p class="pi-body">Text</p></article>
```

**Folie:**
```html
<link rel="stylesheet" href="tokens/tokens.css">
<link rel="stylesheet" href="css/design-system.css">
<link rel="stylesheet" href="css/slides.css">

<div class="pi-slide pi-slide--gruen pi-slide--accent">
  <div class="pi-slide__inner pi-on-dark">
    <span class="pi-slide-overline">Präsentation · 2026</span>
    <h2 class="pi-slide-title">Titel der Folie</h2>
  </div>
</div>
```

Nie Werte hartkodieren — immer Tokens (`var(--pi-honig-gold)`) verwenden.

---

## Für KI-Systeme

Drei Dateien liefern die ganze Marken-DNA: [`ai/AI-GUIDE.md`](ai/AI-GUIDE.md) (Regeln + Prompt-Vorlagen), [`ai/brand-dna.json`](ai/brand-dna.json) und [`tokens/tokens.json`](tokens/tokens.json). Damit erzeugt eine KI markenkonforme Präsentationen und Interfaces auf Knopfdruck.

---

## Schrift einbinden

Urbanist wird von `design-system.css` automatisch über Google Fonts geladen. Alternativ:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Urbanist:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
```

---

## Lizenz &amp; Nutzung

Marke, Logo und Assets sind Eigentum der **public imaging GmbH**. Das Design-System ist für autorisierte Projekte im Auftrag der Agentur bestimmt. Kontakt: info@publicimaging.de

*Version 1.0 · Schrift: Urbanist · Hamburg 2026*
