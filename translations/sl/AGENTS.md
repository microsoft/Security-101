<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:46:45+00:00",
  "source_file": "AGENTS.md",
  "language_code": "sl"
}
-->
# AGENTS.md

## Pregled projekta

**Security-101** je začetnikom prijazna učna vsebina o kibernetski varnosti, ki jo je ustvaril Microsoft. Projekt je dokumentacijski učni vir, ki prek strukturiranih modulov poučuje osnovne koncepte kibernetske varnosti. Je neodvisen od ponudnikov in zasnovan tako, da ga je mogoče dokončati v kratkih lekcijah (30–60 minut vsaka).

**Ključne tehnologije:**
- Markdown za vsebino
- Docsify za generiranje statičnih spletnih strani
- GitHub Pages za gostovanje
- Co-op Translator za podporo več jezikom (50+ jezikov)
- GitHub Actions za CI/CD

**Arhitektura:**
- Izobraževalna vsebina organizirana v 8 glavnih modulov, vsak z več podlekcijami
- Statična HTML stran z Docsify, ki prikazuje vsebino v Markdownu
- Avtomatiziran prevajalski proces z uporabo Azure AI storitev
- Brez potrebnih orodij za gradnjo ali upravljanja paketov za osnovno vsebino

## Struktura repozitorija

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

## Ukazi za nastavitev

To je dokumentacijski projekt brez potrebnih odvisnosti za namestitev. Za delo z vsebino:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Delovni proces razvoja

### Ogled vsebine lokalno

Projekt uporablja Docsify za prikazovanje. Za predogled sprememb:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Struktura vsebine

Moduli so oštevilčeni zaporedno:
- **Modul 1:** Osnovni koncepti varnosti (1.1–1.7)
- **Modul 2:** Upravljanje identitete in dostopa (2.1–2.4)
- **Modul 3:** Omrežna varnost (3.1–3.4)
- **Modul 4:** Operacije varnosti (4.1–4.4)
- **Modul 5:** Varnost aplikacij (5.1–5.3)
- **Modul 6:** Varnost infrastrukture (6.1–6.3)
- **Modul 7:** Varnost podatkov (7.1–7.3)
- **Modul 8:** Varnost umetne inteligence (8.1–8.4)

Vsak modul se zaključi s kvizom (npr. "1.7 End of module quiz.md").

### Spreminjanje vsebine

1. Uredite Markdown datoteke neposredno v korenskem imeniku
2. Upoštevajte obstoječo konvencijo poimenovanja: `[module].[lesson] [Title].md`
3. Posodobite tabelo v README.md, če dodajate ali odstranjujete module
4. Dodajte slike v imenik `/images/`
5. Sklicujte se na slike z relativnimi potmi: `![Opis](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.sl.png)`

## Proces prevajanja

**Avtomatizirano prevajanje:**
- Prevajanje se izvaja samodejno prek GitHub Action Co-op Translator
- Ko potisnete spremembe v vejo `main`, delovni proces prevede vsebino v več kot 50 jezikov
- Prevedene datoteke so shranjene v `/translations/[language_code]/`
- Metapodatki prevodov so ohranjeni v YAML frontmatter

**Podprti jeziki:** Arabščina, Bengalščina, Bolgarščina, Burmanščina, Kitajščina (poenostavljena, tradicionalna), Hrvaščina, Češčina, Danščina, Nizozemščina, Estonščina, Finščina, Francoščina, Nemščina, Grščina, Hebrejščina, Hindijščina, Madžarščina, Indonezijščina, Italijanščina, Japonščina, Korejščina, Litovščina, Malajščina, Maratščina, Nepalščina, Norveščina, Perzijščina, Poljščina, Portugalščina, Pandžabščina, Romunščina, Ruščina, Srbščina, Slovaščina, Slovenščina, Španščina, Svahili, Švedščina, Tagalog, Tamilščina, Tajščina, Turščina, Ukrajinščina, Urdujščina, Vietnamščina in drugi.

**Ne urejajte prevedenih datotek ročno** - te bodo prepisane z avtomatiziranim procesom.

## Smernice za slog kode

### Konvencije za Markdown

- Uporabljajte standardno sintakso Markdown
- Naslovi: Uporabite `#` za glavni naslov, `##` za razdelke, `###` za podrazdelke
- Seznami: Uporabite `-` ali `*` za neurejene sezname, `1.` za urejene sezname
- Povezave: Uporabite opisno besedilo s polnimi GitHub URL-ji za medsebojne povezave
- Slike: Shranite v imenik `/images/`, uporabite opisni alt tekst
- Bloki kode: Uporabite trojne obratne narekovaje z identifikatorjem jezika, kadar je primerno

### Smernice za vsebino

- Naj bodo lekcije osredotočene in jedrnate (30–60 minut branja)
- Uporabljajte jasen, začetnikom prijazen jezik
- Izogibajte se navodilom za orodja določenih ponudnikov (učni načrt je neodvisen od ponudnikov)
- Na začetku vsakega modula vključite učne cilje
- Povezujte se na zunanje vire Microsoft Learn, kjer je primerno
- Poskrbite, da je vsebina izobraževalna, ne promocijska

### Poimenovanje datotek

- Uporabite format: `[Module].[Lesson] [Title].md`
- Primer: `1.1 The CIA triad and other key concepts.md`
- Datoteke kvizov: `[Module].[Last] End of module quiz.md`
- Uporabljajte presledke v imenih datotek (obstoječa konvencija)

## GitHub delovni procesi

### Co-op Translator (co-op-translator.yml)

**Sprožilec:** Potisnite v vejo `main`  
**Namen:** Samodejno prevede nove/spremenjene Markdown datoteke v več kot 50 jezikov

**Potrebne okoljske spremenljivke:**
- Poverilnice za Azure AI storitve (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Poverilnice za Azure OpenAI (neobvezna alternativa)
- Poverilnice za OpenAI (neobvezna alternativa)

### Deploy (deploy.yaml)

**Sprožilec:** Potisnite v vejo `main`, ko se spremeni README.md  
**Namen:** Objavi statično stran na GitHub Pages  
**Izhod:** Posodobi GitHub Pages stran

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Sprožilec:** Potisnite v konfigurirano vejo  
**Namen:** Zgradi in objavi stran z uporabo Jekyll

## Smernice za pull requeste

### Pred oddajo

1. **Pregled vsebine:** Poskrbite za točnost in jasnost konceptov kibernetske varnosti
2. **Oblikovanje:** Preverite, ali se Markdown pravilno prikazuje
3. **Povezave:** Preizkusite vse notranje in zunanje povezave
4. **Slike:** Poskrbite, da se vse slike naložijo in imajo opisni alt tekst
5. **Doslednost:** Upoštevajte obstoječo strukturo in slog vsebine

### Format naslova PR

Uporabite opisne naslove:
- `Add: [Opis nove vsebine]`
- `Update: [Modul/Lekcija] - [Kratek opis]`
- `Fix: [Opis težave]`
- `Docs: [Spremembe dokumentacije]`

### Zahtevani pregledi

- Točnost vsebine (ročni pregled)
- Validacija Markdown oblikovanja
- Preverjanje povezav
- Zaključek prevajalskega procesa (za združitve v vejo `main`)

### Proces pregleda

1. Zahtevan je vsaj en pregled vzdrževalca
2. Osredotočite se na tehnično točnost konceptov varnosti
3. Preverite dostopnost in prijaznost do začetnikov
4. Poskrbite, da se ohranja nevtralnost glede ponudnikov

## Pogoste naloge

### Dodajanje nove lekcije

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

### Posodabljanje obstoječe vsebine

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Dodajanje slik

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.sl.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testiranje in validacija

### Validacija vsebine

Ker gre za dokumentacijski projekt, se testiranje osredotoča na:

1. **Prikaz Markdowna:** Ogled sprememb lokalno z Docsify
2. **Preverjanje povezav:** Ročno kliknite vse povezave
3. **Nalaganje slik:** Preverite, ali se vse slike pravilno prikazujejo
4. **Prevajanje:** Preverite, ali datoteke zazna prevajalski proces (avtomatizirano)
5. **Dostopnost:** Poskrbite za pravilno hierarhijo naslovov in alt tekst

### Lokalni predogled

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Kontrolni seznam pred oddajo

- [ ] Markdown datoteke uporabljajo pravilno sintakso
- [ ] Vse povezave so veljavne in uporabljajo HTTPS, kjer je mogoče
- [ ] Slike imajo opisni alt tekst
- [ ] Vsebina je prijazna začetnikom in točna
- [ ] Nevtralni jezik glede ponudnikov je ohranjen
- [ ] README.md posodobljen, če dodajate/odstranjujete module
- [ ] Poimenovanje datotek sledi konvencijam

## Varnostni vidiki

- **Brez skrivnosti v vsebini:** Nikoli ne vključujte API ključev, gesel ali občutljivih podatkov
- **Validacija povezav:** Poskrbite, da so vse zunanje povezave zaupanja vredne
- **Vsebina slik:** Preverite, da slike ne vsebujejo občutljivih informacij
- **Prevajalski proces:** Uporablja Azure AI storitve z ustrezno avtentikacijo
- **SECURITY.md:** Upoštevajte proces poročanja o ranljivostih v SECURITY.md

## Dodatni viri

### Povezani Microsoft tečaji

Ta učni načrt je del večje zbirke Microsoftovih izobraževalnih virov:
- Generativna umetna inteligenca za začetnike
- Umetna inteligenca za začetnike
- Podatkovna znanost za začetnike
- Strojno učenje za začetnike
- Spletni razvoj za začetnike
- IoT za začetnike

### Zunanji učni načrti

Po zaključku Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Izpit SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Prispevanje

1. **Forkajte repozitorij** na GitHubu
2. **Ustvarite funkcijsko vejo** za svoje spremembe
3. **Izvedite spremembe** v skladu s smernicami zgoraj
4. **Testirajte lokalno**, da se prepričate, da se vse pravilno prikazuje
5. **Oddajte pull request** z jasnim opisom sprememb
6. **Odgovorite na povratne informacije** vzdrževalcev

## Pogoste težave in odpravljanje napak

### Prevajanje ne deluje

- Preverite, ali so spremembe potisnjene v vejo `main`
- Preverite zavihek GitHub Actions za status delovnega procesa
- Preverite, ali so konfigurirane skrivnosti za prevajalski proces
- Prevajanje se izvaja samodejno; ne urejajte prevedenih datotek ročno

### Slike se ne nalagajo

- Preverite, ali pot slike uporablja poševnice: `images/filename.png`
- Preverite, ali je datoteka slike vključena v repozitorij
- Poskrbite, da se ime datoteke slike popolnoma ujema (občutljivo na velike/male črke)
- Uporabljajte relativne poti, ne absolutnih URL-jev

### Docsify ne prikazuje

- Preverite, ali je `index.html` prisoten v korenskem imeniku
- Preverite, ali so Docsify CDN povezave dostopne
- Poskrbite, da datoteke Markdown uporabljajo standardno sintakso
- Preverite konzolo brskalnika za JavaScript napake

### Povezave ne delujejo

- Uporabljajte polne GitHub URL-je za medsebojne povezave med lekcijami
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testirajte povezave v prikazani obliki, ne samo v surovem Markdownu

## Vzdrževanje projekta

### Redne naloge

- Pregled in združevanje prispevkov skupnosti
- Posodabljanje vsebine za točnost glede na razvoj varnostne pokrajine
- Spremljanje prevajalskega procesa za napake
- Odgovarjanje na težave in razprave
- Posodabljanje zunanjih povezav

### Upravljanje različic

- Veja `main` je zaščitena in zahteva preglede PR
- Vse spremembe gredo skozi proces pull requesta
- Prevedene datoteke so samodejno generirane, ne urejajte jih ročno
- Uporabljajte smiselna sporočila ob potrditvi

## Opombe za AI kodirne agente

- **To je dokumentacijski projekt** - osredotočite se na kakovost vsebine, ne na kodo
- **Ne spreminjajte prevedenih datotek** - te so samodejno generirane
- **Ohranite konvencije poimenovanja datotek** - uporabljajte presledke v imenih datotek v skladu z obstoječim vzorcem
- **Posodobite README.md**, ko dodajate/odstranjujete module, da ohranite tabelo sinhronizirano
- **Testirajte lokalno**, preden oddate PR, da se prepričate, da se Markdown pravilno prikazuje
- **Upoštevajte obstoječi slog vsebine** - ohranite začetnikom prijazen, neodvisen ton
- **Ni potrebnega procesa gradnje** - preprost HTTP strežnik je dovolj za lokalni razvoj
- **Spoštujte strukturo modulov** - vsak modul ima dosledno oštevilčenje in organizacijo

---

**Omejitev odgovornosti**:  
Ta dokument je bil preveden z uporabo storitve za prevajanje z umetno inteligenco [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, vas prosimo, da upoštevate, da lahko avtomatski prevodi vsebujejo napake ali netočnosti. Izvirni dokument v njegovem izvirnem jeziku je treba obravnavati kot avtoritativni vir. Za ključne informacije priporočamo profesionalni človeški prevod. Ne prevzemamo odgovornosti za morebitna napačna razumevanja ali napačne interpretacije, ki izhajajo iz uporabe tega prevoda.