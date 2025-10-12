<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:44:03+00:00",
  "source_file": "AGENTS.md",
  "language_code": "sk"
}
-->
# AGENTS.md

## Prehľad projektu

**Security-101** je učebný plán kybernetickej bezpečnosti pre začiatočníkov, ktorý vytvorila spoločnosť Microsoft. Projekt je vzdelávací zdroj založený na dokumentácii, ktorý učí základné koncepty kybernetickej bezpečnosti prostredníctvom štruktúrovaných modulov. Je nezávislý od dodávateľa a navrhnutý tak, aby sa dal dokončiť v krátkych lekciách (každá trvá 30-60 minút).

**Kľúčové technológie:**
- Markdown pre obsah
- Docsify pre generovanie statických stránok
- GitHub Pages pre hosting
- Co-op Translator pre podporu viacerých jazykov (50+ jazykov)
- GitHub Actions pre CI/CD

**Architektúra:**
- Vzdelávací obsah organizovaný v 8 hlavných moduloch, každý s podlekciami
- Statická HTML stránka s Docsify, ktorá vykresľuje obsah Markdown
- Automatizovaný prekladový proces pomocou služieb Azure AI
- Nie sú potrebné žiadne nástroje na zostavovanie alebo správu balíkov pre základný obsah

## Štruktúra repozitára

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

## Príkazy na nastavenie

Toto je projekt dokumentácie bez potreby inštalácie závislostí. Na prácu s obsahom:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Pracovný postup vývoja

### Zobrazenie obsahu lokálne

Projekt používa Docsify na vykresľovanie. Na náhľad zmien:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Štruktúra obsahu

Moduly sú číslované postupne:
- **Modul 1:** Základné koncepty bezpečnosti (1.1-1.7)
- **Modul 2:** Správa identity a prístupu (2.1-2.4)
- **Modul 3:** Sieťová bezpečnosť (3.1-3.4)
- **Modul 4:** Bezpečnostné operácie (4.1-4.4)
- **Modul 5:** Bezpečnosť aplikácií (5.1-5.3)
- **Modul 6:** Bezpečnosť infraštruktúry (6.1-6.3)
- **Modul 7:** Bezpečnosť dát (7.1-7.3)
- **Modul 8:** Bezpečnosť AI (8.1-8.4)

Každý modul končí súborom s kvízom (napr. "1.7 End of module quiz.md").

### Zmeny obsahu

1. Upravte súbory Markdown priamo v koreňovom adresári
2. Dodržujte existujúce názvoslovie: `[module].[lesson] [Title].md`
3. Aktualizujte tabuľku v README.md, ak pridávate/odstraňujete moduly
4. Obrázky pridávajte do adresára `/images/`
5. Odkazujte na obrázky pomocou relatívnych ciest: `![Popis](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.sk.png)`

## Pracovný postup prekladu

**Automatizovaný preklad:**
- Preklady sú spracovávané automaticky pomocou GitHub Action Co-op Translator
- Keď vykonáte zmeny v hlavnej vetve `main`, pracovný postup preloží obsah do viac ako 50 jazykov
- Preložené súbory sú uložené v `/translations/[language_code]/`
- Metadáta prekladu sú zachované v YAML frontmatter

**Podporované jazyky:** Arabčina, bengálčina, bulharčina, barmčina, čínština (zjednodušená, tradičná), chorvátčina, čeština, dánčina, holandčina, estónčina, fínčina, francúzština, nemčina, gréčtina, hebrejčina, hindčina, maďarčina, indonézština, taliančina, japončina, kórejčina, litovčina, malajčina, maráthčina, nepálčina, nórčina, perzština, poľština, portugalčina, pandžábčina, rumunčina, ruština, srbčina, slovenčina, slovinčina, španielčina, svahilčina, švédčina, tagalčina, tamilčina, thajčina, turečtina, ukrajinčina, urdčina, vietnamčina a ďalšie.

**NEUPRAVUJTE manuálne prekladové súbory** - budú prepísané automatizovaným procesom.

## Štýlové pokyny pre kód

### Konvencie pre Markdown

- Používajte štandardnú syntax Markdown
- Nadpisy: Používajte `#` pre hlavný názov, `##` pre sekcie, `###` pre podsekcie
- Zoznamy: Používajte `-` alebo `*` pre nečíslované zoznamy, `1.` pre číslované zoznamy
- Odkazy: Používajte popisný text s úplnými URL adresami GitHub pre krížové odkazy
- Obrázky: Ukladajte do adresára `/images/`, používajte popisný alt text
- Bloky kódu: Používajte trojité spätné úvodzovky s identifikátorom jazyka, ak je to možné

### Pokyny pre obsah

- Udržujte lekcie zamerané a stručné (30-60 minút čítania)
- Používajte jasný, začiatočníkom priateľský jazyk
- Vyhnite sa pokynom pre nástroje špecifické pre konkrétneho dodávateľa (učebný plán je nezávislý od dodávateľa)
- Na začiatku každého modulu uveďte vzdelávacie ciele
- Odkazujte na externé zdroje Microsoft Learn, kde je to vhodné
- Zabezpečte, aby bol obsah vzdelávací, nie propagačný

### Názvoslovie súborov

- Používajte formát: `[Module].[Lesson] [Title].md`
- Príklad: `1.1 The CIA triad and other key concepts.md`
- Súbory s kvízmi: `[Module].[Last] End of module quiz.md`
- Používajte medzery v názvoch súborov (existujúca konvencia)

## GitHub pracovné postupy

### Co-op Translator (co-op-translator.yml)

**Spúšťač:** Push do vetvy `main`  
**Účel:** Automaticky prekladá nové/upravené súbory Markdown do viac ako 50 jazykov

**Požadované premenné prostredia:**
- Prihlasovacie údaje služby Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Prihlasovacie údaje Azure OpenAI (voliteľná alternatíva)
- Prihlasovacie údaje OpenAI (voliteľná alternatíva)

### Nasadenie (deploy.yaml)

**Spúšťač:** Push do vetvy `main`, keď sa zmení README.md  
**Účel:** Nasadenie statickej stránky na GitHub Pages  
**Výstup:** Aktualizuje stránku GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Spúšťač:** Push do konfigurovanej vetvy  
**Účel:** Vytvára a nasadzuje stránku pomocou Jekyll

## Pokyny pre pull requesty

### Pred odoslaním

1. **Kontrola obsahu:** Zabezpečte presnosť a jasnosť konceptov kybernetickej bezpečnosti
2. **Formátovanie:** Overte, že formátovanie Markdown sa správne zobrazuje
3. **Odkazy:** Otestujte všetky interné a externé odkazy
4. **Obrázky:** Zabezpečte, že všetky obrázky sa načítajú a majú popisný alt text
5. **Konzistentnosť:** Dodržujte existujúcu štruktúru a štýl obsahu

### Formát názvu PR

Používajte popisné názvy:
- `Add: [Popis nového obsahu]`
- `Update: [Modul/Lekcia] - [Stručný popis]`
- `Fix: [Popis problému]`
- `Docs: [Zmeny v dokumentácii]`

### Požadované kontroly

- Presnosť obsahu (manuálna kontrola)
- Validácia formátovania Markdown
- Overenie odkazov
- Dokončenie prekladového pracovného postupu (pre zlúčenia do vetvy `main`)

### Proces kontroly

1. Vyžaduje sa aspoň jedna kontrola od správcu
2. Zamerajte sa na technickú presnosť konceptov bezpečnosti
3. Overte prístupnosť a priateľskosť pre začiatočníkov
4. Zabezpečte, aby bola zachovaná nezávislosť od dodávateľa

## Bežné úlohy

### Pridanie novej lekcie

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

### Aktualizácia existujúceho obsahu

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Pridanie obrázkov

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.sk.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testovanie a validácia

### Validácia obsahu

Keďže ide o projekt dokumentácie, testovanie sa zameriava na:

1. **Vykresľovanie Markdown:** Zobrazenie zmien lokálne pomocou Docsify
2. **Validácia odkazov:** Manuálne kliknutie na všetky odkazy
3. **Načítanie obrázkov:** Overenie, že všetky obrázky sa správne zobrazujú
4. **Preklad:** Overenie, že súbory sú zachytené prekladovým pracovným postupom (automatizované)
5. **Prístupnosť:** Zabezpečenie správnej hierarchie nadpisov a alt textu

### Lokálny náhľad

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Kontrolný zoznam pred commitom

- [ ] Súbory Markdown používajú správnu syntax
- [ ] Všetky odkazy sú platné a používajú HTTPS, ak je to možné
- [ ] Obrázky majú popisný alt text
- [ ] Obsah je priateľský pre začiatočníkov a presný
- [ ] Je zachovaný jazyk nezávislý od dodávateľa
- [ ] README.md je aktualizovaný, ak sa pridávajú/odstraňujú moduly
- [ ] Názvy súborov dodržiavajú konvencie

## Bezpečnostné úvahy

- **Žiadne tajomstvá v obsahu:** Nikdy neukladajte API kľúče, heslá alebo citlivé údaje
- **Validácia odkazov:** Zabezpečte, že všetky externé odkazy vedú na dôveryhodné zdroje
- **Obsah obrázkov:** Overte, že obrázky neobsahujú citlivé informácie
- **Prekladový pracovný postup:** Používa služby Azure AI s riadnym overením
- **SECURITY.md:** Dodržujte proces nahlasovania zraniteľností uvedený v SECURITY.md

## Ďalšie zdroje

### Súvisiace kurzy od Microsoftu

Tento učebný plán je súčasťou väčšej kolekcie vzdelávacích zdrojov od Microsoftu:
- Generatívna AI pre začiatočníkov
- AI pre začiatočníkov
- Data Science pre začiatočníkov
- ML pre začiatočníkov
- Webový vývoj pre začiatočníkov
- IoT pre začiatočníkov

### Externé vzdelávacie cesty

Po dokončení Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Prispievanie

1. **Forknite repozitár** na GitHube
2. **Vytvorte vetvu pre funkciu** pre vaše zmeny
3. **Urobte svoje zmeny** podľa vyššie uvedených pokynov
4. **Otestujte lokálne**, aby ste sa uistili, že všetko sa správne vykresľuje
5. **Odošlite pull request** s jasným popisom zmien
6. **Reagujte na spätnú väzbu** od správcov

## Bežné problémy a riešenie

### Preklady nefungujú

- Uistite sa, že zmeny boli odoslané do vetvy `main`
- Skontrolujte kartu GitHub Actions pre stav pracovného postupu
- Overte, že sú nastavené tajomstvá pre prekladový pracovný postup
- Preklad prebieha automaticky; manuálne neupravujte prekladové súbory

### Obrázky sa nenačítavajú

- Overte, že cesta k obrázku používa lomky: `images/filename.png`
- Skontrolujte, či bol súbor obrázka odoslaný do repozitára
- Uistite sa, že názov súboru obrázka presne zodpovedá (rozlišuje sa veľkosť písmen)
- Používajte relatívne cesty, nie absolútne URL

### Docsify sa nevykresľuje

- Skontrolujte, či je v koreňovom adresári prítomný súbor `index.html`
- Overte, že odkazy na CDN Docsify sú prístupné
- Uistite sa, že súbory Markdown používajú štandardnú syntax
- Skontrolujte konzolu prehliadača pre chyby JavaScriptu

### Odkazy nefungujú

- Používajte úplné URL adresy GitHub pre krížové odkazy medzi lekciami
- Formát: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testujte odkazy v zobrazení vykreslenia, nielen v surovom Markdown

## Údržba projektu

### Pravidelné úlohy

- Kontrola a zlúčenie príspevkov od komunity
- Aktualizácia obsahu pre presnosť podľa vývoja v oblasti bezpečnosti
- Monitorovanie prekladového pracovného postupu pre chyby
- Reakcia na problémy a diskusie
- Udržiavanie aktuálnosti externých odkazov

### Správa verzií

- Vetva `main` je chránená a vyžaduje kontrolu PR
- Všetky zmeny prechádzajú procesom pull requestu
- Prekladové súbory sú automaticky generované, neupravujte ich manuálne
- Používajte zmysluplné správy commitov

## Poznámky pre AI programátorských agentov

- **Toto je projekt dokumentácie** - zamerajte sa na kvalitu obsahu, nie na kód
- **Neupravujte prekladové súbory** - sú automaticky generované
- **Zachovajte konvencie názvov súborov** - používajte medzery v názvoch súborov podľa existujúceho vzoru
- **Aktualizujte README.md** pri pridávaní/odstraňovaní modulov, aby bola tabuľka synchronizovaná
- **Testujte lokálne** pred odoslaním PR, aby ste sa uistili, že Markdown sa správne vykresľuje
- **Dodržujte existujúci štýl obsahu** - zachovajte priateľský tón pre začiatočníkov a nezávislosť od dodávateľa
- **Nie je potrebný žiadny proces zostavovania** - jednoduchý HTTP server je dostatočný pre lokálny vývoj
- **Rešpektujte štruktúru modulu** - každý modul má konzistentné číslovanie a organizáciu

---

**Upozornenie**:  
Tento dokument bol preložený pomocou služby AI prekladu [Co-op Translator](https://github.com/Azure/co-op-translator). Hoci sa snažíme o presnosť, upozorňujeme, že automatizované preklady môžu obsahovať chyby alebo nepresnosti. Pôvodný dokument v jeho pôvodnom jazyku by mal byť považovaný za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny ľudský preklad. Nenesieme zodpovednosť za akékoľvek nedorozumenia alebo nesprávne interpretácie vyplývajúce z použitia tohto prekladu.