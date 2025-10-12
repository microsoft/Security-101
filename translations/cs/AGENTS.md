<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:43:26+00:00",
  "source_file": "AGENTS.md",
  "language_code": "cs"
}
-->
# AGENTS.md

## Přehled projektu

**Security-101** je přívětivý vzdělávací program o kybernetické bezpečnosti vytvořený společností Microsoft. Projekt je dokumentačním zdrojem, který učí základní koncepty kybernetické bezpečnosti prostřednictvím strukturovaných modulů. Je nezávislý na dodavatelích a navržený tak, aby byl dokončen v krátkých lekcích (30–60 minut každá).

**Klíčové technologie:**
- Markdown pro obsah
- Docsify pro generování statických stránek
- GitHub Pages pro hosting
- Co-op Translator pro podporu více jazyků (50+ jazyků)
- GitHub Actions pro CI/CD

**Architektura:**
- Vzdělávací obsah organizovaný do 8 hlavních modulů, každý s podlekcemi
- Statická HTML stránka s Docsify, která vykresluje obsah v Markdownu
- Automatizovaný překladový proces pomocí Azure AI služeb
- Pro základní obsah nejsou potřeba žádné nástroje pro sestavení nebo správce balíčků

## Struktura repozitáře

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

## Příkazy pro nastavení

Tento projekt je dokumentační a nevyžaduje instalaci závislostí. Pro práci s obsahem:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Pracovní postup vývoje

### Zobrazení obsahu lokálně

Projekt používá Docsify pro vykreslování. Pro náhled změn:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Struktura obsahu

Moduly jsou číslovány postupně:
- **Modul 1:** Základní koncepty bezpečnosti (1.1–1.7)
- **Modul 2:** Správa identity a přístupu (2.1–2.4)
- **Modul 3:** Síťová bezpečnost (3.1–3.4)
- **Modul 4:** Bezpečnostní operace (4.1–4.4)
- **Modul 5:** Bezpečnost aplikací (5.1–5.3)
- **Modul 6:** Bezpečnost infrastruktury (6.1–6.3)
- **Modul 7:** Bezpečnost dat (7.1–7.3)
- **Modul 8:** Bezpečnost AI (8.1–8.4)

Každý modul končí souborem s kvízem (např. "1.7 End of module quiz.md").

### Úpravy obsahu

1. Upravte soubory Markdown přímo v kořenovém adresáři
2. Dodržujte existující konvenci pojmenování: `[module].[lesson] [Title].md`
3. Aktualizujte tabulku v README.md při přidávání/odstraňování modulů
4. Přidejte obrázky do adresáře `/images/`
5. Odkazujte na obrázky pomocí relativních cest: `![Popis](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.cs.png)`

## Pracovní postup překladu

**Automatizovaný překlad:**
- Překlady jsou automaticky zpracovány pomocí GitHub Action Co-op Translator
- Při odeslání změn do větve `main` workflow přeloží obsah do více než 50 jazyků
- Přeložené soubory jsou uloženy v `/translations/[language_code]/`
- Metadata překladu jsou zachována v YAML frontmatter

**Podporované jazyky:** Arabština, bengálština, bulharština, barmština, čínština (zjednodušená, tradiční), chorvatština, čeština, dánština, nizozemština, estonština, finština, francouzština, němčina, řečtina, hebrejština, hindština, maďarština, indonéština, italština, japonština, korejština, litevština, malajština, maráthština, nepálština, norština, perština, polština, portugalština, pandžábština, rumunština, ruština, srbština, slovenština, slovinština, španělština, svahilština, švédština, tagalog, tamilština, thajština, turečtina, ukrajinština, urdština, vietnamština a další.

**NEUPRAVUJTE ručně překladové soubory** - budou přepsány automatizovaným workflow.

## Pokyny pro styl kódu

### Konvence Markdown

- Používejte standardní syntaxi Markdown
- Nadpisy: Používejte `#` pro hlavní titul, `##` pro sekce, `###` pro podsekce
- Seznamy: Používejte `-` nebo `*` pro nečíslované seznamy, `1.` pro číslované seznamy
- Odkazy: Používejte popisný text s plnými URL GitHubu pro křížové odkazy
- Obrázky: Ukládejte do adresáře `/images/`, používejte popisný alt text
- Bloky kódu: Používejte trojité zpětné uvozovky s identifikátorem jazyka, pokud je to vhodné

### Pokyny pro obsah

- Udržujte lekce zaměřené a stručné (30–60 minut čtení)
- Používejte jasný, přívětivý jazyk pro začátečníky
- Vyhněte se pokynům pro nástroje specifické pro dodavatele (kurikulum je nezávislé na dodavatelích)
- Na začátku každého modulu zahrňte vzdělávací cíle
- Odkazujte na externí zdroje Microsoft Learn, kde je to vhodné
- Zajistěte, aby obsah byl vzdělávací, nikoli propagační

### Pojmenování souborů

- Používejte formát: `[Module].[Lesson] [Title].md`
- Příklad: `1.1 The CIA triad and other key concepts.md`
- Soubory kvízů: `[Module].[Last] End of module quiz.md`
- Používejte mezery v názvech souborů (existující konvence)

## GitHub Workflows

### Co-op Translator (co-op-translator.yml)

**Spouštěč:** Odeslání do větve `main`  
**Účel:** Automaticky překládá nové/upravené soubory Markdown do více než 50 jazyků

**Požadované proměnné prostředí:**
- Přihlašovací údaje Azure AI Service (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Přihlašovací údaje Azure OpenAI (volitelná alternativa)
- Přihlašovací údaje OpenAI (volitelná alternativa)

### Deploy (deploy.yaml)

**Spouštěč:** Odeslání do větve `main` při změně README.md  
**Účel:** Nasazuje statickou stránku na GitHub Pages  
**Výstup:** Aktualizuje stránku GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Spouštěč:** Odeslání do konfigurované větve  
**Účel:** Sestavuje a nasazuje stránku pomocí Jekyll

## Pokyny pro pull requesty

### Před odesláním

1. **Kontrola obsahu:** Zajistěte přesnost a jasnost konceptů kybernetické bezpečnosti
2. **Formátování:** Ověřte, že formátování Markdownu se vykresluje správně
3. **Odkazy:** Otestujte všechny interní a externí odkazy
4. **Obrázky:** Zajistěte, že všechny obrázky se načítají a mají popisný alt text
5. **Konzistence:** Dodržujte existující strukturu a styl obsahu

### Formát názvu PR

Používejte popisné názvy:
- `Add: [Popis nového obsahu]`
- `Update: [Modul/Lekce] - [Stručný popis]`
- `Fix: [Popis problému]`
- `Docs: [Změny v dokumentaci]`

### Požadované kontroly

- Přesnost obsahu (ruční kontrola)
- Validace formátování Markdownu
- Ověření odkazů
- Dokončení workflow překladu (pro sloučení do větve `main`)

### Proces kontroly

1. Vyžaduje se alespoň jedna kontrola od správce
2. Zaměřte se na technickou přesnost konceptů bezpečnosti
3. Ověřte přístupnost a přívětivost pro začátečníky
4. Zajistěte, aby byla zachována neutralita vůči dodavatelům

## Běžné úkoly

### Přidání nové lekce

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

### Aktualizace existujícího obsahu

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Přidání obrázků

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.cs.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testování a validace

### Validace obsahu

Protože se jedná o dokumentační projekt, testování se zaměřuje na:

1. **Vykreslování Markdownu:** Zobrazte změny lokálně pomocí Docsify
2. **Ověření odkazů:** Ručně klikněte na všechny odkazy
3. **Načítání obrázků:** Ověřte, že všechny obrázky se zobrazují správně
4. **Překlad:** Zkontrolujte, že soubory jsou zachyceny workflow překladače (automatizované)
5. **Přístupnost:** Zajistěte správnou hierarchii nadpisů a alt text

### Lokální náhled

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Kontrolní seznam před odesláním

- [ ] Soubory Markdown používají správnou syntaxi
- [ ] Všechny odkazy jsou platné a používají HTTPS, kde je to možné
- [ ] Obrázky mají popisný alt text
- [ ] Obsah je přívětivý pro začátečníky a přesný
- [ ] Je zachována neutralita vůči dodavatelům
- [ ] README.md je aktualizováno při přidávání/odstraňování modulů
- [ ] Pojmenování souborů dodržuje konvence

## Bezpečnostní úvahy

- **Žádná tajemství v obsahu:** Nikdy nekomitujte API klíče, hesla nebo citlivá data
- **Ověření odkazů:** Zajistěte, že všechny externí odkazy vedou na důvěryhodné zdroje
- **Obsah obrázků:** Ověřte, že obrázky neobsahují citlivé informace
- **Workflow překladu:** Používá Azure AI služby s řádnou autentizací
- **SECURITY.md:** Dodržujte proces hlášení zranitelností v SECURITY.md

## Další zdroje

### Související kurzy Microsoftu

Tento kurikulum je součástí širší kolekce vzdělávacích zdrojů Microsoftu:
- Generativní AI pro začátečníky
- AI pro začátečníky
- Data Science pro začátečníky
- ML pro začátečníky
- Web Dev pro začátečníky
- IoT pro začátečníky

### Externí vzdělávací cesty

Po dokončení Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Přispívání

1. **Forkněte repozitář** na GitHubu
2. **Vytvořte větev funkcí** pro své změny
3. **Proveďte změny** podle výše uvedených pokynů
4. **Otestujte lokálně**, aby bylo zajištěno správné vykreslení
5. **Odešlete pull request** s jasným popisem změn
6. **Reagujte na zpětnou vazbu** od správců

## Běžné problémy a řešení

### Překlady nefungují

- Ujistěte se, že změny byly odeslány do větve `main`
- Zkontrolujte stav workflow na kartě GitHub Actions
- Ověřte, že tajemství workflow překladu jsou nakonfigurována
- Překlad probíhá automaticky; nepřepisujte ručně překladové soubory

### Obrázky se nenačítají

- Ověřte, že cesta k obrázku používá lomítka: `images/filename.png`
- Zkontrolujte, zda byl soubor obrázku odeslán do repozitáře
- Ujistěte se, že název souboru obrázku přesně odpovídá (rozlišuje velká/malá písmena)
- Používejte relativní cesty, nikoli absolutní URL

### Docsify se nevykresluje

- Zkontrolujte, zda je v kořenovém adresáři přítomen `index.html`
- Ověřte, že odkazy na CDN Docsify jsou dostupné
- Ujistěte se, že soubory Markdown používají standardní syntaxi
- Zkontrolujte konzoli prohlížeče kvůli chybám JavaScriptu

### Odkazy nefungují

- Používejte plné URL GitHubu pro křížové odkazy mezi lekcemi
- Formát: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testujte odkazy v zobrazeném náhledu, ne pouze v surovém Markdownu

## Údržba projektu

### Pravidelné úkoly

- Kontrola a sloučení příspěvků od komunity
- Aktualizace obsahu pro přesnost, jak se vyvíjí bezpečnostní prostředí
- Monitorování workflow překladu kvůli chybám
- Reakce na problémy a diskuse
- Udržování aktuálnosti externích odkazů

### Správa verzí

- Větev `main` je chráněná a vyžaduje recenze PR
- Všechny změny procházejí procesem pull requestu
- Překladové soubory jsou automaticky generovány, neupravujte je ručně
- Používejte smysluplné zprávy o commitech

## Poznámky pro AI Coding Agents

- **Toto je dokumentační projekt** - zaměřte se na kvalitu obsahu, ne na kód
- **Neupravujte překladové soubory** - jsou automaticky generovány
- **Dodržujte konvence pojmenování souborů** - používejte mezery v názvech souborů podle existujícího vzoru
- **Aktualizujte README.md** při přidávání/odstraňování modulů, aby byla tabulka synchronizována
- **Testujte lokálně** před odesláním PR, aby bylo zajištěno správné vykreslení Markdownu
- **Dodržujte existující styl obsahu** - udržujte přívětivý tón pro začátečníky a neutralitu vůči dodavatelům
- **Není vyžadován proces sestavení** - jednoduchý HTTP server je dostatečný pro lokální vývoj
- **Respektujte strukturu modulů** - každý modul má konzistentní číslování a organizaci

---

**Prohlášení**:  
Tento dokument byl přeložen pomocí služby pro automatický překlad [Co-op Translator](https://github.com/Azure/co-op-translator). Přestože se snažíme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho původním jazyce by měl být považován za autoritativní zdroj. Pro důležité informace doporučujeme profesionální lidský překlad. Neodpovídáme za žádná nedorozumění nebo nesprávné interpretace vyplývající z použití tohoto překladu.