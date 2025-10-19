---
{"dg-publish":true,"dg-permalink":"setup","permalink":"/setup/"}
---

# Installation und erstes Setup für Website-Projekt mit cursor
# 🚀 Next.js 15 Website Setup - Komplettanleitung

> **Für:** Professionelle Next.js Websites mit Design System
> **Level:** Anfänger bis Fortgeschritten
> **Tech Stack:** Node.js 22 LTS + Next.js 15 + Tailwind CSS 3.4 + TypeScript + pnpm

**Zeit:** 30-60 Min (erstes Projekt) | 10-15 Min (weitere Projekte)

# Teil 0: Vorbereitung (BEVOR du startest!)
## 0.1 Accounts erstellen
### GitHub Account
1. **https://github.com/signup**
2. Kostenlosen Account erstellen
3. E-Mail bestätigen

**Warum?** Code-Versionierung & Vercel-Integration

---
### Vercel Account
1. **https://vercel.com/signup**
2. **Mit GitHub anmelden** (wichtig!)
3. Vercel mit GitHub verbinden (automatisch)

**Warum?** Kostenloses Hosting für deine Website

**Plan:** Hobby (kostenlos) reicht für Start!

---
### Claude Account (Content-Erstellung)
1. **https://claude.ai**
2. Account erstellen
3. Optional: Pro upgraden ($20/Monat)

**Warum?** Sitemap, Content, SEO-Texte schreiben

---
## 0.2 Software installieren
### Cursor IDE

1. **https://cursor.com**
2. Installiere für dein System
3. Öffne und schließe Einführung ab

**Subscription:**
- **Free:** Zum Testen ok
- **Pro ($20/Monat):** Empfohlen!

---
## 0.3 Checklist Vorbereitung
- [ ] GitHub Account ✅
- [ ] Vercel Account (mit GitHub verbunden) ✅
- [ ] Claude Account ✅
- [ ] Cursor installiert ✅
- [ ] Optional: Cursor Pro Abo ✅

**Alles erledigt? → Weiter zu Teil 1!**

# Teil 1: System-Voraussetzungen (EINMALIG)

## 1.1 Node.js 22 LTS installieren

**Download:** https://nodejs.org

**Installation:**
1. Lade **22.x LTS** herunter (NICHT 23.x!)
2. Installiere mit Standard-Einstellungen
3. Optional: Computer neu starten

**Check:**
```bash
node -v    # Sollte v22.x.x zeigen
npm -v     # Sollte 10.x.x zeigen
```

---

## 1.2 pnpm installieren

```bash
# macOS/Linux:
sudo npm install -g pnpm

# Windows (als Admin):
npm install -g pnpm
```

**Check:**
```bash
pnpm -v    # Sollte 9.x.x zeigen
```

---

## 1.3 Git konfigurieren

```bash
git config --global user.name "Dein Name"
git config --global user.email "deine@email.de"
git config --global init.defaultBranch main
```

**Check:**
```bash
git --version    # Sollte 2.x.x zeigen
```

---

## 1.4 GitHub CLI

```bash
# macOS:
brew install gh

# Windows:
winget install GitHub.cli
```

**Login:**
```bash
gh auth login
# Protocol: HTTPS oder SSH
# Authenticate: Login with web browser
```

**Check:**
```bash
gh auth status    # Sollte "Logged in" zeigen
```

---

# Teil 2: Neues Projekt erstellen

## 2.1 Projekt initialisieren

```bash
# Im Projektordner-Parent:
cd ~/Documents/projekte/

# Projekt erstellen mit pnpm:
pnpm create next-app@latest mein-projekt

# Einstellungen:
# TypeScript: Yes
# ESLint: Yes
# Tailwind CSS: Yes
# src/ directory: No
# App Router: Yes
# Turbopack: Yes
# Import alias: No

# In Projekt wechseln:
cd mein-projekt
```

---

## 2.2 Cursor Setup (AUTOMATISCH)

**Öffne Cursor im Projekt, dann dieser Prompt:**

```
Setup für dieses Projekt:

1. Tailwind CSS 3.4.18 (nicht v4!) - prüfe und korrigiere komplette Konfiguration
   - Entferne @tailwindcss/postcss falls vorhanden
   - Erstelle korrekte postcss.config.js
   - Korrigiere globals.css (nur @tailwind Direktiven)
   - Stelle sicher tailwind.config.ts hat content: [...] Array

2. Port [DEIN-PORT z.B. 3030] in package.json setzen (dev und start scripts)

3. LÖSCHE README.md aus dem Root

4. Erstelle /docs Ordner mit:
   - README.md (Dokumentations-Hub)
   - tech-stack.md (Next 15, React 19, Tailwind 3.4, Port [PORT], pnpm)
   - design-system.md (Farbpalette + Tailwind Config Vorlage)
   - sitemap.md (Struktur-Template)

Verwende professionelle Templates mit Platzhaltern zum Ausfüllen.
Zeige mir alle Änderungen.
```

> [!IMPORTANT]
> **Ersetze [DEIN-PORT] mit z.B. 3010, 3020, 3030**
> Das ist vor allem dann wichtig, wenn man mit dem KI-Editor auch andere Tools und Skripte bearbeitet und als Server starten lässt.

**Warte bis Cursor fertig ist.**

---

## 2.3 Port-Übersicht

```
Projekt 1: 3010
Projekt 2: 3020
Projekt 3: 3030
Projekt 4: 3040
```

Wähle einen freien Port!

---

## 2.4 Server testen

```bash
# Dependencies installieren
pnpm install

# Cache löschen (wichtig!)
rm -rf .next node_modules/.cache

# Server starten
pnpm dev
```

**Öffne:** http://localhost:[DEIN-PORT]

**Sollte Next.js Seite zeigen - ohne Fehler!** ✅

---
# Teil 2.5: Projekt-Dokumentation verstehen (WICHTIG!)

## Was ist gerade passiert?

Cursor hat einen `/docs` Ordner mit 4 Templates erstellt:

```
/docs/
├── README.md           # Dokumentations-Hub
├── tech-stack.md       # Tech-Infos (Port, Versionen)
├── design-system.md    # Farben, Fonts, Spacing
└── sitemap.md          # Seiten-Struktur
```

---

## 🧠 Warum ist das das "Gehirn" deines Projekts?

**Das ist deine "Single Source of Truth"!**

### Ohne diese Docs:

❌ Cursor erfindet jedes Mal neue Farben
❌ Cursor nutzt inkonsistente Styles
❌ Cursor weiß nicht, welche Seiten existieren sollen
❌ Jede Komponente sieht anders aus

### Mit diesen Docs:

✅ Cursor prüft **automatisch** die Dokumentation
✅ Cursor nutzt **nur definierte Farben**
✅ Cursor folgt **deiner Struktur**
✅ Konsistenter Code über das gesamte Projekt

---

## 🔗 Wie funktioniert die Magie?

**Deine Global Rules** (die du in Teil 4 erstellt hast) sagen Cursor:

```
Before writing ANY component with styles:
1. Check for design system documentation (in docs/)
```

**Das bedeutet:**

Wenn du sagst: `@Cursor Erstelle einen Button`

**Cursor macht:**
1. 🔍 Öffnet `docs/design-system.md`
2. 📖 Liest: "Primary Color: #60BEAF (neptune)"
3. 💻 Erstellt: `<Button className="bg-neptune">`

**NICHT:**
- ❌ `<Button className="bg-blue-500">` (random Farbe)
- ❌ `<Button style={{background: '#1234AB'}}>` (erfundene Farbe)

---

## 📝 Was du JETZT tun musst

Die Templates sind **Platzhalter** - du musst sie ausfüllen!

### 1. design-system.md (10 Min)

**Öffne:** `docs/design-system.md`

**Fülle aus:**
- Deine Farben (Hex-Codes + Namen)
- Deine Font (z.B. Inter, Roboto)
- Tailwind Config kopieren & anpassen

**Oder frag Cursor:**

```
Schlage mir eine professionelle Farbpalette für meine Website vor.
Zielgruppe: [deine Zielgruppe]
Branche: [deine Branche]
Stil: [Modern/Klassisch/etc.]

Aktualisiere docs/design-system.md damit.
```

---

### 2. sitemap.md (15 Min)

**Öffne:** `docs/sitemap.md`

**Plane:**
- Welche Seiten brauchst du?
- Wie sind die URLs?
- Was ist auf jeder Seite?

**Oder mit Claude (empfohlen):**

1. Claude-Projekt erstellen
2. Infos zu deinem Business hochladen
3. Prompt: "Erstelle eine Sitemap für meine Website"
4. Output nach `docs/sitemap.md` kopieren

---

### 3. tech-stack.md (2 Min)

**Öffne:** `docs/tech-stack.md`

**Meist schon korrekt befüllt!** Nur prüfen:
- Port richtig? (z.B. 3030)
- Domains richtig?
- Alle Versionen korrekt?

---

## ✅ Warum dieser Schritt so wichtig ist

**Ohne ausgefüllte Docs:**
- Cursor arbeitet "blind"
- Inkonsistente Ergebnisse
- Du musst ständig korrigieren

**Mit ausgefüllten Docs:**
- Cursor arbeitet wie ein gut-gebriefter Entwickler
- Konsistenter Code
- Schnellere Entwicklung
- Bessere Qualität

---

## 🎯 Quick-Check

**Sind deine Docs fertig?**

```bash
# Öffne jedes Dokument:
cat docs/design-system.md  # Farben definiert?
cat docs/sitemap.md        # Seiten geplant?
cat docs/tech-stack.md     # Infos korrekt?
```

**Wenn alle ausgefüllt:** ✅ Weiter zu Teil 3!

**Wenn noch Platzhalter:** ⏸️ Jetzt ausfüllen!

---

**Zeit investieren:** 15-30 Minuten in Docs
**Zeitersparnis:** Stunden später bei der Entwicklung! ⚡

**Das erklärt jetzt:**
- ✅ WARUM die Docs wichtig sind
- ✅ WIE Cursor sie nutzt (durch Global Rules!)
- ✅ WAS ausgefüllt werden muss
- ✅ Zeit-Investment vs. Zeitersparnis


---
# Teil 3: GitHub Repository

## 3.1 Check gh auth

```bash
gh auth status
```

Falls nicht angemeldet:
```bash
gh auth login
```

---

## 3.2 Repository erstellen

```bash
git add .
git commit -m "Initial setup: Next.js 15 + Tailwind 3.4"
gh repo create mein-projekt --private --source=. --remote=origin --push
```

**Beachte:** `--private` für Websites! 🔒

---

# Teil 4: Cursor Rules einrichten

## 4.1 Was sind Cursor Rules?

**Cursor Rules = Anweisungen für die KI in Cursor**

Es gibt **zwei Arten:**

| Type | Datei | Gilt für |
|------|-------|----------|
| **Global Rules** | In Cursor Settings | ALLE deine Projekte |
| **Project Rules** | `.cursorrules` im Projekt | NUR dieses Projekt |

**Unterschied:**
- **Global:** Deine generellen Präferenzen (pnpm, Code-Style)
- **Project:** Tech Stack, Design System, Architektur

---

## 4.2 Global Rules erstellen (einmalig für ALLE Projekte)

**In Cursor:**

1. Klicke **⚙️** (Zahnrad) 
2. "Rules and Memories"
3. "Add Rule"
4. Name: `General Development`
5. Inhalt:

```
Use pnpm exclusively (not npm or yarn)
Fetch logs from the console when debugging
Suggest performance improvements when reviewing code
Point out potential security issues and suggest solutions
Don't install packages unless explicitly asked
Prefer iteration and modularization over code duplication
Use available MCP servers for knowledgebase and understanding

### DESIGN SYSTEM ENFORCEMENT
Before writing ANY component with styles:
1. Check for design system documentation (usually in docs/ or _docs/)
2. Use only defined colors and spacing values
3. Follow established component patterns
4. Never invent custom design tokens
```

6. "Save"

**Das war's!** Diese Rules gelten jetzt für ALLE deine Projekte.

---

## 4.3 Project Rules erstellen (pro Projekt)

**In Cursor (im geöffneten Projekt):**

1. ⚙️ → "Rules and Memories"
2. Tab: **"Project Rules"**
3. "Add Rule"
4. Name: `[dein-projekt-name]`
5. Inhalt einfügen (siehe unten)
6. "Save"

---

### Option A: Cursor fragen (EMPFOHLEN!)

**Cursor Prompt:**

```
Erstelle Cursor Project Rules für dieses Projekt basierend auf:

Tech Stack:
- Next.js 15
- React 19
- Tailwind CSS 3.4
- TypeScript
- Port: [DEIN-PORT]
- Domains: [deine-domains]
- pnpm only

Fokus:
- Design System Enforcement (docs/design-system.md)
- TypeScript Best Practices
- Performance Optimization
- Accessibility (WCAG 2.1 AA)
- i18n (falls mehrsprachig)

Erstelle Professional-Level Project Rules.
```

**Cursor erstellt dann automatisch passende Rules!**

---

### Option B: Template verwenden

**Basis-Template (minimal):**

```
Expert in: TypeScript, Next.js 15, React 19, Tailwind CSS 3.4

### Project
- Port: [DEIN-PORT]
- Domains: [deine-domain.de]
- pnpm only

### Code
- TypeScript
- Functional components
- Mobile-first

### Design
- Check docs/design-system.md before styling
- Use defined colors only
```

---

### Option C: Vollständiges Template (für Corporate Websites)

**Für professionelle Websites mit Design System:**

```
### DESIGN SYSTEM (IMPORTANT!)

**CENTRAL DESIGN DOCUMENT:** docs/design-system.md

For ALL visual decisions (colors, spacing, typography, component patterns):
1. ALWAYS check the Design System first
2. NEVER invent custom colors
3. ONLY use Tailwind classes from the Design System

---

You are an expert in TypeScript, Node.js, Next.js 15, React 19, Tailwind CSS 3.4, and Shadcn UI.

### Project Specifics
- Port: [DEIN-PORT]
- Domains: [domain.de], [domain.com] (falls mehrsprachig)
- pnpm ONLY

### Code Style
- Functional components with TypeScript
- Named exports
- Interfaces instead of types
- Descriptive variable names (isLoading, hasError)

### UI and Styling
- Shadcn UI + Radix for components
- Tailwind CSS 3.4 (ALWAYS use Design System classes)
- Mobile-first responsive
- WCAG 2.1 Level AA

### Performance
- Minimize 'use client'
- Server Components default
- Lazy load non-critical components
- Optimize images (WebP, lazy-load)

### i18n (falls mehrsprachig)
- Domains: [domain.de] (DE), [domain.com] (EN)
- Translations: locales/de/ and locales/en/
- Domain-based routing (NO /de or /en prefixes)

### Key Conventions
- Always check docs/design-system.md BEFORE styling
- Optimize Core Web Vitals
- GDPR compliant
```

---

## 4.4 Welches Template wählen?

| Projekt-Typ | Template |
|-------------|----------|
| Einfache Website | Option B (Minimal) |
| Corporate Website | Option C (Vollständig) |
| Unsicher? | Option A (Cursor fragen!) |

---

## 4.5 Rules testen

**Cursor fragen:**

```
@Cursor Welche Rules sind aktiv? Fasse zusammen.
```

Cursor sollte deine Rules zusammenfassen!

**Praktischer Test:**

```
@Cursor Erstelle eine Button-Komponente
```

Cursor sollte:
- ✅ Design System prüfen
- ✅ TypeScript verwenden
- ✅ Deine Conventions befolgen

---

## 4.6 Rules später anpassen

**Global Rules:**
⚙️ → Rules → Deine Rule auswählen → Bearbeiten

**Project Rules:**
⚙️ → Rules → Project Rules → Deine Rule → Bearbeiten

**Nach Änderung:**
- Cursor neu laden: Cmd/Ctrl + Shift + P → "Reload Window"

---

**Fertig!** Cursor kennt jetzt deine Regeln. ✅

---

**Das ist jetzt Teil 4 komplett:**
- ✅ Global vs Project Rules erklärt
- ✅ Deine Global Rules als Beispiel
- ✅ 3 Optionen für Project Rules
- ✅ Hinweis auf Cursor fragen
- ✅ Testing & Anpassung

**Ready zum Kopieren!** 🎯

---

# Teil 5: Shadcn UI

```bash
pnpm dlx shadcn@latest init

# Einstellungen:
# TypeScript: Yes
# Style: Default
# Color: Stone
# CSS variables: Yes

# Basis-Komponenten:
pnpm dlx shadcn@latest add button card input label
```

---

# Teil 6: Design System anpassen

**Cursor Prompt (optional - wenn spezifische Farben):**

```
Aktualisiere tailwind.config.ts und docs/design-system.md mit diesen Farben:

Primary: #HEXCODE
Secondary: #HEXCODE
Accent: #HEXCODE
[weitere Farben...]

Füge vollständige Tailwind Config mit allen Farben hinzu.
Dokumentiere in docs/design-system.md.
```

**Oder:** Fülle Templates manuell aus (docs/design-system.md, tech-stack.md)

---

# Teil 7: Vercel Deployment (Optional - Hosting)

## 7.1 Wann deployen?

**Jetzt schon?** Optional - du kannst später deployen.

**Vorteil früh deployen:**
- Live-URL sofort verfügbar
- Automatische Deployments bei git push
- Teste auf echter Domain

---

## 7.2 Vercel mit GitHub verbinden

**Falls noch nicht verbunden:**

1. Gehe zu: **https://vercel.com/dashboard**
2. "Add New Project"
3. "Import Git Repository"
4. Autorisiere Vercel für GitHub

**Sollte bereits verbunden sein, wenn du dich mit GitHub angemeldet hast!**

---

## 7.3 Projekt deployen

**Methode A: Über Vercel Dashboard (GUI)**

1. **https://vercel.com/new**
2. Wähle dein GitHub Repository aus der Liste
3. **Framework Preset:** Next.js (automatisch erkannt)
4. **Build Settings:**
   - Build Command: `pnpm build` (automatisch)
   - Output Directory: `.next` (automatisch)
   - Install Command: `pnpm install` (automatisch)
5. **Environment Variables:** Keine (für jetzt)
6. Klicke **"Deploy"**

**Vercel macht:**
- ✅ Code von GitHub holen
- ✅ Dependencies installieren
- ✅ Build erstellen
- ✅ Deployen
- ✅ Live-URL generieren

**Zeit: ~2-3 Minuten**

---

**Methode B: Mit Vercel CLI (Terminal)**

```bash
# Vercel CLI installieren
pnpm add -g vercel

# In Projektordner
cd mein-projekt

# Deployen
vercel

# Fragen beantworten:
# Set up and deploy? Yes
# Which scope? [dein-account]
# Link to existing project? No
# Project name? [projektname]
# Directory? ./
# Override settings? No
```

---

## 7.4 Nach Deployment

**Vercel zeigt:**
```
✅ Deployed to production
🔗 https://mein-projekt.vercel.app
```

**Was passiert ist:**
- ✅ Website ist LIVE!
- ✅ Automatische SSL (HTTPS)
- ✅ Globales CDN
- ✅ Bei jedem `git push` → automatisches Re-Deployment

---

## 7.5 Custom Domain verbinden (später)

**Falls du eine eigene Domain hast:**

1. Vercel Dashboard → Dein Projekt → "Domains"
2. "Add Domain"
3. Domain eingeben: `meine-domain.de`
4. DNS-Einträge bei deinem Domain-Provider setzen:
   ```
   A Record: 76.76.21.21
   CNAME: cname.vercel-dns.com
   ```
5. Warten (~5-60 Min)
6. **Fertig!** Website läuft auf deiner Domain

---

## 7.6 Automatisches Deployment

**Ab jetzt:**

```bash
# Code ändern
git add .
git commit -m "Update Homepage"
git push

# Vercel deployt automatisch!
# Nach ~2 Min: Änderungen sind live
```

**Kein manuelles Deployment mehr nötig!** 🚀

---

## 7.7 Deployment-Übersicht

```
GitHub Repo (dein-projekt)
        ↓
    git push
        ↓
Vercel (erkennt Push automatisch)
        ↓
Build & Deploy
        ↓
Live: https://projekt.vercel.app
```

**Das war's!** ✅


# ✅ Komplette Setup Checklist

## Vorbereitung
- [ ] GitHub Account erstellt
- [ ] Vercel Account (mit GitHub verbunden)
- [ ] Claude Account erstellt
- [ ] Cursor installiert
- [ ] Cursor Subscription gewählt

## System-Tools (einmalig)
- [ ] Node.js 22+ installiert
- [ ] pnpm installiert
- [ ] Git konfiguriert
- [ ] GitHub CLI installiert & angemeldet

## Projekt Setup
- [ ] Next.js Projekt erstellt (pnpm create next-app)
- [ ] Cursor: Tailwind 3.4 + Port + Docs
- [ ] Server läuft lokal ohne Fehler
- [ ] GitHub Repo erstellt (private!)
- [ ] Cursor Project Rules gespeichert
- [ ] Shadcn UI installiert

## Deployment (optional)
- [ ] Vercel Projekt erstellt
- [ ] Erste Deployment erfolgreich
- [ ] Live-URL funktioniert

## Content (nächster Schritt)
- [ ] Sitemap in docs/sitemap.md
- [ ] Mit Claude Content schreiben
- [ ] Cursor lässt Struktur erstellen

**Alles abgehakt? 🎉 Los geht's mit der Website!**


# Nächste Schritte: Content & Website-Aufbau

## Workflow-Übersicht

```
PHASE 1: Content-Planung (Claude)
└─ Sitemap erstellen
└─ Texte schreiben
└─ SEO planen

PHASE 2: Technischer Aufbau (Cursor)
└─ Struktur erstellen
└─ Content einfügen
└─ Design umsetzen

PHASE 3: Optimierung (Cursor)
└─ Text-Anpassungen
└─ Design-Tweaks
└─ SEO-Optimierung
```

---

## Phase 1: Content mit Claude vorbereiten

### 1.1 Claude-Projekt erstellen

**Gehe zu:** https://claude.ai

**Erstelle neues Projekt:**
1. "New Project"
2. Name: `[deine-website] Content`
3. "Create Project"

---

### 1.2 Wissensbasis hochladen

**Lade diese Dateien als Project Knowledge hoch:**

- `unternehmen.md` - Über dein Unternehmen
- `services.md` - Deine Services/Produkte
- `zielgruppe.md` - Deine Zielgruppen
- `faqs.md` - Häufige Fragen
- `unique-value.md` - Dein Alleinstellungsmerkmal

**Beispiel-Struktur:**

```markdown
# unternehmen.md
- Name, Gründungsjahr
- Geschichte
- Team
- Referenzen

# services.md
- Service 1: Beschreibung, Features, Nutzen
- Service 2: ...
```

---

### 1.3 System-Prompt erstellen

**Custom Instructions für das Projekt:**

```markdown
Du bist SEO- und Content-Stratege für [Projektname].

Erstelle professionelle Website-Inhalte:
- SEO-optimiert (Title, Description, Keywords)
- Zielgruppe: [deine Zielgruppe]
- Tonalität: Professionell, B2B/B2C
- Struktur: Hero, Sections, CTAs, FAQs

Format:
- Markdown
- Klare Überschriften (H1-H3)
- SEO-Metadaten pro Seite
- Technische Specs für Entwickler

Verwende NUR Informationen aus den hochgeladenen Dateien.
```

**Oder:** Nutze ein vollständiges Template (siehe Anhang für Beispiel)

---

### 1.4 Sitemap erstellen lassen

**Claude Prompt:**

```
Erstelle eine vollständige Sitemap für meine Website basierend auf den hochgeladenen Informationen.

Struktur:
1. URL-Übersicht (DE und/oder EN)
2. Pro Seite:
   - SEO (Title, Description, Keywords)
   - Content-Struktur (Hero, Sections)
   - Technische Specs

Format: Markdown, direkt verwendbar für Cursor.
```

**Claude erstellt:** Eine detaillierte `sitemap.md` wie im OSINT-Projekt

---

### 1.5 Einzelne Seiten detaillieren

**Nach Sitemap, pro Seite:**

```
Schreibe vollständigen Content für die Homepage:
- Hero Section
- Service-Übersicht
- Trust-Elemente
- FAQ
- CTA

SEO-optimiert, ready für Cursor.
```

**Speichere Claudes Output als:**
- `content-homepage-de.md`
- `content-services-de.md`
- etc.

---

## Phase 2: Cursor baut Website

### 2.1 Sitemap zu Cursor geben

**Kopiere die Claude-Sitemap nach:** `docs/sitemap.md`

**Cursor Prompt:**

```
Basierend auf docs/sitemap.md:

1. Erstelle komplette Ordnerstruktur in /app
   - Deutsche Seiten im Root
   - Englische in /en (falls mehrsprachig)

2. Erstelle alle page.tsx Dateien:
   - Mit SEO Metadata aus Sitemap
   - Mit Basis-Hero-Structure
   - Mit Kommentaren wo Content kommt

3. Erstelle Navigation (components/layout/Navigation.tsx)
4. Erstelle Footer (components/layout/Footer.tsx)

Verwende Design System aus docs/design-system.md.
```

**Cursor erstellt die komplette Struktur!**

---

### 2.2 Content einfügen

**Pro Seite:**

```
Füge diesen Content in app/page.tsx ein:

[Content aus Claude kopieren]

Verwende Design System, erstelle passende Komponenten.
```

---

## Phase 3: Optimierungen in Cursor

**Ab jetzt alles in Cursor:**

```
Ändere Hero-Text auf Homepage zu: [neuer Text]
```

```
Optimiere CTA-Button-Farben für bessere Conversion
```

---

## Tipps & Best Practices

### Content-Versionierung

**Speichere Claude-Outputs als Markdown:**

```
/content/
├── de/
│   ├── homepage.md
│   ├── services.md
│   └── contact.md
└── en/
    ├── homepage.md
    └── services.md
```

**Vorteil:** Immer Original-Texte verfügbar, versioniert in Git!

---

### Claude System-Prompt Template

**Vollständiges Beispiel (gekürzt):**

```markdown
# Rolle
Du bist SEO- und Content-Stratege für [Unternehmen].

# Aufgabe
Erstelle professionelle, SEO-optimierte Website-Inhalte.

# Stil
- Zielgruppe: [B2B/B2C]
- Tonalität: [Professionell/Locker]
- Anrede: [Sie/Du]

# Format
- Markdown
- SEO-Metadaten (Title, Description)
- Technische Specs für Entwickler

# Regeln
- Nur Infos aus Project Knowledge
- Keine Erfindungen
- Aktive Sprache
- Scanbare Absätze

# Output-Struktur
1. SEO-Strategie
2. Content-Struktur
3. Volltext pro Section
4. Technische Specs
```

---

### Content-Checkliste pro Seite

- [ ] SEO Title (50-60 Zeichen)
- [ ] Meta Description (150-160 Zeichen)
- [ ] H1 Headline
- [ ] Hero-Text
- [ ] 3-5 Hauptsektionen
- [ ] FAQ (falls relevant)
- [ ] CTA
- [ ] Technische Specs für Cursor

---

## Zusammenfassung

**3-Phasen-Workflow:**

1. **Claude:** Plant & schreibt (Sitemap, Content, SEO)
2. **Cursor:** Baut & strukturiert (Code, Design, Komponenten)
3. **Cursor:** Optimiert & tweakt (Anpassungen, Verbesserungen)

**Trennung der Verantwortlichkeiten:**
- Claude = Content-Strategie & Texte
- Cursor = Technische Umsetzung
- Du = Qualitätskontrolle & Entscheidungen

**Vorteile:**
- ✅ Claude ist besser in langen Texten & SEO-Strategie
- ✅ Cursor ist besser in Code & Design
- ✅ Du behältst Kontrolle über Content
- ✅ Versionierte Content-Dateien in Git

---

**Bereit?** Starte mit Claude-Projekt! 🚀



---

# Quick Setup: Weitere Projekte

**Wenn System-Tools bereits installiert (Node, pnpm, Git, gh):**

## 1. Projekt erstellen

```bash
cd ~/Documents/projekte/
pnpm create next-app@latest neues-projekt
cd neues-projekt
```

## 2. Cursor Setup

**Cursor Prompt:**

```
Setup:
1. Tailwind 3.4.18 (korrigiere v4 falls installiert)
2. Port [NÄCHSTER-PORT] in package.json
3. Lösche Root README.md
4. Erstelle /docs mit Templates (README, tech-stack, design-system, sitemap)
```

## 3. Server testen

```bash
pnpm install
rm -rf .next
pnpm dev
```

## 4. GitHub & Rules

```bash
git add .
git commit -m "Initial setup"
gh repo create projekt --private --source=. --remote=origin --push
```

Cursor Rules erstellen (siehe Teil 4)

## 5. Shadcn UI

```bash
pnpm dlx shadcn@latest init
pnpm dlx shadcn@latest add button card input
```

**Fertig in ~10 Min!** ⚡

---

# Templates für /docs

## Template: tech-stack.md

```
# Tech Stack: [Projektname]

Erstellt: [Datum]

## System
- Node.js: [Version]
- pnpm: [Version]

## Framework
- Next.js: [Version]
- React: [Version]
- TypeScript: [Version]

## Styling
- Tailwind CSS: [Version]
- Shadcn UI: [Ja/Nein]

## Development
- Port: [Port]
- Turbopack: [Ja/Nein]

## i18n (falls mehrsprachig)
- Domains: [domain.de], [domain.com]
- Routing: Domain-basiert

## Deployment
- Platform: [Vercel]
- GitHub: [URL]
```

---

## Template: design-system.md

```
# Design System: [Projektname]

## 1. FARBEN

Farbe       | Hex      | Tailwind    | Verwendung
------------|----------|-------------|------------
[Name]      | #HEXCODE | farbe-name  | Beschreibung
[Name]      | #HEXCODE | farbe-name  | Beschreibung

## 2. TYPOGRAFIE

Font: [z.B. Inter]
H1: text-5xl font-light
H2: text-3xl font-light
Body: text-base

## 3. SPACING

Section: py-20 md:py-32
Container: max-w-[1200px]

## 4. TAILWIND CONFIG

```typescript
import type { Config } from 'tailwindcss'

const config: Config = {
  content: [
    './pages/**/*.{js,ts,jsx,tsx,mdx}',
    './components/**/*.{js,ts,jsx,tsx,mdx}',
    './app/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {
      colors: {
        // Deine Farben hier
      },
    },
  },
  plugins: [],
}

export default config
```


---

## Template: sitemap.md

```
# Sitemap: [Projektname]

## Domains
- [domain.de] oder [domain.com]

## Seiten

/                  # Homepage
/about/            # Über uns
/services/         # Services
/contact/          # Kontakt
/impressum/        # Impressum
/datenschutz/     # Datenschutz

## Seiten-Details

### Homepage (/)
- Hero
- Features
- CTA

### Services (/services)
- Service Liste
- Details

### Contact (/contact)
- Formular
- Kontaktdaten
```

---
