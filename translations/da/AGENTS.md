<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:37:38+00:00",
  "source_file": "AGENTS.md",
  "language_code": "da"
}
-->
# AGENTS.md

## Projektoversigt

**Security-101** er et begyndervenligt cybersikkerhedsforløb skabt af Microsoft. Projektet er en dokumentationsbaseret læringsressource, der underviser i grundlæggende cybersikkerhedskoncepter gennem strukturerede moduler. Det er leverandøruafhængigt og designet til at kunne gennemføres i små lektioner (30-60 minutter hver).

**Nøgleteknologier:**
- Markdown til indhold
- Docsify til statisk sidegenerering
- GitHub Pages til hosting
- Co-op Translator til flersproget support (50+ sprog)
- GitHub Actions til CI/CD

**Arkitektur:**
- Uddannelsesindhold organiseret i 8 hovedmoduler, hver med underlektioner
- Statisk HTML-side med Docsify, der gengiver Markdown-indhold
- Automatiseret oversættelsesworkflow ved hjælp af Azure AI-tjenester
- Ingen build-værktøjer eller pakkehåndteringssystemer kræves for kerneindholdet

## Repository-struktur

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

## Opsætningskommandoer

Dette er et dokumentationsprojekt uden afhængigheder, der skal installeres. For at arbejde med indholdet:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Udviklingsworkflow

### Visning af indhold lokalt

Projektet bruger Docsify til gengivelse. For at forhåndsvise ændringer:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Indholdsstruktur

Modulerne er nummereret sekventielt:
- **Modul 1:** Grundlæggende sikkerhedskoncepter (1.1-1.7)
- **Modul 2:** Identitets- og adgangsstyring (2.1-2.4)
- **Modul 3:** Netværkssikkerhed (3.1-3.4)
- **Modul 4:** Sikkerhedsoperationer (4.1-4.4)
- **Modul 5:** Applikationssikkerhed (5.1-5.3)
- **Modul 6:** Infrastruktur-sikkerhed (6.1-6.3)
- **Modul 7:** Datasikkerhed (7.1-7.3)
- **Modul 8:** AI-sikkerhed (8.1-8.4)

Hvert modul afsluttes med en quiz-fil (f.eks. "1.7 End of module quiz.md").

### Ændring af indhold

1. Rediger Markdown-filer direkte i rodkataloget
2. Følg den eksisterende navngivningskonvention: `[module].[lesson] [Title].md`
3. Opdater README.md-tabellen, hvis du tilføjer/fjerner moduler
4. Tilføj billeder til `/images/`-kataloget
5. Referer til billeder ved hjælp af relative stier: `![Beskrivelse](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.da.png)`

## Oversættelsesworkflow

**Automatiseret oversættelse:**
- Oversættelser håndteres automatisk af Co-op Translator GitHub Action
- Når du skubber ændringer til `main`-grenen, oversætter workflowet indholdet til 50+ sprog
- Oversatte filer gemmes i `/translations/[language_code]/`
- Oversættelsesmetadata bevares i YAML frontmatter

**Understøttede sprog:** Arabisk, Bengali, Bulgarsk, Burmesisk, Kinesisk (forenklet, traditionelt), Kroatisk, Tjekkisk, Dansk, Hollandsk, Estisk, Finsk, Fransk, Tysk, Græsk, Hebraisk, Hindi, Ungarsk, Indonesisk, Italiensk, Japansk, Koreansk, Litauisk, Malaysisk, Marathi, Nepalesisk, Norsk, Persisk, Polsk, Portugisisk, Punjabi, Rumænsk, Russisk, Serbisk, Slovakisk, Slovensk, Spansk, Swahili, Svensk, Tagalog, Tamil, Thai, Tyrkisk, Ukrainsk, Urdu, Vietnamesisk og flere.

**Rediger IKKE oversættelsesfiler manuelt** - de vil blive overskrevet af det automatiserede workflow.

## Kodestil-retningslinjer

### Markdown-konventioner

- Brug standard Markdown-syntaks
- Overskrifter: Brug `#` til hovedtitel, `##` til sektioner, `###` til undersektioner
- Lister: Brug `-` eller `*` til uordnede lister, `1.` til ordnede lister
- Links: Brug beskrivende tekst med fulde GitHub-URL'er til krydshenvisninger
- Billeder: Gem i `/images/`-kataloget, brug beskrivende alt-tekst
- Kodeblokke: Brug tre backticks med sprogidentifikator, når det er relevant

### Indholdsretningslinjer

- Hold lektioner fokuserede og korte (30-60 minutters læsetid)
- Brug klart, begyndervenligt sprog
- Undgå instruktioner om leverandørspecifikke værktøjer (forløbet er leverandøruafhængigt)
- Inkluder læringsmål i starten af hvert modul
- Link til eksterne Microsoft Learn-ressourcer, hvor det er relevant
- Sørg for, at indholdet er uddannelsesmæssigt og ikke reklamepræget

### Filnavngivning

- Brug formatet: `[Module].[Lesson] [Title].md`
- Eksempel: `1.1 The CIA triad and other key concepts.md`
- Quiz-filer: `[Module].[Last] End of module quiz.md`
- Brug mellemrum i filnavne (eksisterende konvention)

## GitHub-workflows

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push til `main`-grenen  
**Formål:** Oversætter automatisk nye/modificerede Markdown-filer til 50+ sprog

**Påkrævede miljøvariabler:**
- Azure AI Service-legitimationsoplysninger (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI-legitimationsoplysninger (valgfrit alternativ)
- OpenAI-legitimationsoplysninger (valgfrit alternativ)

### Deploy (deploy.yaml)

**Trigger:** Push til `main`-grenen, når README.md ændres  
**Formål:** Udruller statisk side til GitHub Pages  
**Output:** Opdaterer GitHub Pages-side

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push til konfigureret gren  
**Formål:** Bygger og udruller side ved hjælp af Jekyll

## Retningslinjer for pull requests

### Før indsendelse

1. **Indholdsrevision:** Sørg for nøjagtighed og klarhed i cybersikkerhedskoncepterne
2. **Formatering:** Bekræft, at Markdown-formateringen gengives korrekt
3. **Links:** Test alle interne og eksterne links
4. **Billeder:** Sørg for, at alle billeder indlæses og har beskrivende alt-tekst
5. **Konsistens:** Følg den eksisterende indholdsstruktur og stil

### PR-titelformat

Brug beskrivende titler:
- `Add: [Beskrivelse af nyt indhold]`
- `Update: [Modul/Lektion] - [Kort beskrivelse]`
- `Fix: [Beskrivelse af problem]`
- `Docs: [Ændringer i dokumentation]`

### Påkrævede kontrolpunkter

- Indholdsnøjagtighed (manuel revision)
- Markdown-formateringsvalidering
- Linkverifikation
- Oversættelsesworkflow fuldført (for merges til `main`-grenen)

### Review-proces

1. Mindst én vedligeholderanmeldelse kræves
2. Fokus på teknisk nøjagtighed af sikkerhedskoncepter
3. Bekræft tilgængelighed og begyndervenlighed
4. Sørg for, at leverandøruafhængighed opretholdes

## Almindelige opgaver

### Tilføjelse af en ny lektion

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

### Opdatering af eksisterende indhold

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Tilføjelse af billeder

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.da.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Test og validering

### Indholdsvalidering

Da dette er et dokumentationsprojekt, fokuserer test på:

1. **Markdown-gengivelse:** Se ændringer lokalt ved hjælp af Docsify
2. **Linkvalidering:** Klik manuelt på alle links
3. **Billedindlæsning:** Bekræft, at alle billeder vises korrekt
4. **Oversættelse:** Kontroller, at filer opfanges af oversættelsesworkflowet (automatisk)
5. **Tilgængelighed:** Sørg for korrekt overskrifthierarki og alt-tekst

### Lokal forhåndsvisning

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Tjekliste før commit

- [ ] Markdown-filer bruger korrekt syntaks
- [ ] Alle links er gyldige og bruger HTTPS, hvor det er muligt
- [ ] Billeder har beskrivende alt-tekst
- [ ] Indholdet er begyndervenligt og nøjagtigt
- [ ] Leverandøruafhængigt sprog opretholdes
- [ ] README.md opdateret, hvis moduler tilføjes/fjernes
- [ ] Filnavngivning følger konventioner

## Sikkerhedsovervejelser

- **Ingen hemmeligheder i indhold:** Commit aldrig API-nøgler, adgangskoder eller følsomme data
- **Linkvalidering:** Sørg for, at alle eksterne links fører til betroede kilder
- **Billedindhold:** Bekræft, at billeder ikke indeholder følsomme oplysninger
- **Oversættelsesworkflow:** Bruger Azure AI-tjenester med korrekt autentificering
- **SECURITY.md:** Følg processen for rapportering af sårbarheder i SECURITY.md

## Yderligere ressourcer

### Relaterede Microsoft-kurser

Dette forløb er en del af en større samling af Microsofts uddannelsesressourcer:
- Generativ AI for begyndere
- AI for begyndere
- Data Science for begyndere
- ML for begyndere
- Webudvikling for begyndere
- IoT for begyndere

### Eksterne læringsforløb

Efter afslutning af Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Eksamen SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Bidrag

1. **Fork repositoryet** på GitHub
2. **Opret en feature branch** til dine ændringer
3. **Foretag dine ændringer** i henhold til ovenstående retningslinjer
4. **Test lokalt** for at sikre, at alt gengives korrekt
5. **Indsend en pull request** med en klar beskrivelse af ændringerne
6. **Svar på feedback** fra vedligeholdere

## Almindelige problemer og fejlfinding

### Oversættelser fungerer ikke

- Sørg for, at ændringer er skubbet til `main`-grenen
- Tjek GitHub Actions-fanen for workflowstatus
- Bekræft, at oversættelsesworkflowets hemmeligheder er konfigureret
- Oversættelse sker automatisk; rediger ikke oversættelsesfiler manuelt

### Billeder indlæses ikke

- Bekræft, at billedstien bruger skråstreger: `images/filename.png`
- Tjek, at billedfilen er committed til repositoryet
- Sørg for, at billedfilnavnet matcher præcist (case-sensitive)
- Brug relative stier, ikke absolutte URL'er

### Docsify gengiver ikke

- Tjek, at `index.html` er til stede i roden
- Bekræft, at Docsify CDN-links er tilgængelige
- Sørg for, at Markdown-filer bruger standard syntaks
- Tjek browserkonsollen for JavaScript-fejl

### Links fungerer ikke

- Brug fulde GitHub-URL'er til krydshenvisninger mellem lektioner
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Test links i den gengivne visning, ikke kun i rå Markdown

## Projektvedligeholdelse

### Regelmæssige opgaver

- Gennemgå og merge bidrag fra fællesskabet
- Opdater indhold for nøjagtighed, efterhånden som sikkerhedslandskabet udvikler sig
- Overvåg oversættelsesworkflow for fejl
- Besvar problemer og diskussioner
- Hold eksterne links opdaterede

### Versionskontrol

- `main`-grenen er beskyttet og kræver PR-reviews
- Alle ændringer går gennem pull request-processen
- Oversættelsesfiler genereres automatisk, rediger ikke manuelt
- Brug meningsfulde commit-beskeder

## Noter til AI-kodningsagenter

- **Dette er et dokumentationsprojekt** - fokusér på indholdskvalitet, ikke kode
- **Rediger ikke oversættelsesfiler** - de genereres automatisk
- **Bevar filnavngivningskonventioner** - brug mellemrum i filnavne i henhold til eksisterende mønster
- **Opdater README.md** ved tilføjelse/fjernelse af moduler for at holde tabellen synkroniseret
- **Test lokalt** før indsendelse af PR'er for at sikre, at Markdown gengives korrekt
- **Følg eksisterende indholdsstil** - oprethold begyndervenlig, leverandøruafhængig tone
- **Ingen build-proces kræves** - en simpel HTTP-server er tilstrækkelig til lokal udvikling
- **Respektér modulstrukturen** - hvert modul har konsekvent nummerering og organisering

---

**Ansvarsfraskrivelse**:  
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, skal det bemærkes, at automatiserede oversættelser kan indeholde fejl eller unøjagtigheder. Det originale dokument på dets oprindelige sprog bør betragtes som den autoritative kilde. For kritisk information anbefales professionel menneskelig oversættelse. Vi påtager os intet ansvar for misforståelser eller fejltolkninger, der måtte opstå som følge af brugen af denne oversættelse.