# Theaterwerk Website – GitHub Copilot Anleitung

## 🎭 Projektübersicht

Dies ist die Website des Vereins **Theaterwerk** (Reutlingen), eine junge Theaterpädagogikwerkstatt für Begegnung und Partizipation.

**GitHub Pages Basis:** Jekyll-basiertes Setup  
**Hosting:** GitHub Pages (GitHub Pages liest automatisch diese Konfiguration)  
**Live unter:** https://mirvollegal.github.io

## 🎨 Designsprache

Die Website basiert auf der Designsprache des Theaterwerk-Plakats:

### Farbpalette
- **Primär-Magenta:** `#C71E4C` (Kräftige, freundliche Hauptfarbe)
- **Primär-Pink:** `#E73D8C` (Hellere Variante)
- **Sekundär-Blau:** `#1E3B8F` (Kontrast-Textfarbe)
- **Akzent-Türkis:** `#2DB4A9` (Dekorative Elemente)
- **Akzent-Orange:** `#F5A623` (Weitere Highlights)
- **Hintergrund-Creme:** `#FDF8F3` (Warmtonig, einladend)
- **Hintergrund-Light-Pink:** `#F5E6E8`
- **Hintergrund-Light-Yellow:** `#FFFBEB`

### Design-Merkmale
- Freundlich, einladend, energisch
- Runde, organische Formen (border-radius: 8px, 12px, 25px)
- Farbverläufe und Gradients verwenden
- Moderne, aber warme Ästhetik
- Icons und Dekoration (z.B. Dots, Lines mit Farben)

## 📁 Projektstruktur

```
.
├── _config.yml              # Jekyll Konfiguration
├── _layouts/
│   └── default.html        # Haupt-Template mit Nav & Footer
├── _data/
│   └── kontakt.yml         # Kontaktdaten (YAML)
├── assets/
│   └── css/
│       └── style.css       # Haupt-Stylesheet (Farben, Layout)
├── index.md                # Startseite
├── ueber-uns.md            # Über uns
├── angebote.md             # Angebote & Kurse
├── kontakt.md              # Kontakt
└── README.md               # Projekt-Doku
```

## 📝 Wie man neue Seiten hinzufügt

### Methode 1: GitHub Web-Interface (empfohlen für einfache Bearbeitungen)

1. Gehe auf https://github.com/mirvollegal/mirvollegal.github.io
2. Klicke auf "Add file" → "Create new file"
3. Benenne die Datei: `seite-name.md` (z.B. `team.md`, `angebote-jugendliche.md`)
4. Führe diesen **Template** oben ein:

```markdown
---
layout: default
title: Seitentitel
subtitle: Untertitel (optional)
---

<div class="accent-line"></div>

## Hauptüberschrift

Dein Inhalt hier...

```

5. Commit und die Seite ist live! (URL wird: `/seite-name`)

### Methode 2: Lokal über Terminal (für komplexere Arbeiten)

```bash
# Repository lokal klonen
git clone https://github.com/mirvollegal/mirvollegal.github.io.git
cd mirvollegal.github.io

# Neue Seite erstellen
echo "---
layout: default
title: Meine Seite
---

Inhalt..." > meine-seite.md

# Lokal mit Jekyll testen (optional)
bundle install
bundle exec jekyll serve
# Dann öffne http://localhost:4000

# Änderungen hochladen
git add .
git commit -m "Neue Seite: Meine Seite"
git push
```

## 🎯 Best Practices für Inhalte

### Seitentitel & Struktur
- Seitentitel sollte **kurz, prägnant und aussagekräftig** sein
- Nutze Markdown-Header (`##`, `###`) für Gliederung
- Pro Seite 1-2 Hauptsektionen

### Texte schreiben
- **Warm, freundlich, einladend** – Tone of Voice des Vereins
- **Kurze Absätze** (max. 3 Sätze pro Paragraf)
- **Inklusive Sprache** verwenden (z.B. nicht nur "Schauspieler", sondern "Schauspielende")
- **Calls-to-Action** nutzen: Links, Buttons, E-Mail-Aufforderungen

### HTML-Elemente in Markdown

du kannst auch HTML direkt in Markdown einmischen:

```markdown
## Unser Angebot

<div class="grid">
  <div class="grid-item">
    <h3>🎭 Theatergruppe</h3>
    <p>Beschreibung...</p>
  </div>
  
  <div class="grid-item">
    <h3>📚 Workshops</h3>
    <p>Beschreibung...</p>
  </div>
</div>

<a href="mailto:kontakt@example.com" class="btn">Uns kontaktieren</a>
```

### CSS-Klassen für Styling

**Verfügbare Klassen:**
- `btn` – Button (Magenta)
- `btn-secondary` – Button (Blau)
- `grid` – Responsive Spalten-Layout
- `grid-item` – Element in Grid
- `content-section` – Weiße Inhaltsbox
- `info-card` – Farbige Highlight-Box
- `accent-line` – Bunte Dekorationslinie
- `text-center`, `mt-lg`, `mb-lg`, etc. – Utility-Klassen

**Beispiel:**
```markdown
<div class="info-card">
  <h4>💡 Wichtige Information</h4>
  <p>Hier geht dein Text hin...</p>
</div>
```

## 🔧 Navigation aktualisieren

Die Navigation wird in `_layouts/default.html` hardcoded. Um neue Seiten zur Nav hinzuzufügen:

1. Öffne `_layouts/default.html`
2. Finde den `<nav>`-Bereich
3. Füge einen neuen Link hinzu:

```html
<a href="{{ site.baseurl }}/neue-seite">Neue Seite</a>
```

## 📋 Kontaktdaten ändern

Die Kontaktdaten im Footer werden aus `_data/kontakt.yml` geladen:

```yaml
email: theaterwerk.info@gmx.de
telefon: "+49 176 82181505"
adresse:
  - "Museumstr. 7"
  - "72764 Reutlingen"
  - "Deutschland"
```

Diese Daten werden automatisch in der Navigation und im Footer angezeigt.

## 🚀 Live gehen

- **Automatisches Deployment:** Sobald du eine `.md`-Datei commitest, deployed GitHub Pages automatisch
- **Waiting Zeit:** Mit jekyll können neue Seiten nach 1-5 Minuten live sehen
- **URL-Schema:** `index.md` → `/`, `seite.md` → `/seite/`

## ⚠️ Häufige Fehler vermeiden

1. **Markdown YAML-Header vergessen:**
   ```markdown
   ---
   layout: default
   title: Mytitle
   ---
   ```
   → Ohne diesen Header wird die Seite nicht korrekt gerendert!

2. **Dateityp-Fehler:**
   - Verwende `.md` (Markdown), nicht `.html`, `.txt` etc.
   - Ausnahme: Dateien in `_layouts/` sind `.html`

3. **Sonderzeichen in Dateinamen:**
   - Nur Kleinbuchstaben, Bindestrich, Unterstrich verwenden
   - Nicht: `Neue-Seite.md` → Ja: `neue-seite.md`

4. **Absolute vs. relative URLs:**
   - Verwende `{{ site.baseurl }}/seite` für Links, nicht `/seite`
   - Beispiel: `[Link]({{ site.baseurl }}/kontakt)`

## 💡 Tipps für Copilot

Wenn du Copilot fragst, neuen Content zu generieren, gib folgende Infos:

**Goooder Prompt:**
> "Erstelle eine neue Seite für Theaterwerk über 'Team'. Die Seite sollte mit der Designsprache (Magenta, freundlich, einladend) matchen. Nutze die Farbklassen aus style.css und das default.html Layout. Zeige 3-4 Teammitglieder in einem grid-Item Layout."

**Schlechterer Prompt:**
> "Mach ne neue Seite"

## 📞 Support & Wartung

- **Fragen zu Jekyll:** https://jekyllrb.com/docs/
- **GitHub Pages Docs:** https://pages.github.com/
- **Markdown Syntax:** https://www.markdownguide.org/

---

**Viel Erfolg beim Aufbau der Website für Theaterwerk! 🎭✨**
