<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:49:43+00:00",
  "source_file": "AGENTS.md",
  "language_code": "et"
}
-->
# AGENTS.md

## Projekti Ülevaade

**Security-101** on Microsofti loodud algajatele mõeldud küberturvalisuse õppekava. Projekt on dokumentatsioonipõhine õppevahend, mis õpetab küberturvalisuse põhikontseptsioone struktureeritud moodulite kaudu. See on sõltumatu konkreetsetest tootjatest ja mõeldud väikeste õppetundide (30–60 minutit) kaupa läbimiseks.

**Peamised tehnoloogiad:**
- Markdown sisu jaoks
- Docsify staatilise veebisaidi genereerimiseks
- GitHub Pages majutamiseks
- Co-op Translator mitmekeelsete tõlgete jaoks (50+ keelt)
- GitHub Actions CI/CD jaoks

**Arhitektuur:**
- Hariduslik sisu on jaotatud 8 põhimoooduliks, millest igaühel on alamõppetunnid
- Staatiline HTML-veebisait, kus Docsify renderdab Markdowni sisu
- Automatiseeritud tõlkeprotsess Azure AI teenuste abil
- Põhisisu jaoks pole vaja ehitustööriistu ega pakihaldureid

## Repositooriumi Struktuur

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

## Seadistamise Käsud

See on dokumentatsiooniprojekt, millel pole sõltuvusi, mida installida. Sisuga töötamiseks:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Arenduse Töövoog

### Sisu Kohalik Kuvamine

Projekt kasutab Docsify't renderdamiseks. Muudatuste eelvaateks:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Sisu Struktuur

Moodulid on nummerdatud järjestikku:
- **Moodul 1:** Turvalisuse põhikontseptsioonid (1.1–1.7)
- **Moodul 2:** Identiteedi ja juurdepääsu haldamine (2.1–2.4)
- **Moodul 3:** Võrguturvalisus (3.1–3.4)
- **Moodul 4:** Turvaoperatsioonid (4.1–4.4)
- **Moodul 5:** Rakenduste turvalisus (5.1–5.3)
- **Moodul 6:** Infrastruktuuri turvalisus (6.1–6.3)
- **Moodul 7:** Andmete turvalisus (7.1–7.3)
- **Moodul 8:** AI turvalisus (8.1–8.4)

Iga moodul lõpeb viktoriinifailiga (nt "1.7 Mooduli lõpu viktoriin.md").

### Sisumuudatuste Tegemine

1. Redigeeri Markdowni faile otse juurkataloogis
2. Järgi olemasolevat nimekonventsiooni: `[moodul].[õppetund] [Pealkiri].md`
3. Uuenda README.md tabelit, kui lisad/eemaldad mooduleid
4. Lisa pildid kataloogi `/images/`
5. Viita piltidele suhteliste teedega: `![Kirjeldus](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.et.png)`

## Tõlke Töövoog

**Automatiseeritud Tõlge:**
- Tõlked tehakse automaatselt Co-op Translator GitHub Actioni abil
- Kui muudatused lükatakse `main` harusse, tõlgib töövoog sisu 50+ keelde
- Tõlgitud failid salvestatakse kataloogi `/translations/[language_code]/`
- Tõlke metaandmed säilitatakse YAML frontmatter'is

**Toetatud Keeled:** Araabia, Bengali, Bulgaaria, Birma, Hiina (lihtsustatud, traditsiooniline), Horvaadi, Tšehhi, Taani, Hollandi, Eesti, Soome, Prantsuse, Saksa, Kreeka, Heebrea, Hindi, Ungari, Indoneesia, Itaalia, Jaapani, Korea, Leedu, Malai, Marathi, Nepali, Norra, Pärsia, Poola, Portugali, Punjabi, Rumeenia, Vene, Serbia, Slovaki, Sloveeni, Hispaania, Suahiili, Rootsi, Tagalogi, Tamili, Tai, Türgi, Ukraina, Urdu, Vietnami ja palju muud.

**Ära muuda tõlkefailide sisu käsitsi** - need kirjutatakse automaatse töövoo poolt üle.

## Koodistiili Juhised

### Markdowni Konventsioonid

- Kasuta standardset Markdowni süntaksit
- Pealkirjad: Kasuta `#` põhitiitli jaoks, `##` sektsioonide jaoks, `###` alasektsioonide jaoks
- Loendid: Kasuta `-` või `*` loendite jaoks, `1.` järjestatud loendite jaoks
- Lingid: Kasuta kirjeldavat teksti koos täielike GitHubi URL-idega viidete jaoks
- Pildid: Salvesta kataloogi `/images/`, kasuta kirjeldavat alt-teksti
- Koodiplokid: Kasuta kolmekordseid tagurpidi jutumärke koos keele identifikaatoriga, kui võimalik

### Sisujuhised

- Hoia õppetunnid keskendunud ja lühikesed (30–60 minutit lugemisaega)
- Kasuta selget ja algajasõbralikku keelt
- Vältida tootjaspetsiifiliste tööriistade juhiseid (õppekava on sõltumatu tootjatest)
- Lisa õpieesmärgid iga mooduli algusesse
- Viita Microsoft Learn'i välistele ressurssidele, kui sobilik
- Veendu, et sisu oleks hariv, mitte reklaamiv

### Failinime Konventsioonid

- Kasuta formaati: `[Moodul].[Õppetund] [Pealkiri].md`
- Näide: `1.1 CIA triad ja muud olulised kontseptsioonid.md`
- Viktoriinifailid: `[Moodul].[Viimane] Mooduli lõpu viktoriin.md`
- Kasuta failinimedes tühikuid (olemasolev konventsioon)

## GitHubi Töövood

### Co-op Translator (co-op-translator.yml)

**Käivitamine:** Push `main` harusse  
**Eesmärk:** Tõlgib automaatselt uued/muudetud Markdowni failid 50+ keelde

**Nõutavad Keskkonnamuutujad:**
- Azure AI teenuse mandaadid (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI mandaadid (valikuline alternatiiv)
- OpenAI mandaadid (valikuline alternatiiv)

### Deploy (deploy.yaml)

**Käivitamine:** Push `main` harusse, kui README.md muutub  
**Eesmärk:** Staatilise veebisaidi juurutamine GitHub Pages'ile  
**Väljund:** Uuendab GitHub Pages'i veebisaiti

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Käivitamine:** Push konfigureeritud harusse  
**Eesmärk:** Ehitatakse ja juurutatakse veebisait Jekylli abil

## Pull Request'i Juhised

### Enne Esitamist

1. **Sisu Ülevaatus:** Veendu küberturvalisuse kontseptsioonide täpsuses ja selguses
2. **Formaatimine:** Kontrolli, et Markdowni formaatimine renderduks õigesti
3. **Lingid:** Testi kõiki sisemisi ja väliseid linke
4. **Pildid:** Veendu, et kõik pildid laadiksid ja neil oleks kirjeldav alt-tekst
5. **Järjepidevus:** Järgi olemasolevat sisu struktuuri ja stiili

### PR Pealkirja Formaat

Kasuta kirjeldavaid pealkirju:
- `Lisa: [Uue sisu kirjeldus]`
- `Uuenda: [Moodul/Õppetund] - [Lühike kirjeldus]`
- `Paranda: [Probleemi kirjeldus]`
- `Dokumendid: [Dokumentatsiooni muudatused]`

### Nõutavad Kontrollid

- Sisu täpsus (käsitsi ülevaatus)
- Markdowni formaadi valideerimine
- Linkide kontroll
- Tõlke töövoo lõpetamine (kui `main` harusse ühendatakse)

### Ülevaatusprotsess

1. Vähemalt üks haldaja ülevaatus on vajalik
2. Keskendu turvalisuse kontseptsioonide tehnilisele täpsusele
3. Kontrolli ligipääsetavust ja algajasõbralikkust
4. Veendu, et tootjaspetsiifilisus oleks välditud

## Üldised Ülesanded

### Uue Õppetunni Lisamine

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

### Olemasoleva Sisu Uuendamine

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Piltide Lisamine

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.et.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testimine ja Valideerimine

### Sisu Valideerimine

Kuna tegemist on dokumentatsiooniprojektiga, keskendub testimine järgmisele:

1. **Markdowni Renderdamine:** Vaata muudatusi kohalikult Docsify abil
2. **Linkide Kontroll:** Klõpsa käsitsi läbi kõik lingid
3. **Piltide Laadimine:** Veendu, et kõik pildid kuvatakse õigesti
4. **Tõlge:** Kontrolli, et failid oleksid tõlkija töövoo poolt tuvastatud (automaatne)
5. **Ligipääsetavus:** Veendu, et pealkirjade hierarhia ja alt-tekst oleksid korrektsed

### Kohalik Eelvaade

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Enne Commit'i Kontrollnimekiri

- [ ] Markdowni failid kasutavad õiget süntaksit
- [ ] Kõik lingid on kehtivad ja kasutavad võimalusel HTTPS-i
- [ ] Piltidel on kirjeldav alt-tekst
- [ ] Sisu on algajasõbralik ja täpne
- [ ] Tootjaspetsiifilisus on välditud
- [ ] README.md on uuendatud, kui mooduleid lisatakse/eemaldatakse
- [ ] Failinimed järgivad konventsioone

## Turvalisuse Kaalutlused

- **Ära lisa sisu salajasi andmeid:** Ära kunagi commit'i API võtmeid, paroole ega tundlikke andmeid
- **Linkide Kontroll:** Veendu, et kõik välised lingid viiksid usaldusväärsetele allikatele
- **Piltide Sisu:** Kontrolli, et pildid ei sisaldaks tundlikku teavet
- **Tõlke Töövoog:** Kasutab Azure AI teenuseid koos korrektse autentimisega
- **SECURITY.md:** Järgi SECURITY.md-s kirjeldatud haavatavuste raporteerimise protsessi

## Täiendavad Ressursid

### Seotud Microsofti Kursused

See õppekava on osa Microsofti haridusressursside suuremast kogumikust:
- Generatiivne AI algajatele
- AI algajatele
- Andmeteadus algajatele
- ML algajatele
- Veebiarendus algajatele
- IoT algajatele

### Välised Õppeprogrammid

Pärast Security-101 läbimist:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Eksami SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Kaastöö

1. **Fork'i repositoorium** GitHubis
2. **Loo funktsiooni haru** oma muudatuste jaoks
3. **Tee muudatused** järgides ülaltoodud juhiseid
4. **Testi kohalikult**, et veenduda, et kõik renderdub õigesti
5. **Esita pull request** selge muudatuste kirjeldusega
6. **Vasta haldajate tagasisidele**

## Üldised Probleemid ja Tõrkeotsing

### Tõlked Ei Tööta

- Veendu, et muudatused on lükatud `main` harusse
- Kontrolli GitHub Actions'i vahekaarti töövoo staatuse jaoks
- Veendu, et tõlke töövoo mandaadid on konfigureeritud
- Tõlge toimub automaatselt; ära muuda tõlkefailide sisu käsitsi

### Pildid Ei Laadi

- Kontrolli, et pildi tee kasutab kaldkriipse: `images/filename.png`
- Veendu, et pildifail on repositooriumis commit'itud
- Kontrolli, et pildifaili nimi vastab täpselt (tõstutundlik)
- Kasuta suhtelisi teid, mitte absoluutseid URL-e

### Docsify Ei Renderda

- Kontrolli, et `index.html` on juurkataloogis olemas
- Veendu, et Docsify CDN lingid on ligipääsetavad
- Kontrolli, et Markdowni failid kasutavad standardset süntaksit
- Kontrolli brauseri konsooli JavaScripti vigade jaoks

### Lingid Ei Tööta

- Kasuta täielikke GitHubi URL-e viidete jaoks õppetundide vahel
- Formaat: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testi linke renderdatud vaates, mitte ainult toor Markdownis

## Projekti Hooldus

### Regulaarne Ülesannete Täitmine

- Ülevaata ja ühenda kogukonna panused
- Uuenda sisu, et tagada täpsus turvalisuse maastiku muutudes
- Jälgi tõlke töövoogu vigade osas
- Vasta probleemidele ja aruteludele
- Hoia välised lingid ajakohased

### Versioonihaldus

- `main` haru on kaitstud ja nõuab PR-i ülevaatusi
- Kõik muudatused tehakse pull request'i protsessi kaudu
- Tõlkefailid genereeritakse automaatselt, ära muuda neid käsitsi
- Kasuta tähenduslikke commit'i sõnumeid

## Märkused AI Kodeerimisagentidele

- **See on dokumentatsiooniprojekt** - keskendu sisu kvaliteedile, mitte koodile
- **Ära muuda tõlkefailide sisu** - need genereeritakse automaatselt
- **Säilita failinime konventsioonid** - kasuta failinimedes tühikuid vastavalt olemasolevale mustrile
- **Uuenda README.md**, kui lisad/eemaldad mooduleid, et tabel oleks sünkroonis
- **Testi kohalikult**, enne PR-i esitamist, et veenduda, et Markdown renderdub õigesti
- **Järgi olemasolevat sisustiili** - hoia algajasõbralik ja tootjaspetsiifilisuseta toon
- **Ehitustöötlust pole vaja** - lihtne HTTP-server on kohalikuks arenduseks piisav
- **Austa mooduli struktuuri** - iga moodulil on järjekindel nummerdamine ja korraldus

---

**Lahtiütlus**:  
See dokument on tõlgitud AI tõlketeenuse [Co-op Translator](https://github.com/Azure/co-op-translator) abil. Kuigi püüame tagada täpsust, palume arvestada, et automaatsed tõlked võivad sisaldada vigu või ebatäpsusi. Algne dokument selle algses keeles tuleks pidada autoriteetseks allikaks. Olulise teabe puhul soovitame kasutada professionaalset inimtõlget. Me ei vastuta selle tõlke kasutamisest tulenevate arusaamatuste või valesti tõlgenduste eest.