<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:42:57+00:00",
  "source_file": "AGENTS.md",
  "language_code": "hu"
}
-->
# AGENTS.md

## Projekt áttekintése

A **Security-101** egy kezdők számára készült kiberbiztonsági tananyag, amelyet a Microsoft hozott létre. A projekt egy dokumentáció-alapú tanulási forrás, amely strukturált modulokon keresztül tanítja meg az alapvető kiberbiztonsági fogalmakat. Ez egy gyártófüggetlen tananyag, amelyet rövid (30-60 perces) leckékben lehet elvégezni.

**Kulcstechnológiák:**
- Markdown a tartalomhoz
- Docsify a statikus weboldal generálásához
- GitHub Pages a tárhelyhez
- Co-op Translator többnyelvű támogatáshoz (50+ nyelv)
- GitHub Actions a CI/CD-hez

**Architektúra:**
- Oktatási tartalom 8 fő modulba szervezve, mindegyik al-leckékkel
- Statikus HTML weboldal, amelyet a Docsify renderel Markdown tartalommal
- Automatikus fordítási munkafolyamat Azure AI szolgáltatásokkal
- Nincs szükség build eszközökre vagy csomagkezelőkre az alapvető tartalomhoz

## Repozitórium szerkezete

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

## Beállítási parancsok

Ez egy dokumentációs projekt, amelyhez nincs szükség függőségek telepítésére. A tartalommal való munkához:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Fejlesztési munkafolyamat

### Tartalom megtekintése helyben

A projekt a Docsify-t használja a rendereléshez. A változtatások előnézetéhez:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Tartalmi struktúra

A modulok számozása sorrendben történik:
- **1. modul:** Alapvető biztonsági fogalmak (1.1-1.7)
- **2. modul:** Identitás- és hozzáférés-kezelés (2.1-2.4)
- **3. modul:** Hálózati biztonság (3.1-3.4)
- **4. modul:** Biztonsági műveletek (4.1-4.4)
- **5. modul:** Alkalmazásbiztonság (5.1-5.3)
- **6. modul:** Infrastruktúra-biztonság (6.1-6.3)
- **7. modul:** Adatbiztonság (7.1-7.3)
- **8. modul:** Mesterséges intelligencia biztonság (8.1-8.4)

Minden modul egy kvíz fájllal zárul (pl. "1.7 Modul végi kvíz.md").

### Tartalom módosítása

1. Szerkessze közvetlenül a gyökérkönyvtárban található Markdown fájlokat
2. Kövesse a meglévő elnevezési konvenciót: `[modul].[lecke] [Cím].md`
3. Frissítse a README.md táblázatot, ha modulokat ad hozzá vagy távolít el
4. Adjon hozzá képeket a `/images/` könyvtárhoz
5. Hivatkozzon a képekre relatív útvonalakkal: `![Leírás](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.hu.png)`

## Fordítási munkafolyamat

**Automatikus fordítás:**
- A fordításokat automatikusan a Co-op Translator GitHub Action kezeli
- Amikor változtatásokat tol fel a `main` ágra, a munkafolyamat lefordítja a tartalmat 50+ nyelvre
- A fordított fájlok a `/translations/[language_code]/` könyvtárban kerülnek tárolásra
- A fordítási metaadatok megmaradnak a YAML frontmatter-ben

**Támogatott nyelvek:** Arab, Bengáli, Bolgár, Burmai, Egyszerűsített és Hagyományos Kínai, Horvát, Cseh, Dán, Holland, Észt, Finn, Francia, Német, Görög, Héber, Hindi, Magyar, Indonéz, Olasz, Japán, Koreai, Litván, Maláj, Maráthi, Nepáli, Norvég, Perzsa, Lengyel, Portugál, Pandzsábi, Román, Orosz, Szerb, Szlovák, Szlovén, Spanyol, Szuahéli, Svéd, Tagalog, Tamil, Thai, Török, Ukrán, Urdu, Vietnámi és még sok más.

**NE szerkessze manuálisan a fordítási fájlokat** - azokat az automatikus munkafolyamat felülírja.

## Kódstílus irányelvek

### Markdown konvenciók

- Használjon szabványos Markdown szintaxist
- Címek: `#` a főcímhez, `##` a szekciókhoz, `###` az alfejezetekhez
- Listák: `-` vagy `*` a felsorolásokhoz, `1.` a számozott listákhoz
- Hivatkozások: Használjon leíró szöveget teljes GitHub URL-ekkel a kereszthivatkozásokhoz
- Képek: Tárolja a `/images/` könyvtárban, használjon leíró alt szöveget
- Kódrészletek: Használjon hármas backtick-et nyelvi azonosítóval, ha szükséges

### Tartalmi irányelvek

- Tartsa a leckéket fókuszáltan és tömören (30-60 perces olvasási idő)
- Használjon világos, kezdőbarát nyelvezetet
- Kerülje a gyártóspecifikus eszközök használati utasításait (a tananyag gyártófüggetlen)
- Minden modul elején tüntesse fel a tanulási célokat
- Hivatkozzon külső Microsoft Learn forrásokra, ahol releváns
- Biztosítsa, hogy a tartalom oktató jellegű, ne promóciós

### Fájlnév konvenciók

- Formátum: `[Modul].[Lecke] [Cím].md`
- Példa: `1.1 A CIA triász és más kulcsfogalmak.md`
- Kvíz fájlok: `[Modul].[Utolsó] Modul végi kvíz.md`
- Használjon szóközöket a fájlnevekben (meglévő konvenció szerint)

## GitHub munkafolyamatok

### Co-op Translator (co-op-translator.yml)

**Indítás:** Push a `main` ágra  
**Cél:** Új/módosított Markdown fájlok automatikus fordítása 50+ nyelvre

**Szükséges környezeti változók:**
- Azure AI Service hitelesítési adatok (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI hitelesítési adatok (opcionális alternatíva)
- OpenAI hitelesítési adatok (opcionális alternatíva)

### Telepítés (deploy.yaml)

**Indítás:** Push a `main` ágra, ha a README.md módosul  
**Cél:** Statikus weboldal telepítése a GitHub Pages-re  
**Kimenet:** A GitHub Pages weboldal frissítése

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Indítás:** Push a konfigurált ágra  
**Cél:** Weboldal építése és telepítése Jekyll segítségével

## Pull Request irányelvek

### Beküldés előtt

1. **Tartalom ellenőrzése:** Győződjön meg a kiberbiztonsági fogalmak pontosságáról és érthetőségéről
2. **Formázás:** Ellenőrizze, hogy a Markdown formázás helyesen jelenik-e meg
3. **Hivatkozások:** Tesztelje az összes belső és külső hivatkozást
4. **Képek:** Győződjön meg róla, hogy minden kép betöltődik, és van leíró alt szövege
5. **Konzisztencia:** Kövesse a meglévő tartalmi struktúrát és stílust

### PR cím formátuma

Használjon leíró címeket:
- `Hozzáadás: [Új tartalom leírása]`
- `Frissítés: [Modul/Lecke] - [Rövid leírás]`
- `Javítás: [Probléma leírása]`
- `Dokumentáció: [Dokumentációs változások]`

### Szükséges ellenőrzések

- Tartalom pontossága (kézi ellenőrzés)
- Markdown formázás ellenőrzése
- Hivatkozások ellenőrzése
- Fordítási munkafolyamat befejezése (`main` ágra történő egyesítés esetén)

### Felülvizsgálati folyamat

1. Legalább egy karbantartói felülvizsgálat szükséges
2. A kiberbiztonsági fogalmak technikai pontosságára összpontosítson
3. Ellenőrizze az akadálymentességet és a kezdőbarát jelleget
4. Biztosítsa a gyártófüggetlenség fenntartását

## Gyakori feladatok

### Új lecke hozzáadása

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

### Meglévő tartalom frissítése

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Képek hozzáadása

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.hu.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Tesztelés és érvényesítés

### Tartalom érvényesítése

Mivel ez egy dokumentációs projekt, a tesztelés az alábbiakra összpontosít:

1. **Markdown megjelenítés:** Nézze meg a változtatásokat helyben a Docsify segítségével
2. **Hivatkozások ellenőrzése:** Kattintson végig manuálisan az összes hivatkozáson
3. **Képek betöltése:** Ellenőrizze, hogy minden kép helyesen jelenik meg
4. **Fordítás:** Ellenőrizze, hogy a fájlokat a fordító munkafolyamat felismeri-e (automatikus)
5. **Akadálymentesség:** Biztosítsa a megfelelő címsor hierarchiát és az alt szövegeket

### Helyi előnézet

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Előzetes ellenőrző lista

- [ ] A Markdown fájlok helyes szintaxist használnak
- [ ] Minden hivatkozás érvényes, és lehetőség szerint HTTPS-t használ
- [ ] A képeknek van leíró alt szövege
- [ ] A tartalom kezdőbarát és pontos
- [ ] A gyártófüggetlen nyelvezet megmarad
- [ ] A README.md frissítve van, ha modulokat ad hozzá vagy távolít el
- [ ] A fájlnevek megfelelnek a konvencióknak

## Biztonsági szempontok

- **Nincsenek titkos adatok a tartalomban:** Soha ne kövessen el API kulcsokat, jelszavakat vagy érzékeny adatokat
- **Hivatkozások ellenőrzése:** Győződjön meg róla, hogy minden külső hivatkozás megbízható forrásra mutat
- **Képtartalom:** Ellenőrizze, hogy a képek nem tartalmaznak érzékeny információkat
- **Fordítási munkafolyamat:** Az Azure AI szolgáltatásokat megfelelő hitelesítéssel használja
- **SECURITY.md:** Kövesse a SECURITY.md-ben leírt sebezhetőségi jelentési folyamatot

## További források

### Kapcsolódó Microsoft tanfolyamok

Ez a tananyag a Microsoft oktatási forrásainak szélesebb gyűjteményének része:
- Generatív MI kezdőknek
- MI kezdőknek
- Adattudomány kezdőknek
- Gépi tanulás kezdőknek
- Webfejlesztés kezdőknek
- IoT kezdőknek

### Külső tanulási utak

A Security-101 elvégzése után:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [SC-900 vizsga: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Hozzájárulás

1. **Forkolja a repozitóriumot** a GitHubon
2. **Hozzon létre egy új ágat** a változtatásokhoz
3. **Végezze el a változtatásokat** a fentiekben leírt irányelvek szerint
4. **Tesztelje helyben**, hogy minden helyesen jelenik-e meg
5. **Nyújtson be egy pull requestet** a változtatások világos leírásával
6. **Válaszoljon a karbantartók visszajelzéseire**

## Gyakori problémák és hibaelhárítás

### A fordítások nem működnek

- Győződjön meg róla, hogy a változtatások a `main` ágra lettek feltöltve
- Ellenőrizze a GitHub Actions fülön a munkafolyamat állapotát
- Ellenőrizze, hogy a fordítási munkafolyamat titkai megfelelően vannak-e konfigurálva
- A fordítás automatikusan történik; ne szerkessze manuálisan a fordítási fájlokat

### Képek nem töltődnek be

- Ellenőrizze, hogy a kép útvonala előre mutató perjeleket használ: `images/filename.png`
- Ellenőrizze, hogy a kép fájlja el lett-e mentve a repozitóriumba
- Győződjön meg róla, hogy a kép fájlneve pontosan megegyezik (kis- és nagybetű érzékeny)
- Használjon relatív útvonalakat, ne abszolút URL-eket

### A Docsify nem renderel

- Ellenőrizze, hogy az `index.html` jelen van-e a gyökérben
- Győződjön meg róla, hogy a Docsify CDN linkek elérhetők
- Ellenőrizze, hogy a Markdown fájlok szabványos szintaxist használnak
- Nézze meg a böngésző konzolját JavaScript hibákért

### Hivatkozások nem működnek

- Használjon teljes GitHub URL-eket a leckék közötti kereszthivatkozásokhoz
- Formátum: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Tesztelje a hivatkozásokat a renderelt nézetben, ne csak a nyers Markdown-ban

## Projekt karbantartás

### Rendszeres feladatok

- Közösségi hozzájárulások átnézése és egyesítése
- Tartalom frissítése a biztonsági környezet változásainak megfelelően
- A fordítási munkafolyamat hibáinak figyelése
- Kérdésekre és megbeszélésekre való válaszadás
- Külső hivatkozások naprakészen tartása

### Verziókezelés

- A `main` ág védett, és pull request felülvizsgálatot igényel
- Minden változtatás pull request folyamaton keresztül történik
- A fordítási fájlok automatikusan generálódnak, ne szerkessze őket manuálisan
- Használjon érthető commit üzeneteket

## Megjegyzések AI kódoló ügynökök számára

- **Ez egy dokumentációs projekt** - a tartalom minőségére összpontosítson, ne a kódra
- **Ne módosítsa a fordítási fájlokat** - ezek automatikusan generálódnak
- **Tartsa be a fájlnév konvenciókat** - használjon szóközöket a fájlnevekben a meglévő minta szerint
- **Frissítse a README.md-t**, ha modulokat ad hozzá vagy távolít el, hogy a táblázat szinkronban maradjon
- **Tesztelje helyben** a PR-ek benyújtása előtt, hogy a Markdown helyesen jelenik-e meg
- **Kövesse a meglévő tartalmi stílust** - tartsa meg a kezdőbarát, gyártófüggetlen hangnemet
- **Nincs szükség build folyamatra** - egyszerű HTTP szerver elegendő a helyi fejlesztéshez
- **Tartsa be a modulstruktúrát** - minden modulnak következetes számozása és szervezése van

---

**Felelősség kizárása**:  
Ez a dokumentum az [Co-op Translator](https://github.com/Azure/co-op-translator) AI fordítási szolgáltatás segítségével került lefordításra. Bár törekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti dokumentum az eredeti nyelvén tekintendő hiteles forrásnak. Kritikus információk esetén javasolt professzionális emberi fordítást igénybe venni. Nem vállalunk felelősséget semmilyen félreértésért vagy téves értelmezésért, amely a fordítás használatából eredhet.