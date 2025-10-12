<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:46:13+00:00",
  "source_file": "AGENTS.md",
  "language_code": "hr"
}
-->
# AGENTS.md

## Pregled projekta

**Security-101** je početnički kurikulum za kibernetičku sigurnost koji je kreirao Microsoft. Projekt je edukativni resurs temeljen na dokumentaciji koji poučava osnovne koncepte kibernetičke sigurnosti kroz strukturirane module. Ne ovisi o određenom dobavljaču i osmišljen je za dovršavanje u malim lekcijama (30-60 minuta svaka).

**Ključne tehnologije:**
- Markdown za sadržaj
- Docsify za generiranje statičkih stranica
- GitHub Pages za hosting
- Co-op Translator za podršku više jezika (50+ jezika)
- GitHub Actions za CI/CD

**Arhitektura:**
- Edukativni sadržaj organiziran u 8 glavnih modula, svaki s podlekcijama
- Statička HTML stranica s Docsifyjem za prikaz Markdown sadržaja
- Automatizirani proces prevođenja pomoću Azure AI usluga
- Nisu potrebni alati za izgradnju ili upravitelji paketa za osnovni sadržaj

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

## Komande za postavljanje

Ovo je projekt dokumentacije bez potrebnih ovisnosti za instalaciju. Za rad sa sadržajem:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Radni tijek razvoja

### Pregled sadržaja lokalno

Projekt koristi Docsify za prikaz. Za pregled promjena:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Struktura sadržaja

Moduli su numerirani redoslijedom:
- **Modul 1:** Osnovni koncepti sigurnosti (1.1-1.7)
- **Modul 2:** Upravljanje identitetom i pristupom (2.1-2.4)
- **Modul 3:** Sigurnost mreže (3.1-3.4)
- **Modul 4:** Operacije sigurnosti (4.1-4.4)
- **Modul 5:** Sigurnost aplikacija (5.1-5.3)
- **Modul 6:** Sigurnost infrastrukture (6.1-6.3)
- **Modul 7:** Sigurnost podataka (7.1-7.3)
- **Modul 8:** Sigurnost umjetne inteligencije (8.1-8.4)

Svaki modul završava datotekom kviza (npr. "1.7 End of module quiz.md").

### Izmjene sadržaja

1. Uredite Markdown datoteke izravno u glavnom direktoriju
2. Slijedite postojeću konvenciju imenovanja: `[module].[lesson] [Title].md`
3. Ažurirajte README.md tablicu ako dodajete/uklanjate module
4. Dodajte slike u direktorij `/images/`
5. Referencirajte slike koristeći relativne putanje: `![Opis](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.hr.png)`

## Radni tijek prevođenja

**Automatizirano prevođenje:**
- Prijevodi se automatski obrađuju pomoću Co-op Translator GitHub Action
- Kada pošaljete promjene na granu `main`, radni tijek prevodi sadržaj na 50+ jezika
- Prevedene datoteke pohranjuju se u `/translations/[language_code]/`
- Metapodaci prijevoda čuvaju se u YAML frontmatteru

**Podržani jezici:** arapski, bengalski, bugarski, burmanski, kineski (pojednostavljeni, tradicionalni), hrvatski, češki, danski, nizozemski, estonski, finski, francuski, njemački, grčki, hebrejski, hindi, mađarski, indonezijski, talijanski, japanski, korejski, litvanski, malajski, maratski, nepalski, norveški, perzijski, poljski, portugalski, pandžapski, rumunjski, ruski, srpski, slovački, slovenski, španjolski, svahili, švedski, tagalog, tamilski, tajlandski, turski, ukrajinski, urdu, vijetnamski i drugi.

**Nemojte ručno uređivati datoteke prijevoda** - bit će prepisane automatiziranim radnim tijekom.

## Smjernice za stil koda

### Konvencije za Markdown

- Koristite standardnu Markdown sintaksu
- Naslovi: Koristite `#` za glavni naslov, `##` za sekcije, `###` za podsekcije
- Popisi: Koristite `-` ili `*` za neuređene popise, `1.` za uređene popise
- Linkovi: Koristite opisni tekst s punim GitHub URL-ovima za međusobne reference
- Slike: Pohranite u direktorij `/images/`, koristite opisni alt tekst
- Blokovi koda: Koristite trostruke navodnike s identifikatorom jezika kada je primjenjivo

### Smjernice za sadržaj

- Lekcije neka budu fokusirane i sažete (30-60 minuta čitanja)
- Koristite jasan, početnicima prilagođen jezik
- Izbjegavajte upute za alate specifične za dobavljače (kurikulum je neovisan o dobavljaču)
- Uključite ciljeve učenja na početku svakog modula
- Povežite se na vanjske Microsoft Learn resurse gdje je prikladno
- Osigurajte da sadržaj bude edukativan, a ne promotivan

### Imenovanje datoteka

- Koristite format: `[Module].[Lesson] [Title].md`
- Primjer: `1.1 The CIA triad and other key concepts.md`
- Datoteke kviza: `[Module].[Last] End of module quiz.md`
- Koristite razmake u nazivima datoteka (postojeća konvencija)

## GitHub radni tijekovi

### Co-op Translator (co-op-translator.yml)

**Okidač:** Slanje na granu `main`  
**Svrha:** Automatski prevodi nove/izmijenjene Markdown datoteke na 50+ jezika

**Potrebne varijable okruženja:**
- Azure AI Service vjerodajnice (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI vjerodajnice (opcionalna alternativa)
- OpenAI vjerodajnice (opcionalna alternativa)

### Deploy (deploy.yaml)

**Okidač:** Slanje na granu `main` kada se README.md promijeni  
**Svrha:** Objavljuje statičku stranicu na GitHub Pages  
**Izlaz:** Ažurira GitHub Pages stranicu

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Okidač:** Slanje na konfiguriranu granu  
**Svrha:** Gradi i objavljuje stranicu koristeći Jekyll

## Smjernice za zahtjeve za povlačenje (Pull Request)

### Prije slanja

1. **Pregled sadržaja:** Osigurajte točnost i jasnoću koncepata kibernetičke sigurnosti
2. **Formatiranje:** Provjerite da Markdown formatiranje ispravno prikazuje
3. **Linkovi:** Testirajte sve interne i vanjske linkove
4. **Slike:** Osigurajte da se sve slike učitavaju i imaju opisni alt tekst
5. **Dosljednost:** Slijedite postojeću strukturu i stil sadržaja

### Format naslova PR-a

Koristite opisne naslove:
- `Add: [Opis novog sadržaja]`
- `Update: [Modul/Lekcija] - [Kratki opis]`
- `Fix: [Opis problema]`
- `Docs: [Promjene u dokumentaciji]`

### Potrebne provjere

- Točnost sadržaja (ručna provjera)
- Validacija Markdown formatiranja
- Provjera linkova
- Dovršetak radnog tijeka prevođenja (za spajanje na granu `main`)

### Proces pregleda

1. Potreban je pregled od najmanje jednog održavatelja
2. Fokus na tehničku točnost koncepata sigurnosti
3. Provjera pristupačnosti i prilagođenosti početnicima
4. Osiguranje neutralnosti prema dobavljačima

## Uobičajeni zadaci

### Dodavanje nove lekcije

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

### Ažuriranje postojećeg sadržaja

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Dodavanje slika

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.hr.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testiranje i validacija

### Validacija sadržaja

Budući da je ovo projekt dokumentacije, testiranje se fokusira na:

1. **Prikaz Markdowna:** Pregledajte promjene lokalno koristeći Docsify
2. **Provjera linkova:** Ručno kliknite na sve linkove
3. **Učitavanje slika:** Provjerite da se sve slike ispravno prikazuju
4. **Prijevod:** Provjerite da datoteke preuzima radni tijek prevođenja (automatizirano)
5. **Pristupačnost:** Osigurajte pravilnu hijerarhiju naslova i alt tekst

### Lokalni pregled

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Popis za provjeru prije slanja

- [ ] Markdown datoteke koriste ispravnu sintaksu
- [ ] Svi linkovi su valjani i koriste HTTPS gdje je moguće
- [ ] Slike imaju opisni alt tekst
- [ ] Sadržaj je prilagođen početnicima i točan
- [ ] Neutralan jezik prema dobavljačima je očuvan
- [ ] README.md ažuriran ako se dodaju/uklanjaju moduli
- [ ] Imenovanje datoteka slijedi konvencije

## Sigurnosni aspekti

- **Nema tajni u sadržaju:** Nikada ne šaljite API ključeve, lozinke ili osjetljive podatke
- **Provjera linkova:** Osigurajte da su svi vanjski linkovi pouzdani izvori
- **Sadržaj slika:** Provjerite da slike ne sadrže osjetljive informacije
- **Radni tijek prevođenja:** Koristi Azure AI usluge s ispravnom autentifikacijom
- **SECURITY.md:** Slijedite proces prijave ranjivosti u SECURITY.md

## Dodatni resursi

### Povezani Microsoft tečajevi

Ovaj kurikulum dio je veće kolekcije Microsoft edukativnih resursa:
- Generativna AI za početnike
- AI za početnike
- Data Science za početnike
- ML za početnike
- Web razvoj za početnike
- IoT za početnike

### Vanjski edukativni putovi

Nakon dovršetka Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Ispit SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Doprinos

1. **Forkajte repozitorij** na GitHubu
2. **Kreirajte granu za značajke** za svoje promjene
3. **Napravite promjene** slijedeći gore navedene smjernice
4. **Testirajte lokalno** kako biste osigurali da se sve ispravno prikazuje
5. **Pošaljite zahtjev za povlačenje** s jasnim opisom promjena
6. **Odgovorite na povratne informacije** od održavatelja

## Uobičajeni problemi i rješavanje

### Prijevodi ne rade

- Osigurajte da su promjene poslane na granu `main`
- Provjerite karticu GitHub Actions za status radnog tijeka
- Provjerite da su tajne radnog tijeka prevođenja konfigurirane
- Prijevod se događa automatski; nemojte ručno uređivati datoteke prijevoda

### Slike se ne učitavaju

- Provjerite da put slike koristi kose crte: `images/filename.png`
- Provjerite da je datoteka slike poslana u repozitorij
- Osigurajte da naziv datoteke slike točno odgovara (osjetljivo na velika/mala slova)
- Koristite relativne putanje, ne apsolutne URL-ove

### Docsify ne prikazuje

- Provjerite da je `index.html` prisutan u glavnom direktoriju
- Provjerite da su Docsify CDN linkovi dostupni
- Osigurajte da Markdown datoteke koriste standardnu sintaksu
- Provjerite konzolu preglednika za JavaScript pogreške

### Linkovi ne rade

- Koristite pune GitHub URL-ove za međusobne reference između lekcija
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testirajte linkove u prikazanom pogledu, ne samo u sirovom Markdownu

## Održavanje projekta

### Redoviti zadaci

- Pregled i spajanje doprinosa zajednice
- Ažuriranje sadržaja radi točnosti kako se sigurnosni krajolik razvija
- Praćenje radnog tijeka prevođenja radi pogrešaka
- Odgovaranje na probleme i rasprave
- Ažuriranje vanjskih linkova

### Verzijska kontrola

- Grana `main` je zaštićena i zahtijeva pregled PR-a
- Sve promjene prolaze kroz proces zahtjeva za povlačenje
- Datoteke prijevoda se automatski generiraju, nemojte ih ručno uređivati
- Koristite smislene poruke za commit

## Napomene za AI kodne agente

- **Ovo je projekt dokumentacije** - fokusirajte se na kvalitetu sadržaja, ne na kod
- **Nemojte mijenjati datoteke prijevoda** - automatski se generiraju
- **Očuvajte konvencije imenovanja datoteka** - koristite razmake u nazivima datoteka prema postojećem uzorku
- **Ažurirajte README.md** prilikom dodavanja/uklanjanja modula kako bi tablica bila usklađena
- **Testirajte lokalno** prije slanja PR-a kako biste osigurali da Markdown ispravno prikazuje
- **Slijedite postojeći stil sadržaja** - održavajte ton prilagođen početnicima i neutralan prema dobavljačima
- **Nije potreban proces izgradnje** - jednostavan HTTP poslužitelj dovoljan je za lokalni razvoj
- **Poštujte strukturu modula** - svaki modul ima dosljedno numeriranje i organizaciju

---

**Odricanje od odgovornosti**:  
Ovaj dokument je preveden pomoću AI usluge za prevođenje [Co-op Translator](https://github.com/Azure/co-op-translator). Iako težimo točnosti, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati mjerodavnim izvorom. Za ključne informacije preporučuje se profesionalni prijevod od strane čovjeka. Ne snosimo odgovornost za nesporazume ili pogrešna tumačenja koja proizlaze iz korištenja ovog prijevoda.