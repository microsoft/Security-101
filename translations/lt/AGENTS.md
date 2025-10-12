<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:48:31+00:00",
  "source_file": "AGENTS.md",
  "language_code": "lt"
}
-->
# AGENTS.md

## Projekto apžvalga

**Security-101** yra pradedantiesiems skirta kibernetinio saugumo mokymo programa, sukurta „Microsoft“. Projektas yra dokumentacijos pagrindu sukurtas mokymosi šaltinis, kuris moko pagrindinių kibernetinio saugumo koncepcijų per struktūrizuotus modulius. Jis yra nepriklausomas nuo tiekėjų ir sukurtas taip, kad būtų galima atlikti mažas pamokas (po 30–60 minučių).

**Pagrindinės technologijos:**
- Turinys sukurtas naudojant Markdown
- Docsify statinių svetainių generavimui
- GitHub Pages talpinimui
- Co-op Translator daugiakalbei paramai (50+ kalbų)
- GitHub Actions CI/CD procesams

**Architektūra:**
- Mokomasis turinys suskirstytas į 8 pagrindinius modulius, kiekvienas su subpamokomis
- Statinė HTML svetainė, kur Docsify pateikia Markdown turinį
- Automatinis vertimo procesas naudojant Azure AI paslaugas
- Pagrindiniam turiniui nereikia jokių kūrimo įrankių ar paketų valdymo sistemų

## Saugyklos struktūra

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

## Nustatymo komandos

Tai dokumentacijos projektas, kuriam nereikia jokių priklausomybių. Norėdami dirbti su turiniu:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Kūrimo procesas

### Turinio peržiūra vietoje

Projektas naudoja Docsify turinio pateikimui. Norėdami peržiūrėti pakeitimus:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Turinio struktūra

Moduliai numeruojami iš eilės:
- **1 modulis:** Pagrindinės saugumo sąvokos (1.1–1.7)
- **2 modulis:** Tapatybės ir prieigos valdymas (2.1–2.4)
- **3 modulis:** Tinklo saugumas (3.1–3.4)
- **4 modulis:** Saugumo operacijos (4.1–4.4)
- **5 modulis:** Programų saugumas (5.1–5.3)
- **6 modulis:** Infrastruktūros saugumas (6.1–6.3)
- **7 modulis:** Duomenų saugumas (7.1–7.3)
- **8 modulis:** AI saugumas (8.1–8.4)

Kiekvienas modulis baigiasi testu (pvz., „1.7 End of module quiz.md“).

### Turinio pakeitimų atlikimas

1. Redaguokite Markdown failus tiesiogiai pagrindiniame kataloge
2. Laikykitės esamos pavadinimų konvencijos: `[module].[lesson] [Title].md`
3. Atnaujinkite README.md lentelę, jei pridedate/šalinate modulius
4. Pridėkite vaizdus į `/images/` katalogą
5. Naudokite santykinius kelių nurodymus vaizdams: `![Aprašymas](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.lt.png)`

## Vertimo procesas

**Automatinis vertimas:**
- Vertimai atliekami automatiškai naudojant Co-op Translator GitHub veiksmą
- Kai įkeliate pakeitimus į `main` šaką, procesas išverčia turinį į 50+ kalbų
- Išversti failai saugomi `/translations/[language_code]/`
- Vertimo metaduomenys išsaugomi YAML frontmatter

**Palaikomos kalbos:** Arabų, bengalų, bulgarų, birmiečių, kinų (supaprastinta, tradicinė), kroatų, čekų, danų, olandų, estų, suomių, prancūzų, vokiečių, graikų, hebrajų, hindi, vengrų, indoneziečių, italų, japonų, korėjiečių, lietuvių, malajų, maratų, nepaliečių, norvegų, persų, lenkų, portugalų, pandžabų, rumunų, rusų, serbų, slovakų, slovėnų, ispanų, suahilių, švedų, tagalogų, tamilų, tajų, turkų, ukrainiečių, urdu, vietnamiečių ir kt.

**Nedarykite rankinių vertimų failų pakeitimų** - jie bus perrašyti automatinio proceso metu.

## Kodo stiliaus gairės

### Markdown konvencijos

- Naudokite standartinę Markdown sintaksę
- Antraštės: Naudokite `#` pagrindiniam pavadinimui, `##` skirsniams, `###` poskirsniams
- Sąrašai: Naudokite `-` arba `*` neorganizuotiems sąrašams, `1.` organizuotiems sąrašams
- Nuorodos: Naudokite aprašomąjį tekstą su pilnais GitHub URL kryžminėms nuorodoms
- Vaizdai: Saugojimas `/images/` kataloge, naudokite aprašomąjį alt tekstą
- Kodo blokai: Naudokite trigubas kabutes su kalbos identifikatoriumi, jei taikoma

### Turinio gairės

- Pamokos turi būti aiškios ir koncentruotos (30–60 minučių skaitymo laikas)
- Naudokite aiškią, pradedantiesiems draugišką kalbą
- Venkite tiekėjų specifinių įrankių instrukcijų (mokymo programa yra nepriklausoma nuo tiekėjų)
- Pradėkite kiekvieną modulį su mokymosi tikslais
- Nuorodos į išorinius „Microsoft Learn“ šaltinius, kur tinkama
- Užtikrinkite, kad turinys būtų edukacinis, o ne reklaminis

### Failų pavadinimai

- Naudokite formatą: `[Module].[Lesson] [Title].md`
- Pavyzdys: `1.1 The CIA triad and other key concepts.md`
- Testų failai: `[Module].[Last] End of module quiz.md`
- Naudokite tarpus failų pavadinimuose (esama konvencija)

## GitHub procesai

### Co-op Translator (co-op-translator.yml)

**Paleidimas:** Įkėlimas į `main` šaką  
**Tikslas:** Automatiškai išverčia naujus/pakeistus Markdown failus į 50+ kalbų

**Reikalingi aplinkos kintamieji:**
- Azure AI paslaugų kredencialai (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI kredencialai (neprivaloma alternatyva)
- OpenAI kredencialai (neprivaloma alternatyva)

### Diegimas (deploy.yaml)

**Paleidimas:** Įkėlimas į `main` šaką, kai README.md pakeičiamas  
**Tikslas:** Diegia statinę svetainę į GitHub Pages  
**Rezultatas:** Atnaujina GitHub Pages svetainę

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Paleidimas:** Įkėlimas į sukonfigūruotą šaką  
**Tikslas:** Sukuria ir diegia svetainę naudojant Jekyll

## Pull Request gairės

### Prieš pateikimą

1. **Turinio peržiūra:** Užtikrinkite kibernetinio saugumo sąvokų tikslumą ir aiškumą
2. **Formatavimas:** Patikrinkite, ar Markdown formatavimas tinkamai pateikiamas
3. **Nuorodos:** Išbandykite visas vidines ir išorines nuorodas
4. **Vaizdai:** Užtikrinkite, kad visi vaizdai būtų įkeliami ir turėtų aprašomąjį alt tekstą
5. **Nuoseklumas:** Laikykitės esamos turinio struktūros ir stiliaus

### PR pavadinimo formatas

Naudokite aprašomuosius pavadinimus:
- `Add: [Naujo turinio aprašymas]`
- `Update: [Modulis/Pamoka] - [Trumpas aprašymas]`
- `Fix: [Problemos aprašymas]`
- `Docs: [Dokumentacijos pakeitimai]`

### Reikalingi patikrinimai

- Turinio tikslumas (rankinė peržiūra)
- Markdown formatavimo patvirtinimas
- Nuorodų patikrinimas
- Vertimo proceso užbaigimas (skirta `main` šakos sujungimams)

### Peržiūros procesas

1. Reikalinga bent vieno prižiūrėtojo peržiūra
2. Dėmesys kibernetinio saugumo sąvokų techniniam tikslumui
3. Patikrinkite prieinamumą ir pradedantiesiems draugiškumą
4. Užtikrinkite, kad būtų išlaikytas nepriklausomumas nuo tiekėjų

## Dažnos užduotys

### Naujos pamokos pridėjimas

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

### Esamo turinio atnaujinimas

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Vaizdų pridėjimas

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.lt.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testavimas ir patvirtinimas

### Turinio patvirtinimas

Kadangi tai dokumentacijos projektas, testavimas orientuotas į:

1. **Markdown pateikimą:** Peržiūrėkite pakeitimus vietoje naudodami Docsify
2. **Nuorodų patvirtinimą:** Rankiniu būdu spustelėkite visas nuorodas
3. **Vaizdų įkėlimą:** Patikrinkite, ar visi vaizdai tinkamai rodomi
4. **Vertimą:** Patikrinkite, ar failai yra įtraukti į vertimo procesą (automatinis)
5. **Prieinamumą:** Užtikrinkite tinkamą antraščių hierarchiją ir alt tekstą

### Vietinė peržiūra

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Prieš įsipareigojimą kontrolinis sąrašas

- [ ] Markdown failai naudoja tinkamą sintaksę
- [ ] Visos nuorodos yra galiojančios ir, jei įmanoma, naudoja HTTPS
- [ ] Vaizdai turi aprašomąjį alt tekstą
- [ ] Turinys yra pradedantiesiems draugiškas ir tikslus
- [ ] Išlaikytas nepriklausomumas nuo tiekėjų
- [ ] README.md atnaujintas, jei pridedami/šalinami moduliai
- [ ] Failų pavadinimai atitinka konvencijas

## Saugumo aspektai

- **Jokių slaptų duomenų turinyje:** Niekada neįkelkite API raktų, slaptažodžių ar jautrių duomenų
- **Nuorodų patvirtinimas:** Užtikrinkite, kad visos išorinės nuorodos būtų patikimos
- **Vaizdų turinys:** Patikrinkite, ar vaizdai neturi jautrios informacijos
- **Vertimo procesas:** Naudoja Azure AI paslaugas su tinkama autentifikacija
- **SECURITY.md:** Laikykitės pažeidžiamumo pranešimo proceso, nurodyto SECURITY.md

## Papildomi ištekliai

### Susiję „Microsoft“ kursai

Ši mokymo programa yra didesnės „Microsoft“ edukacinių išteklių kolekcijos dalis:
- Generatyvinis AI pradedantiesiems
- AI pradedantiesiems
- Duomenų mokslas pradedantiesiems
- ML pradedantiesiems
- Web Dev pradedantiesiems
- IoT pradedantiesiems

### Išoriniai mokymosi keliai

Baigus Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Prisidėjimas

1. **Fork saugyklą** GitHub
2. **Sukurkite funkcijų šaką** savo pakeitimams
3. **Atlikite pakeitimus** laikydamiesi aukščiau pateiktų gairių
4. **Testuokite vietoje**, kad įsitikintumėte, jog viskas tinkamai pateikiama
5. **Pateikite pull request** su aiškiu pakeitimų aprašymu
6. **Atsakykite į prižiūrėtojų atsiliepimus**

## Dažnos problemos ir trikčių šalinimas

### Vertimai neveikia

- Įsitikinkite, kad pakeitimai įkelti į `main` šaką
- Patikrinkite GitHub Actions skirtuką dėl proceso būsenos
- Patikrinkite, ar vertimo proceso slaptažodžiai yra sukonfigūruoti
- Vertimas vyksta automatiškai; nedarykite rankinių vertimų failų pakeitimų

### Vaizdai neįkeliami

- Patikrinkite, ar vaizdo kelias naudoja pasviruosius brūkšnius: `images/filename.png`
- Įsitikinkite, kad vaizdo failas yra įkeltas į saugyklą
- Patikrinkite, ar vaizdo failo pavadinimas tiksliai atitinka (skirtumas tarp didžiųjų ir mažųjų raidžių)
- Naudokite santykinius kelius, o ne absoliučius URL

### Docsify nepateikia turinio

- Patikrinkite, ar `index.html` yra pagrindiniame kataloge
- Įsitikinkite, kad Docsify CDN nuorodos yra pasiekiamos
- Patikrinkite, ar Markdown failai naudoja standartinę sintaksę
- Naršyklės konsolėje patikrinkite JavaScript klaidas

### Nuorodos neveikia

- Naudokite pilnus GitHub URL kryžminėms nuorodoms tarp pamokų
- Formatavimas: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testuokite nuorodas pateiktame vaizde, o ne tik žaliame Markdown

## Projekto priežiūra

### Reguliarios užduotys

- Peržiūrėkite ir sujunkite bendruomenės indėlius
- Atnaujinkite turinį, kad jis būtų tikslus, kai saugumo aplinka keičiasi
- Stebėkite vertimo procesą dėl klaidų
- Atsakykite į problemas ir diskusijas
- Atnaujinkite išorines nuorodas

### Versijų kontrolė

- `main` šaka yra apsaugota ir reikalauja PR peržiūrų
- Visi pakeitimai atliekami per pull request procesą
- Vertimo failai yra automatiškai generuojami, jų nereikia redaguoti rankiniu būdu
- Naudokite prasmingus commit pranešimus

## Pastabos AI kodavimo agentams

- **Tai dokumentacijos projektas** - dėmesys turinio kokybei, o ne kodui
- **Nekeiskite vertimo failų** - jie yra automatiškai generuojami
- **Išlaikykite failų pavadinimų konvencijas** - naudokite tarpus failų pavadinimuose pagal esamą modelį
- **Atnaujinkite README.md**, kai pridedate/šalinate modulius, kad lentelė būtų sinchronizuota
- **Testuokite vietoje**, prieš pateikdami PR, kad įsitikintumėte, jog Markdown tinkamai pateikiamas
- **Laikykitės esamo turinio stiliaus** - išlaikykite pradedantiesiems draugišką, nepriklausomą nuo tiekėjų toną
- **Nereikia kūrimo proceso** - paprastas HTTP serveris yra pakankamas vietiniam kūrimui
- **Gerbkite modulio struktūrą** - kiekvienas modulis turi nuoseklų numeravimą ir organizaciją

---

**Atsakomybės apribojimas**:  
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors siekiame tikslumo, atkreipkite dėmesį, kad automatiniai vertimai gali turėti klaidų ar netikslumų. Originalus dokumentas jo gimtąja kalba turėtų būti laikomas autoritetingu šaltiniu. Dėl svarbios informacijos rekomenduojama naudotis profesionaliomis žmogaus vertimo paslaugomis. Mes neprisiimame atsakomybės už nesusipratimus ar klaidingus aiškinimus, kylančius dėl šio vertimo naudojimo.