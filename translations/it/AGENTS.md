<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:34:23+00:00",
  "source_file": "AGENTS.md",
  "language_code": "it"
}
-->
# AGENTS.md

## Panoramica del Progetto

**Security-101** è un curriculum di cybersecurity per principianti creato da Microsoft. Il progetto è una risorsa di apprendimento basata sulla documentazione che insegna i concetti fondamentali della cybersecurity attraverso moduli strutturati. È indipendente dal fornitore ed è progettato per essere completato in lezioni brevi (30-60 minuti ciascuna).

**Tecnologie Chiave:**
- Markdown per i contenuti
- Docsify per la generazione di siti statici
- GitHub Pages per l'hosting
- Co-op Translator per il supporto multilingue (50+ lingue)
- GitHub Actions per CI/CD

**Architettura:**
- Contenuti educativi organizzati in 8 moduli principali, ciascuno con sottolezioni
- Sito HTML statico con Docsify che rende i contenuti Markdown
- Workflow di traduzione automatizzato utilizzando i servizi Azure AI
- Nessun tool di build o gestore di pacchetti richiesto per i contenuti principali

## Struttura del Repository

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

## Comandi di Configurazione

Questo è un progetto di documentazione senza dipendenze da installare. Per lavorare con i contenuti:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Workflow di Sviluppo

### Visualizzazione dei Contenuti in Locale

Il progetto utilizza Docsify per il rendering. Per visualizzare le modifiche:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Struttura dei Contenuti

I moduli sono numerati in sequenza:
- **Modulo 1:** Concetti base di sicurezza (1.1-1.7)
- **Modulo 2:** Gestione dell'identità e degli accessi (2.1-2.4)
- **Modulo 3:** Sicurezza della rete (3.1-3.4)
- **Modulo 4:** Operazioni di sicurezza (4.1-4.4)
- **Modulo 5:** Sicurezza delle applicazioni (5.1-5.3)
- **Modulo 6:** Sicurezza dell'infrastruttura (6.1-6.3)
- **Modulo 7:** Sicurezza dei dati (7.1-7.3)
- **Modulo 8:** Sicurezza dell'AI (8.1-8.4)

Ogni modulo termina con un file quiz (es. "1.7 End of module quiz.md").

### Modifiche ai Contenuti

1. Modifica direttamente i file Markdown nella directory principale
2. Segui la convenzione di denominazione esistente: `[module].[lesson] [Title].md`
3. Aggiorna la tabella in README.md se aggiungi/rimuovi moduli
4. Aggiungi immagini alla directory `/images/`
5. Riferisci le immagini utilizzando percorsi relativi: `![Descrizione](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.it.png)`

## Workflow di Traduzione

**Traduzione Automatica:**
- Le traduzioni sono gestite automaticamente dall'azione GitHub Co-op Translator
- Quando si spingono modifiche al branch `main`, il workflow traduce i contenuti in 50+ lingue
- I file tradotti sono archiviati in `/translations/[language_code]/`
- I metadati di traduzione sono preservati nel frontmatter YAML

**Lingue Supportate:** Arabo, Bengalese, Bulgaro, Birmano, Cinese (Semplificato, Tradizionale), Croato, Ceco, Danese, Olandese, Estone, Finlandese, Francese, Tedesco, Greco, Ebraico, Hindi, Ungherese, Indonesiano, Italiano, Giapponese, Coreano, Lituano, Malese, Marathi, Nepalese, Norvegese, Persiano, Polacco, Portoghese, Punjabi, Rumeno, Russo, Serbo, Slovacco, Sloveno, Spagnolo, Swahili, Svedese, Tagalog, Tamil, Thai, Turco, Ucraino, Urdu, Vietnamita e altre.

**Non modificare manualmente i file di traduzione** - saranno sovrascritti dal workflow automatico.

## Linee Guida per lo Stile del Codice

### Convenzioni Markdown

- Usa la sintassi standard Markdown
- Intestazioni: Usa `#` per il titolo principale, `##` per le sezioni, `###` per le sottosezioni
- Liste: Usa `-` o `*` per liste non ordinate, `1.` per liste ordinate
- Link: Usa testo descrittivo con URL completi di GitHub per riferimenti incrociati
- Immagini: Archivia nella directory `/images/`, usa testo alternativo descrittivo
- Blocchi di codice: Usa triple backticks con identificatore di linguaggio quando applicabile

### Linee Guida per i Contenuti

- Mantieni le lezioni focalizzate e concise (tempo di lettura 30-60 minuti)
- Usa un linguaggio chiaro e adatto ai principianti
- Evita istruzioni su strumenti specifici del fornitore (il curriculum è indipendente dal fornitore)
- Includi obiettivi di apprendimento all'inizio di ogni modulo
- Collega risorse esterne di Microsoft Learn dove appropriato
- Assicurati che i contenuti siano educativi, non promozionali

### Convenzioni per i Nomi dei File

- Usa il formato: `[Module].[Lesson] [Title].md`
- Esempio: `1.1 The CIA triad and other key concepts.md`
- File quiz: `[Module].[Last] End of module quiz.md`
- Usa spazi nei nomi dei file (convenzione esistente)

## Workflow GitHub

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push al branch `main`  
**Scopo:** Traduce automaticamente i file Markdown nuovi/modificati in 50+ lingue

**Variabili d'Ambiente Necessarie:**
- Credenziali del servizio Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Credenziali Azure OpenAI (alternativa opzionale)
- Credenziali OpenAI (alternativa opzionale)

### Deploy (deploy.yaml)

**Trigger:** Push al branch `main` quando README.md viene modificato  
**Scopo:** Distribuisce il sito statico su GitHub Pages  
**Output:** Aggiorna il sito GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push al branch configurato  
**Scopo:** Costruisce e distribuisce il sito utilizzando Jekyll

## Linee Guida per le Pull Request

### Prima di Inviare

1. **Revisione dei Contenuti:** Assicurati dell'accuratezza e chiarezza dei concetti di cybersecurity
2. **Formattazione:** Verifica che la formattazione Markdown sia corretta
3. **Link:** Testa tutti i link interni ed esterni
4. **Immagini:** Assicurati che tutte le immagini si carichino e abbiano testo alternativo descrittivo
5. **Coerenza:** Segui la struttura e lo stile dei contenuti esistenti

### Formato del Titolo della PR

Usa titoli descrittivi:
- `Add: [Descrizione nuovo contenuto]`
- `Update: [Modulo/Lezione] - [Breve descrizione]`
- `Fix: [Descrizione problema]`
- `Docs: [Modifiche alla documentazione]`

### Controlli Richiesti

- Accuratezza dei contenuti (revisione manuale)
- Validazione della formattazione Markdown
- Verifica dei link
- Completamento del workflow di traduzione (per merge nel branch `main`)

### Processo di Revisione

1. È richiesta almeno una revisione da parte di un manutentore
2. Focus sull'accuratezza tecnica dei concetti di sicurezza
3. Verifica dell'accessibilità e della facilità di comprensione per principianti
4. Assicurati che la neutralità rispetto ai fornitori sia mantenuta

## Attività Comuni

### Aggiungere una Nuova Lezione

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

### Aggiornare Contenuti Esistenti

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Aggiungere Immagini

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.it.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Test e Validazione

### Validazione dei Contenuti

Poiché si tratta di un progetto di documentazione, i test si concentrano su:

1. **Rendering Markdown:** Visualizza le modifiche in locale utilizzando Docsify
2. **Validazione dei Link:** Clicca manualmente su tutti i link
3. **Caricamento Immagini:** Verifica che tutte le immagini siano visualizzate correttamente
4. **Traduzione:** Controlla che i file siano rilevati dal workflow di traduzione (automatica)
5. **Accessibilità:** Assicurati della gerarchia corretta delle intestazioni e del testo alternativo

### Anteprima Locale

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Checklist Pre-commit

- [ ] I file Markdown utilizzano la sintassi corretta
- [ ] Tutti i link sono validi e utilizzano HTTPS ove possibile
- [ ] Le immagini hanno testo alternativo descrittivo
- [ ] I contenuti sono adatti ai principianti e accurati
- [ ] Il linguaggio neutrale rispetto ai fornitori è mantenuto
- [ ] README.md aggiornato se si aggiungono/rimuovono moduli
- [ ] La denominazione dei file segue le convenzioni

## Considerazioni sulla Sicurezza

- **Nessun segreto nei contenuti:** Non commettere mai chiavi API, password o dati sensibili
- **Validazione dei link:** Assicurati che tutti i link esterni siano fonti affidabili
- **Contenuto delle immagini:** Verifica che le immagini non contengano informazioni sensibili
- **Workflow di traduzione:** Utilizza i servizi Azure AI con autenticazione adeguata
- **SECURITY.md:** Segui il processo di segnalazione delle vulnerabilità in SECURITY.md

## Risorse Aggiuntive

### Corsi Microsoft Correlati

Questo curriculum fa parte di una collezione più ampia di risorse educative Microsoft:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Percorsi di Apprendimento Esterni

Dopo aver completato Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Contributi

1. **Forka il repository** su GitHub
2. **Crea un branch di funzionalità** per le tue modifiche
3. **Apporta le modifiche** seguendo le linee guida sopra
4. **Testa in locale** per assicurarti che tutto venga reso correttamente
5. **Invia una pull request** con una descrizione chiara delle modifiche
6. **Rispondi al feedback** dei manutentori

## Problemi Comuni e Risoluzione

### Traduzioni Non Funzionanti

- Assicurati che le modifiche siano spinte al branch `main`
- Controlla la scheda GitHub Actions per lo stato del workflow
- Verifica che i segreti del workflow di traduzione siano configurati
- La traduzione avviene automaticamente; non modificare manualmente i file di traduzione

### Immagini Non Caricate

- Verifica che il percorso dell'immagine utilizzi le barre oblique: `images/filename.png`
- Controlla che il file immagine sia stato commesso nel repository
- Assicurati che il nome del file immagine corrisponda esattamente (case-sensitive)
- Usa percorsi relativi, non URL assoluti

### Docsify Non Funzionante

- Controlla che `index.html` sia presente nella root
- Verifica che i link CDN di Docsify siano accessibili
- Assicurati che i file Markdown utilizzino la sintassi standard
- Controlla la console del browser per errori JavaScript

### Link Non Funzionanti

- Usa URL completi di GitHub per riferimenti incrociati tra lezioni
- Formato: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testa i link nella vista renderizzata, non solo nel Markdown grezzo

## Manutenzione del Progetto

### Attività Regolari

- Revisiona e unisci i contributi della comunità
- Aggiorna i contenuti per garantirne l'accuratezza con l'evoluzione del panorama della sicurezza
- Monitora il workflow di traduzione per errori
- Rispondi a problemi e discussioni
- Mantieni aggiornati i link esterni

### Controllo delle Versioni

- Il branch `main` è protetto e richiede revisioni delle PR
- Tutte le modifiche passano attraverso il processo di pull request
- I file di traduzione sono generati automaticamente, non modificarli manualmente
- Usa messaggi di commit significativi

## Note per gli Agenti AI di Codifica

- **Questo è un progetto di documentazione** - concentrati sulla qualità dei contenuti, non sul codice
- **Non modificare i file di traduzione** - sono generati automaticamente
- **Preserva le convenzioni di denominazione dei file** - usa spazi nei nomi dei file come da modello esistente
- **Aggiorna README.md** quando aggiungi/rimuovi moduli per mantenere la tabella sincronizzata
- **Testa in locale** prima di inviare PR per assicurarti che il Markdown venga reso correttamente
- **Segui lo stile dei contenuti esistenti** - mantieni un tono adatto ai principianti e neutrale rispetto ai fornitori
- **Non è richiesto alcun processo di build** - un semplice server HTTP è sufficiente per lo sviluppo locale
- **Rispetta la struttura dei moduli** - ogni modulo ha una numerazione e un'organizzazione coerente

---

**Clausola di esclusione della responsabilità**:  
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica [Co-op Translator](https://github.com/Azure/co-op-translator). Sebbene ci impegniamo per garantire l'accuratezza, si prega di notare che le traduzioni automatiche possono contenere errori o imprecisioni. Il documento originale nella sua lingua nativa dovrebbe essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda una traduzione professionale effettuata da un traduttore umano. Non siamo responsabili per eventuali incomprensioni o interpretazioni errate derivanti dall'uso di questa traduzione.