<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:47:18+00:00",
  "source_file": "AGENTS.md",
  "language_code": "my"
}
-->
# AGENTS.md

## ပရောဂျက်အကျဉ်းချုပ်

**Security-101** သည် Microsoft မှ စတင်ဖန်တီးထားသော cybersecurity သင်ခန်းစာများကို စတင်လေ့လာသူများအတွက် အထောက်အကူပြုသော သင်ခန်းစာများဖြစ်သည်။ ဒီပရောဂျက်သည် documentation အခြေခံသင်ခန်းစာများဖြစ်ပြီး module များကို စနစ်တကျ ဖွဲ့စည်းထားကာ အခြေခံ cybersecurity အယူအဆများကို သင်ကြားပေးသည်။ vendor-agnostic ဖြစ်ပြီး သင်ခန်းစာတိုင်းကို ၃၀-၆၀ မိနစ်အတွင်း ပြီးစီးနိုင်ရန် ရည်ရွယ်ထားသည်။

**အဓိကနည်းပညာများ:**
- Markdown ကို အကြောင်းအရာအတွက် အသုံးပြုခြင်း
- Docsify ကို static site ဖန်တီးရန် အသုံးပြုခြင်း
- GitHub Pages ကို hosting အတွက် အသုံးပြုခြင်း
- Co-op Translator ကို multi-language အထောက်အပံ့ (၅၀+ ဘာသာစကားများ) အတွက် အသုံးပြုခြင်း
- GitHub Actions ကို CI/CD အတွက် အသုံးပြုခြင်း

**Architecture:**
- သင်ခန်းစာများကို ၈ ခုသော module အဖြစ် စနစ်တကျ ဖွဲ့စည်းထားပြီး sub-lessons ပါဝင်သည်
- Docsify မှ Markdown အကြောင်းအရာကို rendering လုပ်သော static HTML site
- Azure AI services ကို အသုံးပြုသော automated translation workflow
- core content အတွက် build tools သို့မဟုတ် package managers မလိုအပ်ခြင်း

## Repository ဖွဲ့စည်းပုံ

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

## Setup Commands

ဒီပရောဂျက်သည် documentation project ဖြစ်ပြီး dependencies မလိုအပ်ပါ။ အကြောင်းအရာနှင့်အလုပ်လုပ်ရန်:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Development Workflow

### အကြောင်းအရာကို Local မှာ ကြည့်ရှုခြင်း

ဒီပရောဂျက်သည် Docsify ကို rendering အတွက် အသုံးပြုသည်။ ပြင်ဆင်မှုများကို preview လုပ်ရန်:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### အကြောင်းအရာဖွဲ့စည်းပုံ

Modules များကို အနံပါတ်အလိုက် စနစ်တကျ ဖွဲ့စည်းထားသည်:
- **Module 1:** အခြေခံလုံခြုံရေးအယူအဆများ (1.1-1.7)
- **Module 2:** Identity & access management (2.1-2.4)
- **Module 3:** Network security (3.1-3.4)
- **Module 4:** Security operations (4.1-4.4)
- **Module 5:** Application security (5.1-5.3)
- **Module 6:** Infrastructure security (6.1-6.3)
- **Module 7:** Data security (7.1-7.3)
- **Module 8:** AI security (8.1-8.4)

Module တိုင်းသည် quiz ဖိုင်ဖြင့် အဆုံးသတ်သည် (ဥပမာ - "1.7 End of module quiz.md")။

### အကြောင်းအရာပြင်ဆင်မှုများလုပ်ခြင်း

1. Markdown ဖိုင်များကို root directory မှာ တိုက်ရိုက် ပြင်ဆင်ပါ
2. ရှိပြီးသား naming convention ကို လိုက်နာပါ: `[module].[lesson] [Title].md`
3. module များကို ထည့်/ဖျက်လျှင် README.md table ကို update လုပ်ပါ
4. ရုပ်ပုံများကို `/images/` directory ထဲသို့ ထည့်ပါ
5. ရုပ်ပုံများကို relative paths ဖြင့် ရည်ညွှန်းပါ: `![Description](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.my.png)`

## Translation Workflow

**Automated Translation:**
- Co-op Translator GitHub Action မှ translation များကို အလိုအလျောက် လုပ်ဆောင်သည်
- `main` branch သို့ ပြင်ဆင်မှုများ push လုပ်သောအခါ workflow သည် အကြောင်းအရာကို ၅၀+ ဘာသာစကားများသို့ ဘာသာပြန်ပေးသည်
- ဘာသာပြန်ထားသော ဖိုင်များကို `/translations/[language_code]/` တွင် သိမ်းဆည်းထားသည်
- Translation metadata ကို YAML frontmatter တွင် သိမ်းဆည်းထားသည်

**ထောက်ပံ့သော ဘာသာစကားများ:** Arabic, Bengali, Bulgarian, Burmese, Chinese (Simplified, Traditional), Croatian, Czech, Danish, Dutch, Estonian, Finnish, French, German, Greek, Hebrew, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean, Lithuanian, Malay, Marathi, Nepali, Norwegian, Persian, Polish, Portuguese, Punjabi, Romanian, Russian, Serbian, Slovak, Slovenian, Spanish, Swahili, Swedish, Tagalog, Tamil, Thai, Turkish, Ukrainian, Urdu, Vietnamese, နှင့် အခြားများ။

**ဘာသာပြန်ထားသော ဖိုင်များကို လက်ဖြင့် မပြင်ပါ** - အလိုအလျောက် workflow မှ ပြန်လည်ရေးသားမည်။

## Code Style Guidelines

### Markdown Conventions

- စံ Markdown syntax ကို အသုံးပြုပါ
- Headings: `#` ကို main title အတွက် အသုံးပြုပါ၊ `##` ကို sections အတွက်၊ `###` ကို subsections အတွက် အသုံးပြုပါ
- Lists: Unordered lists အတွက် `-` သို့မဟုတ် `*` ကို အသုံးပြုပါ၊ Ordered lists အတွက် `1.` ကို အသုံးပြုပါ
- Links: Descriptive text နှင့် full GitHub URLs ကို cross-references အတွက် အသုံးပြုပါ
- Images: `/images/` directory တွင် သိမ်းဆည်းပြီး descriptive alt text ကို အသုံးပြုပါ
- Code blocks: Triple backticks နှင့် language identifier ကို အသုံးပြုပါ (လိုအပ်ပါက)

### Content Guidelines

- သင်ခန်းစာများကို အချိန်တို (၃၀-၆၀ မိနစ်) အတွင်း ဖတ်ရှုနိုင်အောင် ရှင်းလင်းစွာ ဖွဲ့စည်းပါ
- စတင်လေ့လာသူများအတွက် ရှင်းလင်းသော ဘာသာစကားကို အသုံးပြုပါ
- vendor-specific tool အညွှန်းများကို ရှောင်ရှားပါ (curriculum သည် vendor-agnostic ဖြစ်သည်)
- Module တိုင်း၏အစမှာ learning objectives ထည့်ပါ
- Microsoft Learn resources သို့ ရည်ညွှန်းပါ (လိုအပ်ပါက)
- အကြောင်းအရာသည် ပညာရေးဆိုင်ရာဖြစ်ရမည်၊ promotion မဖြစ်ရပါ

### File Naming

- Format ကို အသုံးပြုပါ: `[Module].[Lesson] [Title].md`
- ဥပမာ: `1.1 The CIA triad and other key concepts.md`
- Quiz ဖိုင်များ: `[Module].[Last] End of module quiz.md`
- Filename များတွင် space အသုံးပြုပါ (ရှိပြီးသား convention)

## GitHub Workflows

### Co-op Translator (co-op-translator.yml)

**Trigger:** `main` branch သို့ push လုပ်သောအခါ  
**Purpose:** Markdown ဖိုင်များကို ၅၀+ ဘာသာစကားများသို့ အလိုအလျောက် ဘာသာပြန်ပေးသည်

**လိုအပ်သော Environment Variables:**
- Azure AI Service credentials (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI credentials (optional alternative)
- OpenAI credentials (optional alternative)

### Deploy (deploy.yaml)

**Trigger:** README.md ပြောင်းလဲမှုများကို `main` branch သို့ push လုပ်သောအခါ  
**Purpose:** Static site ကို GitHub Pages သို့ deploy လုပ်သည်  
**Output:** GitHub Pages site ကို update လုပ်သည်

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Configured branch သို့ push လုပ်သောအခါ  
**Purpose:** Site ကို Jekyll အသုံးပြု၍ build နှင့် deploy လုပ်သည်

## Pull Request Guidelines

### Submit မလုပ်မီ

1. **Content Review:** Cybersecurity အယူအဆများ၏ တိကျမှုနှင့် ရှင်းလင်းမှုကို စစ်ဆေးပါ
2. **Formatting:** Markdown formatting မှန်ကန်စွာ render လုပ်နိုင်မှုကို စစ်ဆေးပါ
3. **Links:** Internal နှင့် external links အားလုံးကို စမ်းသပ်ပါ
4. **Images:** ရုပ်ပုံအားလုံး load လုပ်နိုင်မှုနှင့် descriptive alt text ရှိမှုကို စစ်ဆေးပါ
5. **Consistency:** ရှိပြီးသား content structure နှင့် style ကို လိုက်နာပါ

### PR Title Format

Descriptive title များကို အသုံးပြုပါ:
- `Add: [New content description]`
- `Update: [Module/Lesson] - [Brief description]`
- `Fix: [Issue description]`
- `Docs: [Documentation changes]`

### Required Checks

- Content တိကျမှု (manual review)
- Markdown formatting validation
- Link verification
- Translation workflow ပြီးစီးမှု (for `main` branch merges)

### Review Process

1. Maintainer review အနည်းဆုံး တစ်ခု လိုအပ်သည်
2. Security အယူအဆများ၏ နည်းပညာပိုင်းတိကျမှုကို အဓိကထားပါ
3. Accessibility နှင့် စတင်လေ့လာသူများအတွက် အထောက်အကူပြုမှုကို စစ်ဆေးပါ
4. Vendor neutrality ကို ထိန်းသိမ်းပါ

## Common Tasks

### သင်ခန်းစာအသစ် ထည့်သွင်းခြင်း

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

### ရှိပြီးသားအကြောင်းအရာကို ပြင်ဆင်ခြင်း

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### ရုပ်ပုံများ ထည့်သွင်းခြင်း

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.my.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testing and Validation

### Content Validation

ဒီပရောဂျက်သည် documentation project ဖြစ်သောကြောင့် စမ်းသပ်မှုများသည် အောက်ပါအချက်များကို အဓိကထားသည်:

1. **Markdown Rendering:** Docsify ကို အသုံးပြု၍ ပြင်ဆင်မှုများကို local မှာ ကြည့်ရှုပါ
2. **Link Validation:** Links အားလုံးကို လက်ဖြင့် click လုပ်ပါ
3. **Image Loading:** ရုပ်ပုံအားလုံး ပြသနိုင်မှုကို စစ်ဆေးပါ
4. **Translation:** Translator workflow မှ ဖိုင်များကို စစ်ဆေးပါ (automated)
5. **Accessibility:** Heading hierarchy နှင့် alt text မှန်ကန်မှုကို စစ်ဆေးပါ

### Local Preview

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Pre-commit Checklist

- [ ] Markdown ဖိုင်များသည် မှန်ကန်သော syntax ကို အသုံးပြုထားသည်
- [ ] Links အားလုံးသည် မှန်ကန်ပြီး HTTPS ကို အသုံးပြုထားသည် (လိုအပ်ပါက)
- [ ] Images တွင် descriptive alt text ရှိသည်
- [ ] Content သည် စတင်လေ့လာသူများအတွက် ရှင်းလင်းပြီး တိကျသည်
- [ ] Vendor-neutral ဘာသာစကားကို ထိန်းသိမ်းထားသည်
- [ ] README.md ကို module များထည့်/ဖျက်လျှင် update လုပ်ထားသည်
- [ ] File naming သည် conventions ကို လိုက်နာထားသည်

## Security Considerations

- **Content တွင် လျှို့ဝှက်ချက်များ မပါဝင်ရ:** API keys, passwords, သို့မဟုတ် sensitive data မ commit လုပ်ပါနှင့်
- **Link validation:** External links အားလုံးသည် ယုံကြည်ရသော source များသို့ ရည်ညွှန်းထားမှုကို စစ်ဆေးပါ
- **Image content:** ရုပ်ပုံများတွင် sensitive information မပါဝင်ရ
- **Translation workflow:** Azure AI services ကို သင့်တော်သော authentication ဖြင့် အသုံးပြုသည်
- **SECURITY.md:** SECURITY.md တွင် vulnerability reporting process ကို လိုက်နာပါ

## Additional Resources

### Microsoft သင်ခန်းစာများနှင့် ဆက်စပ်သောအရင်းအမြစ်များ

ဒီ curriculum သည် Microsoft educational resources များ၏ အစိတ်အပိုင်းတစ်ခုဖြစ်သည်:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### အပြင်ပညာရေးလမ်းကြောင်းများ

Security-101 ကို ပြီးစီးပြီးနောက်:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Contributing

1. **GitHub တွင် repository ကို Fork လုပ်ပါ**
2. **Feature branch တစ်ခု** ဖန်တီးပါ
3. **Guidelines များကို လိုက်နာ၍ ပြင်ဆင်မှုများ** ပြုလုပ်ပါ
4. **Local မှာ စမ်းသပ်ပါ** Markdown rendering မှန်ကန်မှုကို စစ်ဆေးရန်
5. **Pull request တင်ပါ** ပြင်ဆင်မှုအကြောင်းအရာကို ရှင်းလင်းစွာ ဖော်ပြပါ
6. **Maintainers မှ ပြန်လည်တုံ့ပြန်မှုများကို ဖြေရှင်းပါ**

## Common Issues and Troubleshooting

### ဘာသာပြန်မှုများ မလုပ်ဆောင်နိုင်ခြင်း

- ပြင်ဆင်မှုများကို `main` branch သို့ push လုပ်ထားပါ
- GitHub Actions tab တွင် workflow status ကို စစ်ဆေးပါ
- Translation workflow secrets များကို configure လုပ်ထားမှုကို စစ်ဆေးပါ
- Translation သည် အလိုအလျောက် လုပ်ဆောင်သည်။ ဘာသာပြန်ထားသော ဖိုင်များကို လက်ဖြင့် မပြင်ပါနှင့်

### ရုပ်ပုံများ မပြသနိုင်ခြင်း

- ရုပ်ပုံ path သည် forward slashes ကို အသုံးပြုထားမှုကို စစ်ဆေးပါ: `images/filename.png`
- ရုပ်ပုံဖိုင်သည် repository တွင် commit လုပ်ထားမှုကို စစ်ဆေးပါ
- ရုပ်ပုံ filename သည် case-sensitive ဖြစ်သောကြောင့် တိကျမှုကို စစ်ဆေးပါ
- Relative paths ကို အသုံးပြုပါ၊ absolute URLs မသုံးပါနှင့်

### Docsify မ render လုပ်နိုင်ခြင်း

- `index.html` သည် root တွင် ရှိမှုကို စစ်ဆေးပါ
- Docsify CDN links သည် အသုံးပြုနိုင်မှုကို စစ်ဆေးပါ
- Markdown ဖိုင်များသည် စံ syntax ကို အသုံးပြုထားမှုကို စစ်ဆေးပါ
- Browser console တွင် JavaScript errors ရှိ/မရှိကို စစ်ဆေးပါ

### Links မလုပ်ဆောင်နိုင်ခြင်း

- Lesson များအကြား cross-references အတွက် full GitHub URLs ကို အသုံးပြုပါ
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Render view တွင် links ကို စမ်းသပ်ပါ၊ raw Markdown တွင်မဟုတ်ပါ

## Project Maintenance

### Regular Tasks

- Community contributions များကို ပြန်လည်သုံးသပ်ပြီး merge လုပ်ပါ
- Security landscape အပြောင်းအလဲများအရ content ကို update လုပ်ပါ
- Translation workflow errors များကို စောင့်ကြည့်ပါ
- Issues နှင့် discussions များကို တုံ့ပြန်ပါ
- External links များကို အချိန်နှင့်တပြေးညီ update လုပ်ပါ

### Version Control

- `main` branch သည် protected ဖြစ်ပြီး PR reviews လိုအပ်သည်
- အပြောင်းအလဲများအားလုံးသည် pull request process မှတဆင့် လုပ်ဆောင်ရမည်
- Translation ဖိုင်များသည် auto-generated ဖြစ်ပြီး လက်ဖြင့် မပြင်ပါနှင့်
- အဓိက commit messages ကို အသုံးပြုပါ

## Notes for AI Coding Agents

- **ဒီပရောဂျက်သည် documentation project ဖြစ်သည်** - code quality မဟုတ်၊ content quality ကို အဓိကထားပါ
- **ဘာသာပြန်ထားသော ဖိုင်များကို မပြင်ပါနှင့်** - အလိုအလျောက် generate လုပ်ထားသည်
- **File naming conventions ကို ထိန်းသိမ်းပါ** - ရှိပြီးသား pattern အတိုင်း space အသုံးပြုပါ
- **README.md ကို update လုပ်ပါ** module များထည့်/ဖျက်လျှင် table ကို sync လုပ်ရန်
- **Local မှာ စမ်းသပ်ပါ** PR တင်မီ Markdown render လုပ်နိုင်မှုကို စစ်ဆေးရန်
- **Content style ကို လိုက်နာပါ** - စတင်လေ့လာသူများအတွက် beginner-friendly, vendor-neutral tone ကို ထိန်းသိမ်းပါ
- **Build process မလိုအပ်ပါ** - local development အတွက် simple HTTP server လုံလောက်သည်
- **Module structure ကို လေးစားပါ** - module တိုင်းသည် အနံပါတ်နှင့် organization တူညီမှုရှိသည်

---

**အကြောင်းကြားချက်**:  
ဤစာရွက်စာတမ်းကို AI ဘာသာပြန်ဝန်ဆောင်မှု [Co-op Translator](https://github.com/Azure/co-op-translator) ကို အသုံးပြု၍ ဘာသာပြန်ထားပါသည်။ ကျွန်ုပ်တို့သည် တိကျမှုအတွက် ကြိုးစားနေသော်လည်း အလိုအလျောက် ဘာသာပြန်မှုများတွင် အမှားများ သို့မဟုတ် မတိကျမှုများ ပါဝင်နိုင်သည်ကို သတိပြုပါ။ မူရင်းဘာသာစကားဖြင့် ရေးသားထားသော စာရွက်စာတမ်းကို အာဏာတရ အရင်းအမြစ်အဖြစ် သတ်မှတ်သင့်ပါသည်။ အရေးကြီးသော အချက်အလက်များအတွက် လူ့ဘာသာပြန်ပညာရှင်များကို အသုံးပြုရန် အကြံပြုပါသည်။ ဤဘာသာပြန်မှုကို အသုံးပြုခြင်းမှ ဖြစ်ပေါ်လာသော အလွဲအမှားများ သို့မဟုတ် အနားယူမှုများအတွက် ကျွန်ုပ်တို့သည် တာဝန်မယူပါ။