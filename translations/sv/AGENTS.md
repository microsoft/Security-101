<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:37:16+00:00",
  "source_file": "AGENTS.md",
  "language_code": "sv"
}
-->
# AGENTS.md

## Projektöversikt

**Security-101** är en nybörjarvänlig cybersäkerhetskurs skapad av Microsoft. Projektet är en dokumentationsbaserad inlärningsresurs som lär ut grundläggande koncept inom cybersäkerhet genom strukturerade moduler. Det är leverantörsneutralt och utformat för att kunna genomföras i små lektioner (30-60 minuter vardera).

**Nyckelteknologier:**
- Markdown för innehåll
- Docsify för statisk webbplatsgenerering
- GitHub Pages för hosting
- Co-op Translator för flerspråkigt stöd (50+ språk)
- GitHub Actions för CI/CD

**Arkitektur:**
- Utbildningsinnehåll organiserat i 8 huvudmoduler, var och en med underlektioner
- Statisk HTML-webbplats med Docsify som renderar Markdown-innehåll
- Automatiserat översättningsflöde med hjälp av Azure AI-tjänster
- Inga byggverktyg eller paketchefer krävs för kärninnehållet

## Repositoriets struktur

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

## Installationskommandon

Detta är ett dokumentationsprojekt utan några beroenden att installera. För att arbeta med innehållet:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Utvecklingsflöde

### Visa innehåll lokalt

Projektet använder Docsify för rendering. För att förhandsgranska ändringar:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Innehållsstruktur

Modulerna är numrerade i följd:
- **Modul 1:** Grundläggande säkerhetskoncept (1.1-1.7)
- **Modul 2:** Identitet & åtkomsthantering (2.1-2.4)
- **Modul 3:** Nätverkssäkerhet (3.1-3.4)
- **Modul 4:** Säkerhetsoperationer (4.1-4.4)
- **Modul 5:** Applikationssäkerhet (5.1-5.3)
- **Modul 6:** Infrastruktursäkerhet (6.1-6.3)
- **Modul 7:** Datasäkerhet (7.1-7.3)
- **Modul 8:** AI-säkerhet (8.1-8.4)

Varje modul avslutas med en frågesportsfil (t.ex. "1.7 End of module quiz.md").

### Göra ändringar i innehållet

1. Redigera Markdown-filer direkt i rotkatalogen
2. Följ den befintliga namngivningskonventionen: `[modul].[lektion] [Titel].md`
3. Uppdatera README.md-tabellen om du lägger till/ta bort moduler
4. Lägg till bilder i katalogen `/images/`
5. Referera till bilder med relativa sökvägar: `![Beskrivning](../../translated_images/filnamn.289be608bfaf2f33280cb4916b9af0f7c00b984884ce747a36d17384add90a4b.sv.png)`

## Översättningsflöde

**Automatiserad översättning:**
- Översättningar hanteras automatiskt av Co-op Translator GitHub Action
- När du pushar ändringar till `main`-grenen översätter arbetsflödet innehållet till 50+ språk
- Översatta filer lagras i `/translations/[language_code]/`
- Metadata för översättningar bevaras i YAML frontmatter

**Stödda språk:** Arabiska, Bengali, Bulgariska, Burmesiska, Kinesiska (förenklad, traditionell), Kroatiska, Tjeckiska, Danska, Nederländska, Estniska, Finska, Franska, Tyska, Grekiska, Hebreiska, Hindi, Ungerska, Indonesiska, Italienska, Japanska, Koreanska, Litauiska, Malajiska, Marathi, Nepalesiska, Norska, Persiska, Polska, Portugisiska, Punjabi, Rumänska, Ryska, Serbiska, Slovakiska, Slovenska, Spanska, Swahili, Svenska, Tagalog, Tamil, Thailändska, Turkiska, Ukrainska, Urdu, Vietnamesiska och fler.

**Redigera INTE översättningsfiler manuellt** - de kommer att skrivas över av det automatiserade arbetsflödet.

## Kodstilsguide

### Markdown-konventioner

- Använd standard Markdown-syntax
- Rubriker: Använd `#` för huvudrubrik, `##` för avsnitt, `###` för underrubriker
- Listor: Använd `-` eller `*` för oordnade listor, `1.` för ordnade listor
- Länkar: Använd beskrivande text med fullständiga GitHub-URL:er för korsreferenser
- Bilder: Spara i katalogen `/images/`, använd beskrivande alt-text
- Kodblock: Använd tre backticks med språkidentifierare när det är tillämpligt

### Innehållsriktlinjer

- Håll lektionerna fokuserade och koncisa (30-60 minuters lästid)
- Använd tydligt, nybörjarvänligt språk
- Undvik instruktioner för leverantörsspecifika verktyg (kursen är leverantörsneutral)
- Inkludera lärandemål i början av varje modul
- Länka till externa Microsoft Learn-resurser där det är lämpligt
- Säkerställ att innehållet är utbildande, inte marknadsförande

### Filnamngivning

- Använd formatet: `[Modul].[Lektion] [Titel].md`
- Exempel: `1.1 The CIA triad and other key concepts.md`
- Frågesportsfiler: `[Modul].[Sista] End of module quiz.md`
- Använd mellanslag i filnamn (enligt befintlig konvention)

## GitHub-arbetsflöden

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push till `main`-grenen  
**Syfte:** Översätter automatiskt nya/ändrade Markdown-filer till 50+ språk

**Nödvändiga miljövariabler:**
- Azure AI Service-uppgifter (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI-uppgifter (valfritt alternativ)
- OpenAI-uppgifter (valfritt alternativ)

### Deploy (deploy.yaml)

**Trigger:** Push till `main`-grenen när README.md ändras  
**Syfte:** Distribuerar statisk webbplats till GitHub Pages  
**Utdata:** Uppdaterar GitHub Pages-webbplatsen

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push till konfigurerad gren  
**Syfte:** Bygger och distribuerar webbplatsen med Jekyll

## Riktlinjer för pull requests

### Innan du skickar in

1. **Innehållsgranskning:** Säkerställ att cybersäkerhetskoncepten är korrekta och tydliga
2. **Formatering:** Kontrollera att Markdown-formateringen renderas korrekt
3. **Länkar:** Testa alla interna och externa länkar
4. **Bilder:** Säkerställ att alla bilder laddas och har beskrivande alt-text
5. **Konsekvens:** Följ den befintliga innehållsstrukturen och stilen

### PR-titelformat

Använd beskrivande titlar:
- `Add: [Beskrivning av nytt innehåll]`
- `Update: [Modul/Lektion] - [Kort beskrivning]`
- `Fix: [Beskrivning av problemet]`
- `Docs: [Dokumentationsändringar]`

### Obligatoriska kontroller

- Innehållskorrekthet (manuell granskning)
- Validering av Markdown-formatering
- Länkverifiering
- Slutförande av översättningsarbetsflöde (för `main`-grensammanslagningar)

### Granskningsprocess

1. Minst en granskning av en ansvarig krävs
2. Fokus på teknisk korrekthet av säkerhetskoncept
3. Verifiera tillgänglighet och nybörjarvänlighet
4. Säkerställ att leverantörsneutralitet upprätthålls

## Vanliga uppgifter

### Lägga till en ny lektion

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

### Uppdatera befintligt innehåll

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Lägga till bilder

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.sv.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testning och validering

### Validering av innehåll

Eftersom detta är ett dokumentationsprojekt fokuserar testningen på:

1. **Markdown-rendering:** Förhandsgranska ändringar lokalt med Docsify
2. **Länkvalidering:** Klicka manuellt igenom alla länkar
3. **Bildladdning:** Kontrollera att alla bilder visas korrekt
4. **Översättning:** Kontrollera att filer plockas upp av översättningsarbetsflödet (automatiserat)
5. **Tillgänglighet:** Säkerställ korrekt rubrikhierarki och alt-text

### Lokal förhandsgranskning

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Checklista före commit

- [ ] Markdown-filer använder korrekt syntax
- [ ] Alla länkar är giltiga och använder HTTPS där det är möjligt
- [ ] Bilder har beskrivande alt-text
- [ ] Innehållet är nybörjarvänligt och korrekt
- [ ] Leverantörsneutral språkbruk upprätthålls
- [ ] README.md uppdaterad om moduler läggs till/tas bort
- [ ] Filnamn följer konventioner

## Säkerhetsöverväganden

- **Inga hemligheter i innehållet:** Lämna aldrig in API-nycklar, lösenord eller känslig data
- **Länkvalidering:** Säkerställ att alla externa länkar går till pålitliga källor
- **Bildinnehåll:** Kontrollera att bilder inte innehåller känslig information
- **Översättningsarbetsflöde:** Använder Azure AI-tjänster med korrekt autentisering
- **SECURITY.md:** Följ processen för rapportering av sårbarheter i SECURITY.md

## Ytterligare resurser

### Relaterade Microsoft-kurser

Denna kurs är en del av en större samling av Microsofts utbildningsresurser:
- Generativ AI för nybörjare
- AI för nybörjare
- Data Science för nybörjare
- ML för nybörjare
- Webbutveckling för nybörjare
- IoT för nybörjare

### Externa utbildningsvägar

Efter att ha slutfört Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Bidra

1. **Gör en fork av repositoriet** på GitHub
2. **Skapa en feature branch** för dina ändringar
3. **Gör dina ändringar** enligt riktlinjerna ovan
4. **Testa lokalt** för att säkerställa att allt renderas korrekt
5. **Skicka in en pull request** med en tydlig beskrivning av ändringarna
6. **Svara på feedback** från ansvariga

## Vanliga problem och felsökning

### Översättningar fungerar inte

- Säkerställ att ändringar är pushade till `main`-grenen
- Kontrollera GitHub Actions-fliken för arbetsflödets status
- Verifiera att hemligheter för översättningsarbetsflödet är konfigurerade
- Översättning sker automatiskt; redigera inte översättningsfiler manuellt

### Bilder laddas inte

- Kontrollera att bildsökvägen använder snedstreck: `images/filnamn.png`
- Kontrollera att bildfilen är incheckad i repositoriet
- Säkerställ att bildfilens namn stämmer exakt (skiftlägeskänsligt)
- Använd relativa sökvägar, inte absoluta URL:er

### Docsify renderar inte

- Kontrollera att `index.html` finns i roten
- Verifiera att Docsify CDN-länkar är tillgängliga
- Säkerställ att Markdown-filer använder standardsyntax
- Kontrollera webbläsarens konsol för JavaScript-fel

### Länkar fungerar inte

- Använd fullständiga GitHub-URL:er för korsreferenser mellan lektioner
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testa länkar i renderad vy, inte bara i rå Markdown

## Projektunderhåll

### Regelbundna uppgifter

- Granska och slå samman bidrag från communityn
- Uppdatera innehåll för att säkerställa korrekthet när säkerhetslandskapet utvecklas
- Övervaka översättningsarbetsflödet för fel
- Svara på problem och diskussioner
- Håll externa länkar uppdaterade

### Versionskontroll

- `main`-grenen är skyddad och kräver PR-granskningar
- Alla ändringar går genom pull request-processen
- Översättningsfiler genereras automatiskt, redigera dem inte manuellt
- Använd meningsfulla commit-meddelanden

## Anteckningar för AI-kodningsagenter

- **Detta är ett dokumentationsprojekt** - fokusera på innehållskvalitet, inte kod
- **Ändra inte översättningsfiler** - de genereras automatiskt
- **Bevara filnamnskonventioner** - använd mellanslag i filnamn enligt befintligt mönster
- **Uppdatera README.md** när moduler läggs till/tas bort för att hålla tabellen synkroniserad
- **Testa lokalt** innan du skickar in PR för att säkerställa att Markdown renderas korrekt
- **Följ befintlig innehållsstil** - upprätthåll en nybörjarvänlig, leverantörsneutral ton
- **Ingen byggprocess krävs** - en enkel HTTP-server är tillräcklig för lokal utveckling
- **Respektera modulstrukturen** - varje modul har en konsekvent numrering och organisation

---

**Ansvarsfriskrivning**:  
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet, bör det noteras att automatiserade översättningar kan innehålla fel eller felaktigheter. Det ursprungliga dokumentet på dess originalspråk bör betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för eventuella missförstånd eller feltolkningar som uppstår vid användning av denna översättning.