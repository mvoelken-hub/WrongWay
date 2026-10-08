# CLAUDE.md

## Projektbeschreibung

Diese Website repräsentiert ein lockeres Motorrad-Fun-Team. Die Mitglieder verbindet die Leidenschaft für gemeinsame Touren, Technik, Abenteuer und die Gemeinschaft unter Motorradfahrern.

Das Ziel der Website ist es, diese Begeisterung authentisch zu vermitteln und gleichzeitig einen modernen, hochwertigen und professionellen Eindruck zu hinterlassen.

## Designphilosophie

* Modernes, klares und aufgeräumtes Design.
* Hochwertige Optik statt überladener Effekte.
* Fokus auf gute Lesbarkeit und angenehme Nutzerführung.
* Großzügige Abstände und konsistente Gestaltung.
* Mobile-First und vollständig responsive.
* Dezente Animationen und sanfte Übergänge anstelle von auffälligen Spielereien.

## Farbkonzept

* **Hintergründe**: `bg-slate-950` (Seitenhintergrund), `bg-slate-900` (Karten), `bg-slate-800` (Karten zweiter Ebene), `bg-black` (Footer/Header)
* **Akzentfarbe**: Lime-Grün (`lime-500` / `lime-600`) — abgeleitet aus den Farben des Team-Logos. Diese Farbe wird für aktive Nav-Links, Buttons, Startnummer-Badges, Icons und Text-Links verwendet.
* **Hover auf Nav-Links**: `text-lime-400` (etwas heller als der Akzent)
* **Fließtext**: `text-slate-100` (Überschriften), `text-slate-300` (normaler Text), `text-slate-400` (sekundärer Text), `text-slate-500` (Labels/Hilfstext)
* Hoher Kontrast für optimale Lesbarkeit. Keine grellen oder unruhigen Farbkombinationen.
* Buttons mit Lime-Hintergrund erhalten schwarzen Text (`text-black`) für ausreichenden Kontrast.

## Typografie

* **Schriftart**: Inter (Google Fonts, Gewichte 400/500/600/700), eingebunden via `<link>` im `<head>` jeder Seite.
* Einbindung: `font-family: 'Inter', sans-serif` als inline-style auf `<body>`.
* Klare Hierarchie: `text-3xl font-semibold` für Seitenüberschriften (`<h2>`), `text-xl font-semibold` für Abschnittsüberschriften (`<h3>`/`<h4>`).
* Nav-Links: `text-sm uppercase font-medium tracking-wider`.
* Kurze, prägnante Texte statt langer Absätze.

## Aktuelles Seitenlayout

### index.html (Startseite)
* **Hero**: Zweispaltiges Grid (`md:grid-cols-2`). Links: Video (`videos/team.mp4`) in natürlicher Größe mit `rounded-2xl`. Rechts: Logo, Tagline „Benzin im Blut. Asphalt unter den Rädern.", Lime-Button „Lerne uns kennen".
* **Über uns**: Zwei Karten (`bg-slate-800 rounded-2xl`) nebeneinander mit Lime-Bullet-Punkten (▸).

### team.html
* 2-spaltiges Grid (`md:grid-cols-2`) mit 4 Team-Karten.
* Jede Karte: Foto (`h-72 object-cover`, `style="object-position: center 25%;"` für optimale Gesichtsdarstellung), Name, Startnummer in Lime, strukturierte `<dl>`-Liste mit Labels (Bike, Pitbike, Lieblingsstrecke, Erfahrung, Fun Fact).

### strecken.html
* Drei Kategorien (Pitbike, Rennstrecke, Straße) als eigenständige Abschnitte mit `border-t border-slate-800` als Trennlinie.
* Pitbike und Rennstrecke: **3-spaltiges Grid** (`md:grid-cols-3`) mit Bildkarten (`overflow-hidden`, Bild oben / Text unten).
* Straße: Einzelne Textkarte.
* Externe Links in Lime mit `underline`.

### galerie.html
* Masonry-Layout via `css/gallery.css` (4 Spalten).
* Bilder werden dynamisch aus `data/gallery.json` per `fetch()` in `js/gallery.js` geladen.
* **Wichtig**: Die Galerie benötigt einen HTTP-Server — beim direkten Öffnen als `file://` schlägt `fetch()` fehl. Lokal: `npx serve` (konfiguriert in `.claude/launch.json`, Port 3000).
* Lightbox mit Tastaturnavigation (←/→/Esc) und Klick auf Hintergrund zum Schließen.

### kontakt.html
* Zentrierte Karte (`max-w-2xl bg-slate-900 rounded-2xl`) mit Überschrift, Erklärungstext und Lime-Button zur E-Mail (`info.wrongway@gmail.com`).

## Assets

* **Logo**: `images/logo.png` — in allen Headern (`h-8 object-contain`) und im Hero der Startseite. Das Logo hat grün/gelbe Farben, daher wurde Lime als Akzentfarbe gewählt.
* **Team-Fotos**: `images/team/team_mischa.JPG`, `team_marc.JPG`, `team_pascal.jpg`, `team_vivi.jpg`
* **Strecken-Bilder**: `images/tracks/kartbahn_meppen.jpg`, `kartbahn_rheine.jpg`, `kartbahn_wuppertal.jpg`, `strecke_assen.jpg`, `strecke_meppen.jpg`, `strecke_oschersleben_2.jpg`
* **Video**: `videos/team.mp4` (Hero-Abschnitt, Startseite)
* Keine KI-generierten Platzhalter einführen.

## Navigation

* Jede Seite hat eine eigene Kopie des Headers.
* Der aktive Seitenlink erhält die Klasse `text-lime-500` (ohne `hover:`).
* Alle anderen Links: `hover:text-lime-400 transition-colors`.
* Mobile: Hamburger-Toggle (`#menuToggle` / `#navMenu`) mit `classList.toggle('hidden')`.

## Tech-Stack

* **HTML5**, kein Framework
* **Tailwind CSS v3** via CDN (`https://cdn.tailwindcss.com`) — JIT-Modus aktiv, arbitrary values funktionieren
* **Google Fonts**: Inter
* **Vanilla JS**: nur für Galerie (`js/gallery.js`) und Mobile-Menu (inline `<script>` in jedem HTML)
* Lokaler Dev-Server: `npx serve` (`.claude/launch.json`)

## Inhaltlicher Stil

Der Schreibstil soll freundlich, authentisch, sympathisch und leicht humorvoll sein, ohne ins Alberne abzurutschen. Texte sollen Begeisterung für das Motorradfahren vermitteln und Besucher willkommen heißen.

## UX-Richtlinien

* Weniger ist mehr.
* Einheitliche Komponenten verwenden (Karten immer `bg-slate-900 rounded-2xl p-6 shadow-lg`).
* Ausreichend Weißraum: Sektionen mindestens `py-20`.
* Animationen nur einsetzen, wenn sie den Nutzer unterstützen (`transition-colors` auf Links/Buttons).
* Performance und Barrierefreiheit berücksichtigen.

## Kreative Freiheit

Bei Unsicherheiten soll Claude eigenständig professionelle Designentscheidungen treffen und sich an modernen Webdesign-Standards orientieren, anstatt eine minimalistische oder improvisiert wirkende Lösung zu wählen.

## Ziel

Die Website soll den Eindruck vermitteln, dass hinter dem Motorrad-Team eine engagierte, freundliche und gut organisierte Gemeinschaft steht. Besucher sollen Lust bekommen, die Touren anzusehen, mehr über das Team zu erfahren und Teil der Community zu werden.
