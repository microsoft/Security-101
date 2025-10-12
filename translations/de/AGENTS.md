<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:24:24+00:00",
  "source_file": "AGENTS.md",
  "language_code": "de"
}
-->
# AGENTS.md

## Projektübersicht

**Security-101** ist ein anfängerfreundliches Cybersecurity-Curriculum, das von Microsoft erstellt wurde. Das Projekt ist eine dokumentationsbasierte Lernressource, die grundlegende Cybersecurity-Konzepte durch strukturierte Module vermittelt. Es ist herstellerunabhängig und so konzipiert, dass es in kleinen Lektionen (jeweils 30-60 Minuten) abgeschlossen werden kann.

**Wichtige Technologien:**
- Markdown für Inhalte
- Docsify für die Generierung statischer Websites
- GitHub Pages für das Hosting
- Co-op Translator für mehrsprachige Unterstützung (50+ Sprachen)
- GitHub Actions für CI/CD

**Architektur:**
- Bildungsinhalte, organisiert in 8 Hauptmodule, jedes mit Unterlektionen
- Statische HTML-Website mit Docsify, das Markdown-Inhalte rendert
- Automatisierter Übersetzungsworkflow mit Azure AI-Diensten
- Keine Build-Tools oder Paketmanager für die Kerninhalte erforderlich

## Repository-Struktur

```
/
├── README.md                    # Main entry point with curriculum overview
├── index.html                   # Docsify site entry point
├── [1-8].[1-4] *.md            # Curriculum modules and lessons
├── CODE_OF_CONDUCT.md          # Community guidelines
├── SECURITY.md                 # Security policy
├── SUPPORT.md                  # Support information
├── LICENSE                     # MIT License
├── images/                     # Image assets for lessons
├── translated_images/          # Translated image assets
├── translations/               # Translated versions (50+ languages)
└── .github/
    ├── workflows/
    │   ├── co-op-translator.yml    # Automated translation workflow
    │   ├── deploy.yaml             # GitHub Pages deployment
    │   └── jekyll-gh-pages.yml     # Jekyll site generation
    └── ISSUE_TEMPLATE/             # Issue templates
```

## Setup-Befehle

Dies ist ein Dokumentationsprojekt ohne zu installierende Abhängigkeiten. Um mit den Inhalten zu arbeiten:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Entwicklungsworkflow

### Inhalte lokal anzeigen

Das Projekt verwendet Docsify für die Darstellung. Um Änderungen vorzuschauen:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Inhaltsstruktur

Die Module sind fortlaufend nummeriert:
- **Modul 1:** Grundlegende Sicherheitskonzepte (1.1-1.7)
- **Modul 2:** Identitäts- und Zugriffsmanagement (2.1-2.4)
- **Modul 3:** Netzwerksicherheit (3.1-3.4)
- **Modul 4:** Sicherheitsoperationen (4.1-4.4)
- **Modul 5:** Anwendungssicherheit (5.1-5.3)
- **Modul 6:** Infrastruktursicherheit (6.1-6.3)
- **Modul 7:** Datensicherheit (7.1-7.3)
- **Modul 8:** KI-Sicherheit (8.1-8.4)

Jedes Modul endet mit einer Quiz-Datei (z. B. "1.7 End of module quiz.md").

### Änderungen an Inhalten vornehmen

1. Bearbeiten Sie die Markdown-Dateien direkt im Stammverzeichnis
2. Befolgen Sie die bestehende Namenskonvention: `[module].[lesson] [Title].md`
3. Aktualisieren Sie die Tabelle in README.md, wenn Module hinzugefügt oder entfernt werden
4. Fügen Sie Bilder im Verzeichnis `/images/` hinzu
5. Verweisen Sie auf Bilder mit relativen Pfaden: `![Beschreibung](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.de.png)`

## Übersetzungsworkflow

**Automatische Übersetzung:**
- Übersetzungen werden automatisch durch die Co-op Translator GitHub Action durchgeführt
- Wenn Sie Änderungen in den `main`-Branch pushen, übersetzt der Workflow Inhalte in über 50 Sprachen
- Übersetzte Dateien werden in `/translations/[language_code]/` gespeichert
- Übersetzungs-Metadaten werden im YAML-Frontmatter beibehalten

**Unterstützte Sprachen:** Arabisch, Bengalisch, Bulgarisch, Burmesisch, Chinesisch (vereinfacht, traditionell), Kroatisch, Tschechisch, Dänisch, Niederländisch, Estnisch, Finnisch, Französisch, Deutsch, Griechisch, Hebräisch, Hindi, Ungarisch, Indonesisch, Italienisch, Japanisch, Koreanisch, Litauisch, Malaiisch, Marathi, Nepalesisch, Norwegisch, Persisch, Polnisch, Portugiesisch, Punjabi, Rumänisch, Russisch, Serbisch, Slowakisch, Slowenisch, Spanisch, Suaheli, Schwedisch, Tagalog, Tamil, Thai, Türkisch, Ukrainisch, Urdu, Vietnamesisch und mehr.

**Bearbeiten Sie Übersetzungsdateien NICHT manuell** - sie werden vom automatisierten Workflow überschrieben.

## Richtlinien für Code-Stil

### Markdown-Konventionen

- Verwenden Sie standardmäßige Markdown-Syntax
- Überschriften: Verwenden Sie `#` für den Haupttitel, `##` für Abschnitte, `###` für Unterabschnitte
- Listen: Verwenden Sie `-` oder `*` für ungeordnete Listen, `1.` für geordnete Listen
- Links: Verwenden Sie beschreibenden Text mit vollständigen GitHub-URLs für Querverweise
- Bilder: Speichern Sie diese im Verzeichnis `/images/`, verwenden Sie beschreibenden Alt-Text
- Codeblöcke: Verwenden Sie dreifache Backticks mit Sprachkennzeichnung, wenn zutreffend

### Inhaltsrichtlinien

- Halten Sie die Lektionen fokussiert und prägnant (30-60 Minuten Lesezeit)
- Verwenden Sie klare, anfängerfreundliche Sprache
- Vermeiden Sie Anweisungen zu herstellerspezifischen Tools (Curriculum ist herstellerunabhängig)
- Fügen Sie Lernziele zu Beginn jedes Moduls hinzu
- Verlinken Sie bei Bedarf externe Microsoft Learn-Ressourcen
- Stellen Sie sicher, dass die Inhalte lehrreich und nicht werblich sind

### Dateibenennung

- Verwenden Sie das Format: `[Module].[Lesson] [Title].md`
- Beispiel: `1.1 The CIA triad and other key concepts.md`
- Quiz-Dateien: `[Module].[Last] End of module quiz.md`
- Verwenden Sie Leerzeichen in Dateinamen (bestehende Konvention)

## GitHub-Workflows

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push in den `main`-Branch  
**Zweck:** Übersetzt neue/geänderte Markdown-Dateien automatisch in über 50 Sprachen

**Erforderliche Umgebungsvariablen:**
- Azure AI Service-Zugangsdaten (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI-Zugangsdaten (optionale Alternative)
- OpenAI-Zugangsdaten (optionale Alternative)

### Deploy (deploy.yaml)

**Trigger:** Push in den `main`-Branch, wenn README.md geändert wird  
**Zweck:** Stellt die statische Website auf GitHub Pages bereit  
**Ausgabe:** Aktualisiert die GitHub Pages-Website

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push in den konfigurierten Branch  
**Zweck:** Baut und stellt die Website mit Jekyll bereit

## Richtlinien für Pull Requests

### Vor dem Einreichen

1. **Inhaltsprüfung:** Stellen Sie die Genauigkeit und Klarheit der Cybersecurity-Konzepte sicher
2. **Formatierung:** Überprüfen Sie, ob die Markdown-Formatierung korrekt gerendert wird
3. **Links:** Testen Sie alle internen und externen Links
4. **Bilder:** Stellen Sie sicher, dass alle Bilder geladen werden und beschreibenden Alt-Text haben
5. **Konsistenz:** Befolgen Sie die bestehende Inhaltsstruktur und den Stil

### Format für PR-Titel

Verwenden Sie beschreibende Titel:
- `Add: [Neue Inhaltsbeschreibung]`
- `Update: [Modul/Lektion] - [Kurze Beschreibung]`
- `Fix: [Problembeschreibung]`
- `Docs: [Dokumentationsänderungen]`

### Erforderliche Prüfungen

- Inhaltliche Genauigkeit (manuelle Prüfung)
- Validierung der Markdown-Formatierung
- Linkprüfung
- Abschluss des Übersetzungsworkflows (für `main`-Branch-Merges)

### Überprüfungsprozess

1. Mindestens eine Überprüfung durch einen Maintainer erforderlich
2. Fokus auf technische Genauigkeit der Sicherheitskonzepte
3. Überprüfung der Barrierefreiheit und Anfängerfreundlichkeit
4. Sicherstellen, dass die Herstellerneutralität gewahrt bleibt

## Häufige Aufgaben

### Hinzufügen einer neuen Lektion

```bash
# 1. Create new Markdown file with proper naming
touch "[Module].[Lesson] [Title].md"

# 2. Add content following template structure
# 3. Update README.md module table with new entry
# 4. Add entry to module overview table
# 5. Ensure quiz file numbering is correct

# 6. Commit changes
git add "[Module].[Lesson] [Title].md" README.md
git commit -m "Add: [Module].[Lesson] - [Title]"
git push
```

### Aktualisieren bestehender Inhalte

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Hinzufügen von Bildern

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.de.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Tests und Validierung

### Inhaltsvalidierung

Da dies ein Dokumentationsprojekt ist, konzentrieren sich die Tests auf:

1. **Markdown-Darstellung:** Änderungen lokal mit Docsify anzeigen
2. **Linkvalidierung:** Alle Links manuell anklicken
3. **Bildanzeige:** Überprüfen, ob alle Bilder korrekt angezeigt werden
4. **Übersetzung:** Überprüfen, ob Dateien vom Übersetzungsworkflow erfasst werden (automatisiert)
5. **Barrierefreiheit:** Sicherstellen einer korrekten Überschriftenhierarchie und Alt-Text

### Lokale Vorschau

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Pre-Commit-Checkliste

- [ ] Markdown-Dateien verwenden die korrekte Syntax
- [ ] Alle Links sind gültig und verwenden nach Möglichkeit HTTPS
- [ ] Bilder haben beschreibenden Alt-Text
- [ ] Inhalte sind anfängerfreundlich und korrekt
- [ ] Herstellerneutrale Sprache wird beibehalten
- [ ] README.md wird aktualisiert, wenn Module hinzugefügt oder entfernt werden
- [ ] Dateibenennung folgt den Konventionen

## Sicherheitsüberlegungen

- **Keine Geheimnisse in Inhalten:** Niemals API-Schlüssel, Passwörter oder sensible Daten committen
- **Linkvalidierung:** Sicherstellen, dass alle externen Links vertrauenswürdige Quellen sind
- **Bildinhalte:** Überprüfen, dass Bilder keine sensiblen Informationen enthalten
- **Übersetzungsworkflow:** Verwendet Azure AI-Dienste mit ordnungsgemäßer Authentifizierung
- **SECURITY.md:** Befolgen Sie den Prozess zur Meldung von Schwachstellen in SECURITY.md

## Zusätzliche Ressourcen

### Verwandte Microsoft-Kurse

Dieses Curriculum ist Teil einer größeren Sammlung von Microsoft-Bildungsressourcen:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Externe Lernpfade

Nach Abschluss von Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Beitrag leisten

1. **Forken Sie das Repository** auf GitHub
2. **Erstellen Sie einen Feature-Branch** für Ihre Änderungen
3. **Nehmen Sie Ihre Änderungen vor** gemäß den oben genannten Richtlinien
4. **Testen Sie lokal**, um sicherzustellen, dass alles korrekt gerendert wird
5. **Reichen Sie einen Pull Request ein** mit einer klaren Beschreibung der Änderungen
6. **Reagieren Sie auf Feedback** von Maintainers

## Häufige Probleme und Fehlerbehebung

### Übersetzungen funktionieren nicht

- Stellen Sie sicher, dass Änderungen in den `main`-Branch gepusht wurden
- Überprüfen Sie den GitHub Actions-Tab auf den Workflow-Status
- Verifizieren Sie, dass die Geheimnisse des Übersetzungsworkflows konfiguriert sind
- Übersetzungen erfolgen automatisch; bearbeiten Sie Übersetzungsdateien nicht manuell

### Bilder werden nicht geladen

- Überprüfen Sie, ob der Bildpfad Vorwärtsschrägstriche verwendet: `images/filename.png`
- Stellen Sie sicher, dass die Bilddatei im Repository committed wurde
- Überprüfen Sie, ob der Bilddateiname exakt übereinstimmt (Groß-/Kleinschreibung beachten)
- Verwenden Sie relative Pfade, keine absoluten URLs

### Docsify rendert nicht

- Überprüfen Sie, ob `index.html` im Stammverzeichnis vorhanden ist
- Verifizieren Sie, dass die Docsify-CDN-Links zugänglich sind
- Stellen Sie sicher, dass Markdown-Dateien die Standardsyntax verwenden
- Überprüfen Sie die Browserkonsole auf JavaScript-Fehler

### Links funktionieren nicht

- Verwenden Sie vollständige GitHub-URLs für Querverweise zwischen Lektionen
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testen Sie Links in der gerenderten Ansicht, nicht nur im rohen Markdown

## Projektwartung

### Regelmäßige Aufgaben

- Überprüfen und zusammenführen von Beiträgen aus der Community
- Aktualisieren von Inhalten, um die Genauigkeit angesichts der sich entwickelnden Sicherheitslandschaft zu gewährleisten
- Überwachen des Übersetzungsworkflows auf Fehler
- Reagieren auf Probleme und Diskussionen
- Externe Links aktuell halten

### Versionskontrolle

- Der `main`-Branch ist geschützt und erfordert PR-Überprüfungen
- Alle Änderungen durchlaufen den Pull-Request-Prozess
- Übersetzungsdateien werden automatisch generiert, nicht manuell bearbeiten
- Verwenden Sie aussagekräftige Commit-Nachrichten

## Hinweise für KI-Coding-Agenten

- **Dies ist ein Dokumentationsprojekt** - Fokus auf Inhaltsqualität, nicht auf Code
- **Übersetzungsdateien nicht ändern** - sie werden automatisch generiert
- **Dateibenennungskonventionen beibehalten** - verwenden Sie Leerzeichen in Dateinamen gemäß bestehendem Muster
- **README.md aktualisieren**, wenn Module hinzugefügt oder entfernt werden, um die Tabelle synchron zu halten
- **Lokal testen**, bevor PRs eingereicht werden, um sicherzustellen, dass Markdown korrekt gerendert wird
- **Bestehenden Inhaltsstil beibehalten** - anfängerfreundlichen, herstellerneutralen Ton wahren
- **Kein Build-Prozess erforderlich** - einfacher HTTP-Server reicht für die lokale Entwicklung aus
- **Modulstruktur respektieren** - jedes Modul hat eine konsistente Nummerierung und Organisation

---

**Haftungsausschluss**:  
Dieses Dokument wurde mit dem KI-Übersetzungsdienst [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, beachten Sie bitte, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in seiner ursprünglichen Sprache sollte als maßgebliche Quelle betrachtet werden. Für kritische Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die sich aus der Nutzung dieser Übersetzung ergeben.