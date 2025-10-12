<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:39:15+00:00",
  "source_file": "AGENTS.md",
  "language_code": "nl"
}
-->
# AGENTS.md

## Projectoverzicht

**Security-101** is een gebruiksvriendelijke cybersecurity-cursus ontwikkeld door Microsoft. Het project is een documentatiegebaseerde leerbron die fundamentele cybersecurityconcepten leert via gestructureerde modules. Het is onafhankelijk van leveranciers en ontworpen om in kleine lessen (30-60 minuten per les) te worden voltooid.

**Belangrijke technologieën:**
- Markdown voor inhoud
- Docsify voor statische sitegeneratie
- GitHub Pages voor hosting
- Co-op Translator voor meertalige ondersteuning (50+ talen)
- GitHub Actions voor CI/CD

**Architectuur:**
- Educatieve inhoud georganiseerd in 8 hoofdmodules, elk met sublessen
- Statische HTML-site met Docsify die Markdown-inhoud weergeeft
- Geautomatiseerde vertaalworkflow met behulp van Azure AI-services
- Geen buildtools of pakketmanagers nodig voor kerninhoud

## Repositorystructuur

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

## Setupcommando's

Dit is een documentatieproject zonder vereiste afhankelijkheden om te installeren. Om met de inhoud te werken:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Ontwikkelingsworkflow

### Inhoud lokaal bekijken

Het project gebruikt Docsify voor weergave. Om wijzigingen te bekijken:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Inhoudsstructuur

Modules zijn opeenvolgend genummerd:
- **Module 1:** Basisconcepten van beveiliging (1.1-1.7)
- **Module 2:** Identiteits- en toegangsbeheer (2.1-2.4)
- **Module 3:** Netwerkbeveiliging (3.1-3.4)
- **Module 4:** Beveiligingsoperaties (4.1-4.4)
- **Module 5:** Applicatiebeveiliging (5.1-5.3)
- **Module 6:** Infrastructuurbeveiliging (6.1-6.3)
- **Module 7:** Gegevensbeveiliging (7.1-7.3)
- **Module 8:** AI-beveiliging (8.1-8.4)

Elke module eindigt met een quizbestand (bijv. "1.7 End of module quiz.md").

### Inhoud wijzigen

1. Bewerk Markdown-bestanden direct in de hoofdmap
2. Volg de bestaande naamgevingsconventie: `[module].[les] [Titel].md`
3. Werk de tabel in README.md bij als je modules toevoegt/verwijdert
4. Voeg afbeeldingen toe aan de map `/images/`
5. Verwijs naar afbeeldingen met relatieve paden: `![Beschrijving](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.nl.png)`

## Vertaalworkflow

**Geautomatiseerde vertaling:**
- Vertalingen worden automatisch afgehandeld door de Co-op Translator GitHub Action
- Wanneer je wijzigingen naar de `main`-branch pusht, vertaalt de workflow inhoud naar 50+ talen
- Vertaalde bestanden worden opgeslagen in `/translations/[language_code]/`
- Metadata van vertalingen wordt behouden in YAML-frontmatter

**Ondersteunde talen:** Arabisch, Bengaals, Bulgaars, Birmees, Chinees (vereenvoudigd, traditioneel), Kroatisch, Tsjechisch, Deens, Nederlands, Ests, Fins, Frans, Duits, Grieks, Hebreeuws, Hindi, Hongaars, Indonesisch, Italiaans, Japans, Koreaans, Litouws, Maleis, Marathi, Nepalees, Noors, Perzisch, Pools, Portugees, Punjabi, Roemeens, Russisch, Servisch, Slowaaks, Sloveens, Spaans, Swahili, Zweeds, Tagalog, Tamil, Thais, Turks, Oekraïens, Urdu, Vietnamees en meer.

**Bewerk vertaalbestanden NIET handmatig** - ze worden overschreven door de geautomatiseerde workflow.

## Richtlijnen voor codestijl

### Markdown-conventies

- Gebruik standaard Markdown-syntaxis
- Koppen: Gebruik `#` voor hoofdtitel, `##` voor secties, `###` voor subsecties
- Lijsten: Gebruik `-` of `*` voor ongenummerde lijsten, `1.` voor genummerde lijsten
- Links: Gebruik beschrijvende tekst met volledige GitHub-URL's voor kruisverwijzingen
- Afbeeldingen: Opslaan in de map `/images/`, gebruik beschrijvende alt-tekst
- Codeblokken: Gebruik drie backticks met taalidentificatie indien van toepassing

### Richtlijnen voor inhoud

- Houd lessen gefocust en beknopt (30-60 minuten leestijd)
- Gebruik duidelijke, gebruiksvriendelijke taal
- Vermijd instructies voor leveranciersspecifieke tools (curriculum is onafhankelijk van leveranciers)
- Voeg leerdoelen toe aan het begin van elke module
- Link naar externe Microsoft Learn-bronnen waar relevant
- Zorg ervoor dat de inhoud educatief is, niet promotioneel

### Naamgeving van bestanden

- Gebruik het formaat: `[Module].[Les] [Titel].md`
- Voorbeeld: `1.1 The CIA triad and other key concepts.md`
- Quizbestanden: `[Module].[Last] End of module quiz.md`
- Gebruik spaties in bestandsnamen (bestaande conventie)

## GitHub-workflows

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push naar `main`-branch  
**Doel:** Vertaalt nieuwe/aangepaste Markdown-bestanden automatisch naar 50+ talen

**Vereiste omgevingsvariabelen:**
- Azure AI Service-credentials (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI-credentials (optioneel alternatief)
- OpenAI-credentials (optioneel alternatief)

### Deploy (deploy.yaml)

**Trigger:** Push naar `main`-branch wanneer README.md verandert  
**Doel:** Publiceert statische site naar GitHub Pages  
**Output:** Update GitHub Pages-site

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push naar geconfigureerde branch  
**Doel:** Bouwt en publiceert site met Jekyll

## Richtlijnen voor pull requests

### Voordat je indient

1. **Inhoudscontrole:** Zorg voor nauwkeurigheid en duidelijkheid van cybersecurityconcepten
2. **Opmaak:** Controleer of Markdown-opmaak correct wordt weergegeven
3. **Links:** Test alle interne en externe links
4. **Afbeeldingen:** Zorg ervoor dat alle afbeeldingen laden en beschrijvende alt-tekst hebben
5. **Consistentie:** Volg de bestaande inhoudsstructuur en stijl

### Formaat van PR-titels

Gebruik beschrijvende titels:
- `Add: [Beschrijving nieuwe inhoud]`
- `Update: [Module/Les] - [Korte beschrijving]`
- `Fix: [Beschrijving probleem]`
- `Docs: [Wijzigingen in documentatie]`

### Vereiste controles

- Nauwkeurigheid van inhoud (handmatige controle)
- Validatie van Markdown-opmaak
- Linkverificatie
- Voltooiing van vertaalworkflow (voor merges naar `main`-branch)

### Reviewproces

1. Minimaal één review door een maintainer vereist
2. Focus op technische nauwkeurigheid van beveiligingsconcepten
3. Controleer toegankelijkheid en gebruiksvriendelijkheid
4. Zorg ervoor dat neutraliteit ten opzichte van leveranciers wordt gehandhaafd

## Veelvoorkomende taken

### Een nieuwe les toevoegen

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

### Bestaande inhoud bijwerken

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Afbeeldingen toevoegen

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.nl.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testen en validatie

### Validatie van inhoud

Aangezien dit een documentatieproject is, richt testen zich op:

1. **Markdown-weergave:** Bekijk wijzigingen lokaal met Docsify
2. **Linkvalidatie:** Klik handmatig op alle links
3. **Afbeeldingen laden:** Controleer of alle afbeeldingen correct worden weergegeven
4. **Vertaling:** Controleer of bestanden worden opgepikt door de vertaalworkflow (geautomatiseerd)
5. **Toegankelijkheid:** Zorg voor een juiste koppenhiërarchie en alt-tekst

### Lokale preview

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Checklist vóór commit

- [ ] Markdown-bestanden gebruiken correcte syntaxis
- [ ] Alle links zijn geldig en gebruiken HTTPS waar mogelijk
- [ ] Afbeeldingen hebben beschrijvende alt-tekst
- [ ] Inhoud is gebruiksvriendelijk en nauwkeurig
- [ ] Neutraliteit ten opzichte van leveranciers wordt gehandhaafd
- [ ] README.md bijgewerkt bij het toevoegen/verwijderen van modules
- [ ] Bestandsnamen volgen conventies

## Beveiligingsoverwegingen

- **Geen geheimen in inhoud:** Commit nooit API-sleutels, wachtwoorden of gevoelige gegevens
- **Linkvalidatie:** Zorg ervoor dat alle externe links naar betrouwbare bronnen gaan
- **Afbeeldingsinhoud:** Controleer of afbeeldingen geen gevoelige informatie bevatten
- **Vertaalworkflow:** Gebruikt Azure AI-services met juiste authenticatie
- **SECURITY.md:** Volg het proces voor het melden van kwetsbaarheden in SECURITY.md

## Aanvullende bronnen

### Gerelateerde Microsoft-cursussen

Dit curriculum maakt deel uit van een grotere verzameling Microsoft-educatieve bronnen:
- Generatieve AI voor beginners
- AI voor beginners
- Data Science voor beginners
- ML voor beginners
- Webontwikkeling voor beginners
- IoT voor beginners

### Externe leerpaden

Na voltooiing van Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Bijdragen

1. **Fork de repository** op GitHub
2. **Maak een feature branch** voor je wijzigingen
3. **Voer je wijzigingen door** volgens de bovenstaande richtlijnen
4. **Test lokaal** om ervoor te zorgen dat alles correct wordt weergegeven
5. **Dien een pull request in** met een duidelijke beschrijving van de wijzigingen
6. **Reageer op feedback** van maintainers

## Veelvoorkomende problemen en oplossingen

### Vertalingen werken niet

- Zorg ervoor dat wijzigingen naar de `main`-branch zijn gepusht
- Controleer de GitHub Actions-tab voor workflowstatus
- Verifieer dat secrets voor de vertaalworkflow correct zijn geconfigureerd
- Vertaling gebeurt automatisch; bewerk vertaalbestanden niet handmatig

### Afbeeldingen laden niet

- Controleer of het afbeeldingspad forward slashes gebruikt: `images/filename.png`
- Controleer of het afbeeldingsbestand is gecommit naar de repository
- Zorg ervoor dat de bestandsnaam exact overeenkomt (hoofdlettergevoelig)
- Gebruik relatieve paden, geen absolute URL's

### Docsify wordt niet weergegeven

- Controleer of `index.html` aanwezig is in de hoofdmap
- Verifieer dat Docsify CDN-links toegankelijk zijn
- Zorg ervoor dat Markdown-bestanden standaard syntaxis gebruiken
- Controleer de browserconsole op JavaScript-fouten

### Links werken niet

- Gebruik volledige GitHub-URL's voor kruisverwijzingen tussen lessen
- Formaat: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Test links in de weergegeven weergave, niet alleen in ruwe Markdown

## Projectonderhoud

### Regelmatige taken

- Beoordelen en samenvoegen van bijdragen uit de community
- Inhoud bijwerken voor nauwkeurigheid naarmate het beveiligingslandschap evolueert
- Vertaalworkflow monitoren op fouten
- Reageren op issues en discussies
- Externe links up-to-date houden

### Versiebeheer

- `main`-branch is beschermd en vereist PR-reviews
- Alle wijzigingen gaan via het pull request-proces
- Vertaalbestanden worden automatisch gegenereerd, bewerk ze niet handmatig
- Gebruik betekenisvolle commitberichten

## Notities voor AI-coderingsagents

- **Dit is een documentatieproject** - focus op inhoudskwaliteit, niet op code
- **Bewerk vertaalbestanden niet** - ze worden automatisch gegenereerd
- **Behoud naamgevingsconventies** - gebruik spaties in bestandsnamen volgens het bestaande patroon
- **Update README.md** bij het toevoegen/verwijderen van modules om de tabel synchroon te houden
- **Test lokaal** voordat je PR's indient om ervoor te zorgen dat Markdown correct wordt weergegeven
- **Volg de bestaande inhoudsstijl** - behoud een gebruiksvriendelijke, neutrale toon
- **Geen buildproces vereist** - een eenvoudige HTTP-server is voldoende voor lokale ontwikkeling
- **Respecteer de modulestructuur** - elke module heeft een consistente nummering en organisatie

---

**Disclaimer**:  
Dit document is vertaald met behulp van de AI-vertalingsservice [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel we streven naar nauwkeurigheid, dient u zich ervan bewust te zijn dat geautomatiseerde vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het originele document in de oorspronkelijke taal moet worden beschouwd als de gezaghebbende bron. Voor cruciale informatie wordt professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.