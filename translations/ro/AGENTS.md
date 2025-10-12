<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:44:30+00:00",
  "source_file": "AGENTS.md",
  "language_code": "ro"
}
-->
# AGENTS.md

## Prezentare Generală a Proiectului

**Security-101** este un curriculum de introducere în securitatea cibernetică creat de Microsoft. Proiectul este o resursă educațională bazată pe documentație, care predă concepte fundamentale de securitate cibernetică prin module structurate. Este independent de furnizor și conceput pentru a fi parcurs în lecții scurte (30-60 minute fiecare).

**Tehnologii Cheie:**
- Markdown pentru conținut
- Docsify pentru generarea site-urilor statice
- GitHub Pages pentru găzduire
- Co-op Translator pentru suport multilingv (50+ limbi)
- GitHub Actions pentru CI/CD

**Arhitectură:**
- Conținut educațional organizat în 8 module principale, fiecare cu sublecții
- Site HTML static cu Docsify pentru redarea conținutului Markdown
- Flux de lucru automatizat pentru traduceri folosind serviciile Azure AI
- Nu sunt necesare instrumente de build sau manageri de pachete pentru conținutul de bază

## Structura Repozitoriului

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

## Comenzi de Configurare

Acesta este un proiect de documentație fără dependențe de instalat. Pentru a lucra cu conținutul:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Flux de Lucru pentru Dezvoltare

### Vizualizarea Conținutului Local

Proiectul folosește Docsify pentru redare. Pentru a previzualiza modificările:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Structura Conținutului

Modulele sunt numerotate secvențial:
- **Modulul 1:** Concepte de bază în securitate (1.1-1.7)
- **Modulul 2:** Managementul identității și accesului (2.1-2.4)
- **Modulul 3:** Securitatea rețelei (3.1-3.4)
- **Modulul 4:** Operațiuni de securitate (4.1-4.4)
- **Modulul 5:** Securitatea aplicațiilor (5.1-5.3)
- **Modulul 6:** Securitatea infrastructurii (6.1-6.3)
- **Modulul 7:** Securitatea datelor (7.1-7.3)
- **Modulul 8:** Securitatea AI (8.1-8.4)

Fiecare modul se încheie cu un fișier de quiz (ex.: "1.7 End of module quiz.md").

### Modificarea Conținutului

1. Editați fișierele Markdown direct în directorul rădăcină
2. Urmați convenția de denumire existentă: `[modul].[lecție] [Titlu].md`
3. Actualizați tabelul din README.md dacă adăugați/eliminați module
4. Adăugați imagini în directorul `/images/`
5. Referiți imaginile folosind căi relative: `![Descriere](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.ro.png)`

## Flux de Lucru pentru Traduceri

**Traducere Automată:**
- Traducerile sunt gestionate automat de acțiunea GitHub Co-op Translator
- Când împingeți modificări în ramura `main`, fluxul de lucru traduce conținutul în 50+ limbi
- Fișierele traduse sunt stocate în `/translations/[language_code]/`
- Metadatele traducerii sunt păstrate în frontmatter YAML

**Limbi Suportate:** Arabă, Bengali, Bulgară, Birmană, Chineză (Simplificată, Tradițională), Croată, Cehă, Daneză, Olandeză, Estonă, Finlandeză, Franceză, Germană, Greacă, Ebraică, Hindi, Maghiară, Indoneziană, Italiană, Japoneză, Coreeană, Lituaniană, Malaeză, Marathi, Nepaleză, Norvegiană, Persană, Poloneză, Portugheză, Punjabi, Română, Rusă, Sârbă, Slovacă, Slovenă, Spaniolă, Swahili, Suedeză, Tagalog, Tamilă, Thailandeză, Turcă, Ucraineană, Urdu, Vietnameză și altele.

**Nu editați manual fișierele traduse** - acestea vor fi suprascrise de fluxul de lucru automatizat.

## Ghiduri de Stil pentru Cod

### Convenții Markdown

- Folosiți sintaxa standard Markdown
- Titluri: Folosiți `#` pentru titlul principal, `##` pentru secțiuni, `###` pentru subsecțiuni
- Liste: Folosiți `-` sau `*` pentru liste neordonate, `1.` pentru liste ordonate
- Linkuri: Folosiți text descriptiv cu URL-uri complete GitHub pentru referințe încrucișate
- Imagini: Stocați în directorul `/images/`, folosiți text alternativ descriptiv
- Blocuri de cod: Folosiți triple backticks cu identificator de limbaj, dacă este cazul

### Ghiduri pentru Conținut

- Păstrați lecțiile concentrate și concise (30-60 minute de citit)
- Folosiți un limbaj clar, prietenos pentru începători
- Evitați instrucțiunile pentru instrumente specifice furnizorilor (curriculumul este independent de furnizor)
- Includeți obiectivele de învățare la începutul fiecărui modul
- Link către resurse externe Microsoft Learn, unde este cazul
- Asigurați-vă că conținutul este educativ, nu promoțional

### Denumirea Fișierelor

- Folosiți formatul: `[Modul].[Lecție] [Titlu].md`
- Exemplu: `1.1 The CIA triad and other key concepts.md`
- Fișiere de quiz: `[Modul].[Ultim] End of module quiz.md`
- Folosiți spații în denumirile fișierelor (convenția existentă)

## Fluxuri de Lucru GitHub

### Co-op Translator (co-op-translator.yml)

**Declanșare:** Push în ramura `main`  
**Scop:** Traduce automat fișierele Markdown noi/modificate în 50+ limbi

**Variabile de Mediu Necesare:**
- Credențiale pentru serviciul Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Credențiale Azure OpenAI (alternativă opțională)
- Credențiale OpenAI (alternativă opțională)

### Deploy (deploy.yaml)

**Declanșare:** Push în ramura `main` când README.md este modificat  
**Scop:** Publică site-ul static pe GitHub Pages  
**Rezultat:** Actualizează site-ul GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Declanșare:** Push în ramura configurată  
**Scop:** Construiește și publică site-ul folosind Jekyll

## Ghiduri pentru Pull Request

### Înainte de Trimitere

1. **Revizuirea Conținutului:** Asigurați acuratețea și claritatea conceptelor de securitate cibernetică
2. **Formatare:** Verificați că formatarea Markdown se redă corect
3. **Linkuri:** Testați toate linkurile interne și externe
4. **Imagini:** Asigurați-vă că toate imaginile se încarcă și au text alternativ descriptiv
5. **Consistență:** Urmați structura și stilul de conținut existent

### Formatul Titlului PR

Folosiți titluri descriptive:
- `Add: [Descriere conținut nou]`
- `Update: [Modul/Lecție] - [Descriere scurtă]`
- `Fix: [Descriere problemă]`
- `Docs: [Modificări documentație]`

### Verificări Necesare

- Acuratețea conținutului (revizuire manuală)
- Validarea formatarei Markdown
- Verificarea linkurilor
- Finalizarea fluxului de lucru pentru traduceri (pentru merge-uri în ramura `main`)

### Procesul de Revizuire

1. Este necesară cel puțin o revizuire de către un maintainer
2. Concentrare pe acuratețea tehnică a conceptelor de securitate
3. Verificarea accesibilității și prieteniei pentru începători
4. Asigurarea neutralității față de furnizori

## Sarcini Comune

### Adăugarea unei Lecții Noi

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

### Actualizarea Conținutului Existent

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Adăugarea Imaginilor

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.ro.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testare și Validare

### Validarea Conținutului

Deoarece acesta este un proiect de documentație, testarea se concentrează pe:

1. **Redarea Markdown:** Vizualizați modificările local folosind Docsify
2. **Validarea Linkurilor:** Accesați manual toate linkurile
3. **Încărcarea Imaginilor:** Verificați că toate imaginile se afișează corect
4. **Traducere:** Verificați că fișierele sunt preluate de fluxul de lucru pentru traduceri (automatizat)
5. **Accesibilitate:** Asigurați o ierarhie corectă a titlurilor și text alternativ pentru imagini

### Previziune Locală

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Lista de Verificare Pre-commit

- [ ] Fișierele Markdown folosesc sintaxa corectă
- [ ] Toate linkurile sunt valide și folosesc HTTPS, unde este posibil
- [ ] Imaginile au text alternativ descriptiv
- [ ] Conținutul este prietenos pentru începători și corect
- [ ] Limbajul neutru față de furnizori este menținut
- [ ] README.md actualizat dacă se adaugă/elimină module
- [ ] Denumirea fișierelor respectă convențiile

## Considerații de Securitate

- **Fără secrete în conținut:** Nu comiteți niciodată chei API, parole sau date sensibile
- **Validarea linkurilor:** Asigurați-vă că toate linkurile externe sunt către surse de încredere
- **Conținutul imaginilor:** Verificați că imaginile nu conțin informații sensibile
- **Fluxul de lucru pentru traduceri:** Folosește serviciile Azure AI cu autentificare corespunzătoare
- **SECURITY.md:** Urmați procesul de raportare a vulnerabilităților din SECURITY.md

## Resurse Suplimentare

### Cursuri Microsoft Asemănătoare

Acest curriculum face parte dintr-o colecție mai mare de resurse educaționale Microsoft:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Căi de Învățare Externe

După finalizarea Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Contribuții

1. **Fork repo-ul** pe GitHub
2. **Creați o ramură de funcționalitate** pentru modificările dvs.
3. **Faceți modificările** urmând ghidurile de mai sus
4. **Testați local** pentru a vă asigura că totul se redă corect
5. **Trimiteți un pull request** cu o descriere clară a modificărilor
6. **Răspundeți la feedback-ul** de la maintainers

## Probleme Comune și Soluționare

### Traducerile Nu Funcționează

- Asigurați-vă că modificările sunt împinse în ramura `main`
- Verificați fila GitHub Actions pentru statusul fluxului de lucru
- Verificați că secretele fluxului de lucru pentru traduceri sunt configurate
- Traducerea se face automat; nu editați manual fișierele traduse

### Imaginile Nu Se Încarcă

- Verificați că calea imaginii folosește slash-uri înainte: `images/filename.png`
- Asigurați-vă că fișierul imaginii este comis în repo
- Verificați că denumirea fișierului imaginii se potrivește exact (case-sensitive)
- Folosiți căi relative, nu URL-uri absolute

### Docsify Nu Se Redă

- Verificați că `index.html` este prezent în rădăcină
- Asigurați-vă că linkurile CDN Docsify sunt accesibile
- Verificați că fișierele Markdown folosesc sintaxa standard
- Verificați consola browserului pentru erori JavaScript

### Linkurile Nu Funcționează

- Folosiți URL-uri complete GitHub pentru referințe încrucișate între lecții
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testați linkurile în vizualizarea redată, nu doar în Markdown brut

## Întreținerea Proiectului

### Sarcini Regulate

- Revizuirea și integrarea contribuțiilor comunității
- Actualizarea conținutului pentru acuratețe pe măsură ce peisajul de securitate evoluează
- Monitorizarea fluxului de lucru pentru traduceri pentru erori
- Răspuns la probleme și discuții
- Menținerea linkurilor externe actualizate

### Controlul Versiunilor

- Ramura `main` este protejată și necesită revizuiri PR
- Toate modificările trec prin procesul de pull request
- Fișierele traduse sunt auto-generate, nu le editați manual
- Folosiți mesaje de commit semnificative

## Note pentru Agenții AI de Codare

- **Acesta este un proiect de documentație** - concentrați-vă pe calitatea conținutului, nu pe cod
- **Nu modificați fișierele traduse** - acestea sunt auto-generate
- **Respectați convențiile de denumire a fișierelor** - folosiți spații în denumiri conform modelului existent
- **Actualizați README.md** când adăugați/eliminați module pentru a menține tabelul sincronizat
- **Testați local** înainte de a trimite PR-uri pentru a vă asigura că Markdown se redă corect
- **Urmați stilul de conținut existent** - mențineți tonul prietenos pentru începători și neutru față de furnizori
- **Nu este necesar un proces de build** - un server HTTP simplu este suficient pentru dezvoltarea locală
- **Respectați structura modulelor** - fiecare modul are o numerotare și organizare consistentă

---

**Declinarea responsabilității**:  
Acest document a fost tradus folosind serviciul de traducere AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim să asigurăm acuratețea, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original în limba sa maternă ar trebui considerat sursa autoritară. Pentru informații critice, se recomandă traducerea profesională realizată de un specialist uman. Nu ne asumăm răspunderea pentru neînțelegerile sau interpretările greșite care pot apărea din utilizarea acestei traduceri.