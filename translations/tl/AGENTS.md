<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:41:57+00:00",
  "source_file": "AGENTS.md",
  "language_code": "tl"
}
-->
# AGENTS.md

## Pangkalahatang-ideya ng Proyekto

**Security-101** ay isang kurikulum sa cybersecurity na madaling maunawaan ng mga baguhan na ginawa ng Microsoft. Ang proyekto ay isang dokumentasyon na naglalaman ng mga aralin na nagtuturo ng mga pangunahing konsepto ng cybersecurity sa pamamagitan ng mga nakaayos na module. Ito ay hindi nakadepende sa anumang vendor at idinisenyo upang makumpleto sa maliliit na aralin (30-60 minuto bawat isa).

**Pangunahing Teknolohiya:**
- Markdown para sa nilalaman
- Docsify para sa static site generation
- GitHub Pages para sa hosting
- Co-op Translator para sa suporta sa multi-language (50+ wika)
- GitHub Actions para sa CI/CD

**Arkitektura:**
- Nilalaman pang-edukasyon na nakaayos sa 8 pangunahing module, bawat isa ay may sub-lessons
- Static HTML site gamit ang Docsify para sa pag-render ng Markdown content
- Automated na workflow ng pagsasalin gamit ang Azure AI services
- Walang kinakailangang build tools o package managers para sa pangunahing nilalaman

## Istruktura ng Repository

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

## Mga Command sa Setup

Ito ay isang dokumentasyon na proyekto na walang kailangang i-install na dependencies. Para magtrabaho sa nilalaman:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Workflow ng Pag-develop

### Pagtingin sa Nilalaman Lokal

Ang proyekto ay gumagamit ng Docsify para sa pag-render. Para i-preview ang mga pagbabago:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Istruktura ng Nilalaman

Ang mga module ay nakaayos nang sunod-sunod:
- **Module 1:** Mga pangunahing konsepto sa seguridad (1.1-1.7)
- **Module 2:** Pamamahala ng pagkakakilanlan at access (2.1-2.4)
- **Module 3:** Seguridad ng network (3.1-3.4)
- **Module 4:** Operasyon sa seguridad (4.1-4.4)
- **Module 5:** Seguridad ng aplikasyon (5.1-5.3)
- **Module 6:** Seguridad ng imprastraktura (6.1-6.3)
- **Module 7:** Seguridad ng datos (7.1-7.3)
- **Module 8:** Seguridad ng AI (8.1-8.4)

Ang bawat module ay nagtatapos sa isang quiz file (hal. "1.7 End of module quiz.md").

### Paggawa ng Mga Pagbabago sa Nilalaman

1. I-edit ang mga Markdown file nang direkta sa root directory
2. Sundin ang umiiral na naming convention: `[module].[lesson] [Title].md`
3. I-update ang README.md table kung magdadagdag/magtatanggal ng mga module
4. Magdagdag ng mga larawan sa `/images/` directory
5. I-refer ang mga larawan gamit ang relative paths: `![Description](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.tl.png)`

## Workflow ng Pagsasalin

**Automated na Pagsasalin:**
- Ang mga pagsasalin ay awtomatikong pinangangasiwaan ng Co-op Translator GitHub Action
- Kapag nag-push ka ng mga pagbabago sa `main` branch, ang workflow ay nagsasalin ng nilalaman sa 50+ wika
- Ang mga isinaling file ay nakaimbak sa `/translations/[language_code]/`
- Ang metadata ng pagsasalin ay pinapanatili sa YAML frontmatter

**Mga Suportadong Wika:** Arabic, Bengali, Bulgarian, Burmese, Chinese (Simplified, Traditional), Croatian, Czech, Danish, Dutch, Estonian, Finnish, French, German, Greek, Hebrew, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean, Lithuanian, Malay, Marathi, Nepali, Norwegian, Persian, Polish, Portuguese, Punjabi, Romanian, Russian, Serbian, Slovak, Slovenian, Spanish, Swahili, Swedish, Tagalog, Tamil, Thai, Turkish, Ukrainian, Urdu, Vietnamese, at iba pa.

**Huwag MANUAL na i-edit ang mga isinaling file** - sila ay awtomatikong maa-overwrite ng workflow.

## Mga Alituntunin sa Code Style

### Mga Convention sa Markdown

- Gumamit ng standard na syntax ng Markdown
- Mga Heading: Gumamit ng `#` para sa pangunahing pamagat, `##` para sa mga seksyon, `###` para sa mga subseksyon
- Mga Listahan: Gumamit ng `-` o `*` para sa unordered lists, `1.` para sa ordered lists
- Mga Link: Gumamit ng deskriptibong teksto na may buong GitHub URLs para sa cross-references
- Mga Larawan: I-imbak sa `/images/` directory, gumamit ng deskriptibong alt text
- Mga Code Blocks: Gumamit ng triple backticks na may language identifier kung naaangkop

### Mga Alituntunin sa Nilalaman

- Panatilihing nakatuon at maikli ang mga aralin (30-60 minutong oras ng pagbabasa)
- Gumamit ng malinaw, madaling maunawaan na wika para sa mga baguhan
- Iwasan ang mga tagubilin sa vendor-specific tools (ang kurikulum ay vendor-agnostic)
- Isama ang mga layunin sa pag-aaral sa simula ng bawat module
- Mag-link sa mga panlabas na Microsoft Learn resources kung naaangkop
- Siguraduhing pang-edukasyon ang nilalaman, hindi pang-promosyon

### Paggawa ng Pangalan ng File

- Gumamit ng format: `[Module].[Lesson] [Title].md`
- Halimbawa: `1.1 The CIA triad and other key concepts.md`
- Mga Quiz File: `[Module].[Last] End of module quiz.md`
- Gumamit ng mga espasyo sa filenames (umiiral na convention)

## Mga Workflow sa GitHub

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push sa `main` branch  
**Layunin:** Awtomatikong isinasalin ang mga bagong/na-modify na Markdown file sa 50+ wika

**Kinakailangang Environment Variables:**
- Mga kredensyal ng Azure AI Service (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Mga kredensyal ng Azure OpenAI (opsyonal na alternatibo)
- Mga kredensyal ng OpenAI (opsyonal na alternatibo)

### Deploy (deploy.yaml)

**Trigger:** Push sa `main` branch kapag nagbago ang README.md  
**Layunin:** I-deploy ang static site sa GitHub Pages  
**Output:** Ina-update ang GitHub Pages site

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push sa naka-configure na branch  
**Layunin:** Binubuo at dine-deploy ang site gamit ang Jekyll

## Mga Alituntunin sa Pull Request

### Bago Mag-submit

1. **Review ng Nilalaman:** Siguraduhin ang katumpakan at kalinawan ng mga konsepto sa cybersecurity
2. **Formatting:** I-verify na tama ang Markdown formatting
3. **Mga Link:** Subukan ang lahat ng internal at external na link
4. **Mga Larawan:** Siguraduhin na ang lahat ng larawan ay naglo-load at may deskriptibong alt text
5. **Pagkakapareho:** Sundin ang umiiral na istruktura at estilo ng nilalaman

### Format ng PR Title

Gumamit ng deskriptibong pamagat:
- `Add: [Bagong deskripsyon ng nilalaman]`
- `Update: [Module/Lesson] - [Maikling deskripsyon]`
- `Fix: [Deskripsyon ng isyu]`
- `Docs: [Mga pagbabago sa dokumentasyon]`

### Kinakailangang Mga Pagsusuri

- Katumpakan ng nilalaman (manual na pagsusuri)
- Pag-validate ng Markdown formatting
- Pag-verify ng mga link
- Pagtatapos ng workflow ng pagsasalin (para sa `main` branch merges)

### Proseso ng Review

1. Kinakailangan ang review ng hindi bababa sa isang maintainer
2. Tumutok sa teknikal na katumpakan ng mga konsepto sa seguridad
3. I-verify ang accessibility at pagiging beginner-friendly
4. Siguraduhin na ang neutrality ng vendor ay pinapanatili

## Karaniwang Gawain

### Pagdaragdag ng Bagong Aralin

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

### Pag-update ng Umiiral na Nilalaman

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Pagdaragdag ng Mga Larawan

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.tl.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Pagsusuri at Pag-validate

### Pag-validate ng Nilalaman

Dahil ito ay isang dokumentasyon na proyekto, ang pagsusuri ay nakatuon sa:

1. **Pag-render ng Markdown:** Tingnan ang mga pagbabago lokal gamit ang Docsify
2. **Pag-validate ng Link:** Manu-manong i-click ang lahat ng link
3. **Pag-load ng Larawan:** Siguraduhin na ang lahat ng larawan ay nagpapakita nang tama
4. **Pagsasalin:** Tingnan na ang mga file ay kinukuha ng translator workflow (automated)
5. **Accessibility:** Siguraduhin ang tamang hierarchy ng heading at alt text

### Lokal na Preview

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Checklist Bago Mag-commit

- [ ] Ang mga Markdown file ay gumagamit ng tamang syntax
- [ ] Lahat ng link ay valid at gumagamit ng HTTPS kung maaari
- [ ] Ang mga larawan ay may deskriptibong alt text
- [ ] Ang nilalaman ay beginner-friendly at tama
- [ ] Ang wika ay vendor-neutral
- [ ] Na-update ang README.md kung magdadagdag/magtatanggal ng mga module
- [ ] Ang pangalan ng file ay sumusunod sa mga convention

## Mga Pagsasaalang-alang sa Seguridad

- **Walang mga lihim sa nilalaman:** Huwag kailanman mag-commit ng API keys, passwords, o sensitibong data
- **Pag-validate ng Link:** Siguraduhin na ang lahat ng external na link ay sa mga pinagkakatiwalaang source
- **Nilalaman ng Larawan:** Siguraduhin na ang mga larawan ay walang sensitibong impormasyon
- **Workflow ng Pagsasalin:** Gumagamit ng Azure AI services na may tamang authentication
- **SECURITY.md:** Sundin ang proseso ng pag-uulat ng vulnerability sa SECURITY.md

## Karagdagang Mga Resource

### Kaugnay na Kurso ng Microsoft

Ang kurikulum na ito ay bahagi ng mas malaking koleksyon ng mga educational resources ng Microsoft:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Panlabas na Learning Paths

Pagkatapos makumpleto ang Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Pag-aambag

1. **I-fork ang repository** sa GitHub
2. **Gumawa ng feature branch** para sa iyong mga pagbabago
3. **Gawin ang iyong mga pagbabago** ayon sa mga alituntunin sa itaas
4. **Subukan lokal** upang siguraduhin na tama ang pag-render
5. **Mag-submit ng pull request** na may malinaw na deskripsyon ng mga pagbabago
6. **Tumugon sa feedback** mula sa mga maintainer

## Karaniwang Isyu at Troubleshooting

### Hindi Gumagana ang Pagsasalin

- Siguraduhin na ang mga pagbabago ay na-push sa `main` branch
- Tingnan ang GitHub Actions tab para sa status ng workflow
- I-verify na ang mga secrets ng translation workflow ay naka-configure
- Ang pagsasalin ay awtomatikong nangyayari; huwag manual na i-edit ang mga isinaling file

### Hindi Naglo-load ang Mga Larawan

- I-verify na ang path ng larawan ay gumagamit ng forward slashes: `images/filename.png`
- Tingnan na ang file ng larawan ay na-commit sa repository
- Siguraduhin na ang filename ng larawan ay eksaktong tumutugma (case-sensitive)
- Gumamit ng relative paths, hindi absolute URLs

### Hindi Nagre-render ang Docsify

- Tingnan na ang `index.html` ay nasa root
- I-verify na ang Docsify CDN links ay accessible
- Siguraduhin na ang mga Markdown file ay gumagamit ng standard syntax
- Tingnan ang browser console para sa mga error sa JavaScript

### Hindi Gumagana ang Mga Link

- Gumamit ng buong GitHub URLs para sa cross-references sa pagitan ng mga aralin
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Subukan ang mga link sa rendered view, hindi lang sa raw Markdown

## Pagpapanatili ng Proyekto

### Regular na Gawain

- I-review at i-merge ang mga kontribusyon ng komunidad
- I-update ang nilalaman para sa katumpakan habang nagbabago ang security landscape
- I-monitor ang translation workflow para sa mga error
- Tumugon sa mga isyu at diskusyon
- Panatilihing updated ang mga panlabas na link

### Version Control

- Ang `main` branch ay protektado at nangangailangan ng PR reviews
- Lahat ng pagbabago ay dumadaan sa pull request process
- Ang mga isinaling file ay awtomatikong nabubuo, huwag manual na i-edit
- Gumamit ng makabuluhang commit messages

## Mga Tala para sa AI Coding Agents

- **Ito ay isang dokumentasyon na proyekto** - tumutok sa kalidad ng nilalaman, hindi sa code
- **Huwag i-modify ang mga isinaling file** - sila ay awtomatikong nabubuo
- **Panatilihin ang naming conventions ng file** - gumamit ng mga espasyo sa filenames ayon sa umiiral na pattern
- **I-update ang README.md** kapag nagdadagdag/magtatanggal ng mga module upang panatilihing naka-sync ang table
- **Subukan lokal** bago mag-submit ng PRs upang siguraduhin na tama ang pag-render ng Markdown
- **Sundin ang umiiral na estilo ng nilalaman** - panatilihin ang pagiging beginner-friendly at vendor-neutral na tono
- **Walang kinakailangang build process** - simpleng HTTP server ay sapat para sa lokal na pag-develop
- **Igalang ang istruktura ng module** - ang bawat module ay may pare-parehong numbering at organisasyon

---

**Paunawa**:  
Ang dokumentong ito ay isinalin gamit ang AI translation service na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagama't sinisikap naming maging tumpak, mangyaring tandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga pagkakamali o hindi pagkakatugma. Ang orihinal na dokumento sa kanyang katutubong wika ang dapat ituring na opisyal na sanggunian. Para sa mahalagang impormasyon, inirerekomenda ang propesyonal na pagsasalin ng tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na dulot ng paggamit ng pagsasaling ito.