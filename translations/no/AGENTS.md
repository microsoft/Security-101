<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:38:09+00:00",
  "source_file": "AGENTS.md",
  "language_code": "no"
}
-->
# AGENTS.md

## Prosjektoversikt

**Security-101** er et nybegynnervennlig cybersikkerhetskurs utviklet av Microsoft. Prosjektet er en dokumentasjonsbasert læringsressurs som lærer bort grunnleggende konsepter innen cybersikkerhet gjennom strukturerte moduler. Det er leverandøruavhengig og designet for å fullføres i små leksjoner (30-60 minutter hver).

**Nøkkelteknologier:**
- Markdown for innhold
- Docsify for generering av statiske nettsider
- GitHub Pages for hosting
- Co-op Translator for flerspråklig støtte (50+ språk)
- GitHub Actions for CI/CD

**Arkitektur:**
- Utdanningsinnhold organisert i 8 hovedmoduler, hver med underleksjoner
- Statisk HTML-nettside med Docsify som rendrer Markdown-innhold
- Automatisert oversettelsesarbeidsflyt ved bruk av Azure AI-tjenester
- Ingen byggeverktøy eller pakkebehandlere nødvendig for kjerneinnholdet

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

## Oppsettskommandoer

Dette er et dokumentasjonsprosjekt uten avhengigheter som må installeres. For å arbeide med innholdet:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Utviklingsarbeidsflyt

### Vise innhold lokalt

Prosjektet bruker Docsify for rendering. For å forhåndsvise endringer:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Innholdsstruktur

Modulene er nummerert sekvensielt:
- **Modul 1:** Grunnleggende sikkerhetskonsepter (1.1-1.7)
- **Modul 2:** Identitet og tilgangsstyring (2.1-2.4)
- **Modul 3:** Nettverkssikkerhet (3.1-3.4)
- **Modul 4:** Sikkerhetsoperasjoner (4.1-4.4)
- **Modul 5:** Applikasjonssikkerhet (5.1-5.3)
- **Modul 6:** Infrastruktur-sikkerhet (6.1-6.3)
- **Modul 7:** Datasikkerhet (7.1-7.3)
- **Modul 8:** AI-sikkerhet (8.1-8.4)

Hver modul avsluttes med en quiz-fil (f.eks. "1.7 End of module quiz.md").

### Gjøre endringer i innholdet

1. Rediger Markdown-filer direkte i rotkatalogen
2. Følg eksisterende navnekonvensjon: `[modul].[leksjon] [Tittel].md`
3. Oppdater README.md-tabellen hvis du legger til eller fjerner moduler
4. Legg til bilder i `/images/`-katalogen
5. Referer til bilder ved bruk av relative stier: `![Beskrivelse](../../translated_images/filnavn.a88f13e64354600a56548903c2a0c9f6f38c524178362e17b999b654c81fbbad.no.png)`

## Oversettelsesarbeidsflyt

**Automatisk oversettelse:**
- Oversettelser håndteres automatisk av Co-op Translator GitHub Action
- Når du pusher endringer til `main`-grenen, oversetter arbeidsflyten innholdet til 50+ språk
- Oversatte filer lagres i `/translations/[language_code]/`
- Metadata for oversettelser bevares i YAML frontmatter

**Støttede språk:** Arabisk, Bengali, Bulgarsk, Burmesisk, Kinesisk (forenklet, tradisjonell), Kroatisk, Tsjekkisk, Dansk, Nederlandsk, Estisk, Finsk, Fransk, Tysk, Gresk, Hebraisk, Hindi, Ungarsk, Indonesisk, Italiensk, Japansk, Koreansk, Litauisk, Malayisk, Marathi, Nepalsk, Norsk, Persisk, Polsk, Portugisisk, Punjabi, Rumensk, Russisk, Serbisk, Slovakisk, Slovensk, Spansk, Swahili, Svensk, Tagalog, Tamil, Thai, Tyrkisk, Ukrainsk, Urdu, Vietnamesisk og flere.

**Ikke rediger oversettelsesfiler manuelt** - de vil bli overskrevet av den automatiserte arbeidsflyten.

## Retningslinjer for kodeformat

### Markdown-konvensjoner

- Bruk standard Markdown-syntaks
- Overskrifter: Bruk `#` for hovedtittel, `##` for seksjoner, `###` for underseksjoner
- Lister: Bruk `-` eller `*` for punktlister, `1.` for nummererte lister
- Lenker: Bruk beskrivende tekst med fullstendige GitHub-URL-er for kryssreferanser
- Bilder: Lagre i `/images/`-katalogen, bruk beskrivende alt-tekst
- Kodeblokker: Bruk tre backticks med språkidentifikator når det er relevant

### Retningslinjer for innhold

- Hold leksjonene fokuserte og konsise (30-60 minutters lesetid)
- Bruk klart og nybegynnervennlig språk
- Unngå instruksjoner for leverandørspesifikke verktøy (kurset er leverandøruavhengig)
- Inkluder læringsmål i starten av hver modul
- Lenke til eksterne Microsoft Learn-ressurser der det er relevant
- Sørg for at innholdet er pedagogisk, ikke promotering

### Navngivning av filer

- Bruk formatet: `[Modul].[Leksjon] [Tittel].md`
- Eksempel: `1.1 The CIA triad and other key concepts.md`
- Quiz-filer: `[Modul].[Siste] End of module quiz.md`
- Bruk mellomrom i filnavn (eksisterende konvensjon)

## GitHub-arbeidsflyter

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push til `main`-grenen  
**Formål:** Oversetter nye/modifiserte Markdown-filer automatisk til 50+ språk

**Nødvendige miljøvariabler:**
- Azure AI Service-legitimasjon (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI-legitimasjon (valgfritt alternativ)
- OpenAI-legitimasjon (valgfritt alternativ)

### Deploy (deploy.yaml)

**Trigger:** Push til `main`-grenen når README.md endres  
**Formål:** Distribuerer statisk nettside til GitHub Pages  
**Output:** Oppdaterer GitHub Pages-nettsiden

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push til konfigurert gren  
**Formål:** Bygger og distribuerer nettsiden ved bruk av Jekyll

## Retningslinjer for pull requests

### Før innsending

1. **Innholdsrevisjon:** Sørg for nøyaktighet og klarhet i cybersikkerhetskonsepter
2. **Formatering:** Verifiser at Markdown-formateringen rendrer korrekt
3. **Lenker:** Test alle interne og eksterne lenker
4. **Bilder:** Sørg for at alle bilder lastes og har beskrivende alt-tekst
5. **Konsistens:** Følg eksisterende innholdsstruktur og stil

### Format for PR-titler

Bruk beskrivende titler:
- `Add: [Beskrivelse av nytt innhold]`
- `Update: [Modul/Leksjon] - [Kort beskrivelse]`
- `Fix: [Beskrivelse av problem]`
- `Docs: [Endringer i dokumentasjon]`

### Nødvendige sjekker

- Nøyaktighet i innhold (manuell gjennomgang)
- Validering av Markdown-formatering
- Lenkeverifisering
- Fullføring av oversettelsesarbeidsflyt (for merges til `main`-grenen)

### Gjennomgangsprosess

1. Minst én gjennomgang av en vedlikeholder er nødvendig
2. Fokus på teknisk nøyaktighet i sikkerhetskonsepter
3. Verifiser tilgjengelighet og nybegynnervennlighet
4. Sørg for at leverandøruavhengighet opprettholdes

## Vanlige oppgaver

### Legge til en ny leksjon

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

### Oppdatere eksisterende innhold

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Legge til bilder

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.no.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testing og validering

### Validering av innhold

Siden dette er et dokumentasjonsprosjekt, fokuserer testing på:

1. **Markdown-rendering:** Vis endringer lokalt ved bruk av Docsify
2. **Lenkevalidering:** Klikk manuelt gjennom alle lenker
3. **Bildelasting:** Verifiser at alle bilder vises korrekt
4. **Oversettelse:** Sjekk at filer plukkes opp av oversettelsesarbeidsflyten (automatisert)
5. **Tilgjengelighet:** Sørg for riktig overskriftsstruktur og alt-tekst

### Lokal forhåndsvisning

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Sjekkliste før commit

- [ ] Markdown-filer bruker korrekt syntaks
- [ ] Alle lenker er gyldige og bruker HTTPS der det er mulig
- [ ] Bilder har beskrivende alt-tekst
- [ ] Innholdet er nybegynnervennlig og nøyaktig
- [ ] Leverandøruavhengig språk opprettholdes
- [ ] README.md oppdatert hvis moduler legges til eller fjernes
- [ ] Filnavn følger konvensjoner

## Sikkerhetsvurderinger

- **Ingen hemmeligheter i innhold:** Aldri commit API-nøkler, passord eller sensitiv data
- **Lenkevalidering:** Sørg for at alle eksterne lenker er til pålitelige kilder
- **Bildeinnhold:** Verifiser at bilder ikke inneholder sensitiv informasjon
- **Oversettelsesarbeidsflyt:** Bruker Azure AI-tjenester med riktig autentisering
- **SECURITY.md:** Følg prosessen for rapportering av sårbarheter i SECURITY.md

## Tilleggsressurser

### Relaterte Microsoft-kurs

Dette kurset er en del av en større samling av Microsofts utdanningsressurser:
- Generativ AI for nybegynnere
- AI for nybegynnere
- Data Science for nybegynnere
- ML for nybegynnere
- Webutvikling for nybegynnere
- IoT for nybegynnere

### Eksterne læringsveier

Etter å ha fullført Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Eksamen SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Bidra

1. **Fork repositoriet** på GitHub
2. **Opprett en feature branch** for endringene dine
3. **Gjør endringene dine** i henhold til retningslinjene ovenfor
4. **Test lokalt** for å sikre at alt rendrer korrekt
5. **Send inn en pull request** med en klar beskrivelse av endringene
6. **Svar på tilbakemeldinger** fra vedlikeholdere

## Vanlige problemer og feilsøking

### Oversettelser fungerer ikke

- Sørg for at endringer er pushet til `main`-grenen
- Sjekk GitHub Actions-fanen for status på arbeidsflyten
- Verifiser at hemmeligheter for oversettelsesarbeidsflyten er konfigurert
- Oversettelse skjer automatisk; ikke rediger oversettelsesfiler manuelt

### Bilder lastes ikke

- Verifiser at bildefilen bruker skråstreker: `images/filnavn.png`
- Sjekk at bildefilen er commitet til repositoriet
- Sørg for at bildefilnavnet stemmer nøyaktig (case-sensitive)
- Bruk relative stier, ikke absolutte URL-er

### Docsify rendrer ikke

- Sjekk at `index.html` er til stede i roten
- Verifiser at Docsify CDN-lenker er tilgjengelige
- Sørg for at Markdown-filer bruker standard syntaks
- Sjekk nettleserkonsollen for JavaScript-feil

### Lenker fungerer ikke

- Bruk fullstendige GitHub-URL-er for kryssreferanser mellom leksjoner
- Format: `https://github.com/microsoft/Security-101/blob/main/[fil].md`
- Test lenker i rendret visning, ikke bare i rå Markdown

## Prosjektvedlikehold

### Regelmessige oppgaver

- Gjennomgå og merge bidrag fra fellesskapet
- Oppdater innhold for nøyaktighet etter hvert som sikkerhetslandskapet utvikler seg
- Overvåk oversettelsesarbeidsflyten for feil
- Svar på problemer og diskusjoner
- Hold eksterne lenker oppdatert

### Versjonskontroll

- `main`-grenen er beskyttet og krever PR-gjennomganger
- Alle endringer går gjennom pull request-prosessen
- Oversettelsesfiler genereres automatisk, ikke rediger manuelt
- Bruk meningsfulle commit-meldinger

## Notater for AI-kodingsagenter

- **Dette er et dokumentasjonsprosjekt** - fokuser på innholdskvalitet, ikke kode
- **Ikke endre oversettelsesfiler** - de genereres automatisk
- **Bevar navnekonvensjoner for filer** - bruk mellomrom i filnavn i henhold til eksisterende mønster
- **Oppdater README.md** når du legger til eller fjerner moduler for å holde tabellen synkronisert
- **Test lokalt** før du sender inn PR-er for å sikre at Markdown rendrer korrekt
- **Følg eksisterende innholdsstil** - oppretthold nybegynnervennlig, leverandøruavhengig tone
- **Ingen byggeprosess nødvendig** - enkel HTTP-server er tilstrekkelig for lokal utvikling
- **Respekter modulstrukturen** - hver modul har konsistent nummerering og organisering

---

**Ansvarsfraskrivelse**:  
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi tilstreber nøyaktighet, vær oppmerksom på at automatiserte oversettelser kan inneholde feil eller unøyaktigheter. Det originale dokumentet på sitt opprinnelige språk bør anses som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.