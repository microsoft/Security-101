<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:32:45+00:00",
  "source_file": "AGENTS.md",
  "language_code": "pa"
}
-->
# AGENTS.md

## ਪ੍ਰੋਜੈਕਟ ਝਲਕ

**Security-101** ਮਾਈਕਰੋਸਾਫਟ ਦੁਆਰਾ ਬਣਾਇਆ ਗਿਆ ਇੱਕ ਸ਼ੁਰੂਆਤੀ-ਮਿਤਰਵਾਨ ਸਾਇਬਰਸੁਰੱਖਿਆ ਪਾਠਕ੍ਰਮ ਹੈ। ਇਹ ਪ੍ਰੋਜੈਕਟ ਇੱਕ ਦਸਤਾਵੇਜ਼-ਅਧਾਰਿਤ ਸਿੱਖਣ ਸਰੋਤ ਹੈ ਜੋ ਢਾਂਚੇਬੱਧ ਮੋਡੀਊਲਾਂ ਰਾਹੀਂ ਮੂਲ ਸਾਇਬਰਸੁਰੱਖਿਆ ਧਾਰਨਾਵਾਂ ਸਿਖਾਉਂਦਾ ਹੈ। ਇਹ ਵਿਕਰੇਤਾ-ਤਟਸਥ ਹੈ ਅਤੇ ਛੋਟੇ ਪਾਠਾਂ (30-60 ਮਿੰਟ ਹਰ ਇੱਕ) ਵਿੱਚ ਪੂਰਾ ਕਰਨ ਲਈ ਡਿਜ਼ਾਈਨ ਕੀਤਾ ਗਿਆ ਹੈ।

**ਮੁੱਖ ਤਕਨਾਲੋਜੀਆਂ:**
- ਸਮੱਗਰੀ ਲਈ Markdown
- Docsify ਸਥਿਰ ਸਾਈਟ ਜਨਰੇਸ਼ਨ ਲਈ
- GitHub Pages ਹੋਸਟਿੰਗ ਲਈ
- Co-op Translator ਬਹੁ-ਭਾਸ਼ਾ ਸਹਾਇਤਾ ਲਈ (50+ ਭਾਸ਼ਾਵਾਂ)
- GitHub Actions CI/CD ਲਈ

**ਆਰਕੀਟੈਕਚਰ:**
- ਸਿੱਖਣ ਸਮੱਗਰੀ 8 ਮੁੱਖ ਮੋਡੀਊਲਾਂ ਵਿੱਚ ਵਿਵਸਥਿਤ ਕੀਤੀ ਗਈ ਹੈ, ਹਰ ਇੱਕ ਵਿੱਚ ਉਪ-ਪਾਠ ਹਨ
- Docsify ਦੁਆਰਾ Markdown ਸਮੱਗਰੀ ਰੇਂਡਰ ਕਰਨ ਵਾਲੀ ਸਥਿਰ HTML ਸਾਈਟ
- Azure AI ਸੇਵਾਵਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਆਟੋਮੈਟਿਕ ਅਨੁਵਾਦ ਵਰਕਫਲੋ
- ਮੁੱਖ ਸਮੱਗਰੀ ਲਈ ਕੋਈ ਬਿਲਡ ਟੂਲ ਜਾਂ ਪੈਕੇਜ ਮੈਨੇਜਰ ਦੀ ਲੋੜ ਨਹੀਂ

## ਰਿਪੋਜ਼ਟਰੀ ਸਟ੍ਰਕਚਰ

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

## ਸੈਟਅੱਪ ਕਮਾਂਡਸ

ਇਹ ਇੱਕ ਦਸਤਾਵੇਜ਼ ਪ੍ਰੋਜੈਕਟ ਹੈ ਜਿਸ ਵਿੱਚ ਕੋਈ ਨਿਰਭਰਤਾਵਾਂ ਇੰਸਟਾਲ ਕਰਨ ਦੀ ਲੋੜ ਨਹੀਂ। ਸਮੱਗਰੀ ਨਾਲ ਕੰਮ ਕਰਨ ਲਈ:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## ਵਿਕਾਸ ਵਰਕਫਲੋ

### ਸਮੱਗਰੀ ਨੂੰ ਸਥਾਨਕ ਤੌਰ 'ਤੇ ਦੇਖਣਾ

ਪ੍ਰੋਜੈਕਟ Docsify ਦੀ ਵਰਤੋਂ ਕਰਦਾ ਹੈ। ਬਦਲਾਅ ਨੂੰ ਪ੍ਰੀਵਿਊ ਕਰਨ ਲਈ:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### ਸਮੱਗਰੀ ਸਟ੍ਰਕਚਰ

ਮੋਡੀਊਲਾਂ ਨੂੰ ਲਗਾਤਾਰ ਗਿਣਤੀ ਵਿੱਚ ਨੰਬਰ ਦਿੱਤਾ ਗਿਆ ਹੈ:
- **ਮੋਡੀਊਲ 1:** ਮੂਲ ਸੁਰੱਖਿਆ ਧਾਰਨਾਵਾਂ (1.1-1.7)
- **ਮੋਡੀਊਲ 2:** ਪਹਿਚਾਣ ਅਤੇ ਪਹੁੰਚ ਪ੍ਰਬੰਧਨ (2.1-2.4)
- **ਮੋਡੀਊਲ 3:** ਨੈਟਵਰਕ ਸੁਰੱਖਿਆ (3.1-3.4)
- **ਮੋਡੀਊਲ 4:** ਸੁਰੱਖਿਆ ਕਾਰਵਾਈਆਂ (4.1-4.4)
- **ਮੋਡੀਊਲ 5:** ਐਪਲੀਕੇਸ਼ਨ ਸੁਰੱਖਿਆ (5.1-5.3)
- **ਮੋਡੀਊਲ 6:** ਢਾਂਚਾ ਸੁਰੱਖਿਆ (6.1-6.3)
- **ਮੋਡੀਊਲ 7:** ਡਾਟਾ ਸੁਰੱਖਿਆ (7.1-7.3)
- **ਮੋਡੀਊਲ 8:** AI ਸੁਰੱਖਿਆ (8.1-8.4)

ਹਰ ਮੋਡੀਊਲ ਇੱਕ ਕਵਿਜ ਫਾਈਲ ਨਾਲ ਖਤਮ ਹੁੰਦਾ ਹੈ (ਜਿਵੇਂ, "1.7 End of module quiz.md")।

### ਸਮੱਗਰੀ ਵਿੱਚ ਬਦਲਾਅ ਕਰਨਾ

1. ਮੂਲ ਡਾਇਰੈਕਟਰੀ ਵਿੱਚ Markdown ਫਾਈਲਾਂ ਨੂੰ ਸਿੱਧੇ ਤੌਰ 'ਤੇ ਸੋਧੋ
2. ਮੌਜੂਦਾ ਨਾਮਕਰਨ ਰੀਤੀ ਦੀ ਪਾਲਣਾ ਕਰੋ: `[module].[lesson] [Title].md`
3. ਜੇ ਮੋਡੀਊਲ ਜੋੜ/ਹਟਾ ਰਹੇ ਹੋ ਤਾਂ README.md ਟੇਬਲ ਨੂੰ ਅਪਡੇਟ ਕਰੋ
4. ਚਿੱਤਰ `/images/` ਡਾਇਰੈਕਟਰੀ ਵਿੱਚ ਜੋੜੋ
5. ਚਿੱਤਰਾਂ ਨੂੰ ਸੰਬੰਧਿਤ ਪਾਥਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਦਰਸਾਓ: `![Description](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.pa.png)`

## ਅਨੁਵਾਦ ਵਰਕਫਲੋ

**ਆਟੋਮੈਟਿਕ ਅਨੁਵਾਦ:**
- ਅਨੁਵਾਦ Co-op Translator GitHub Action ਦੁਆਰਾ ਆਟੋਮੈਟਿਕ ਤੌਰ 'ਤੇ ਸੰਭਾਲੇ ਜਾਂਦੇ ਹਨ
- ਜਦੋਂ ਤੁਸੀਂ `main` ਸ਼ਾਖਾ ਵਿੱਚ ਬਦਲਾਅ ਪੇਸ਼ ਕਰਦੇ ਹੋ, ਵਰਕਫਲੋ ਸਮੱਗਰੀ ਨੂੰ 50+ ਭਾਸ਼ਾਵਾਂ ਵਿੱਚ ਅਨੁਵਾਦ ਕਰਦਾ ਹੈ
- ਅਨੁਵਾਦ ਕੀਤੀਆਂ ਫਾਈਲਾਂ `/translations/[language_code]/` ਵਿੱਚ ਸਟੋਰ ਕੀਤੀਆਂ ਜਾਂਦੀਆਂ ਹਨ
- YAML ਫਰੰਟਮੈਟਰ ਵਿੱਚ ਅਨੁਵਾਦ ਮੈਟਾਡੇਟਾ ਸੁਰੱਖਿਅਤ ਕੀਤਾ ਜਾਂਦਾ ਹੈ

**ਸਹਾਇਕ ਭਾਸ਼ਾਵਾਂ:** ਅਰਬੀ, ਬੰਗਾਲੀ, ਬੁਲਗਾਰੀਆਈ, ਬਰਮੀ, ਚੀਨੀ (ਸਰਲ, ਰਵਾਇਤੀ), ਕਰੋਏਸ਼ੀਆਈ, ਚੈੱਕ, ਡੈਨਿਸ਼, ਡੱਚ, ਐਸਟੋਨੀਆਈ, ਫਿਨਿਸ਼, ਫਰੈਂਚ, ਜਰਮਨ, ਗ੍ਰੀਕ, ਹਿਬਰੂ, ਹਿੰਦੀ, ਹੰਗਰੀਆਈ, ਇੰਡੋਨੇਸ਼ੀਆਈ, ਇਟਾਲੀਅਨ, ਜਪਾਨੀ, ਕੋਰੀਆਈ, ਲਿਥੂਆਨੀਅਨ, ਮਲੇ, ਮਰਾਠੀ, ਨੇਪਾਲੀ, ਨਾਰਵੇਜੀਅਨ, ਫਾਰਸੀ, ਪੋਲਿਸ਼, ਪੁਰਤਗਾਲੀ, ਪੰਜਾਬੀ, ਰੋਮਾਨੀਆਈ, ਰੂਸੀ, ਸਰਬੀਆਈ, ਸਲੋਵਾਕ, ਸਲੋਵੇਨੀਆਈ, ਸਪੈਨਿਸ਼, ਸਵਾਹਿਲੀ, ਸਵੀਡਿਸ਼, ਟੈਗਾਲੋਗ, ਤਮਿਲ, ਥਾਈ, ਤੁਰਕੀ, ਯੂਕਰੇਨੀ, ਉਰਦੂ, ਵੀਅਤਨਾਮੀ, ਅਤੇ ਹੋਰ।

**ਅਨੁਵਾਦ ਫਾਈਲਾਂ ਨੂੰ ਹੱਥੋਂ ਸੋਧ ਨਾ ਕਰੋ** - ਇਹਨਾਂ ਨੂੰ ਆਟੋਮੈਟਿਕ ਵਰਕਫਲੋ ਦੁਆਰਾ ਓਵਰਰਾਈਟ ਕੀਤਾ ਜਾਵੇਗਾ।

## ਕੋਡ ਸਟਾਈਲ ਗਾਈਡਲਾਈਨਸ

### Markdown ਰੀਤੀਆਂ

- ਸਧਾਰਨ Markdown ਸਿੰਟੈਕਸ ਦੀ ਵਰਤੋਂ ਕਰੋ
- ਸਿਰਲੇਖ: ਮੁੱਖ ਸਿਰਲੇਖ ਲਈ `#`, ਸੈਕਸ਼ਨ ਲਈ `##`, ਉਪ-ਸੈਕਸ਼ਨ ਲਈ `###` ਦੀ ਵਰਤੋਂ ਕਰੋ
- ਸੂਚੀਆਂ: ਅਨੁਕ੍ਰਮਿਤ ਸੂਚੀਆਂ ਲਈ `-` ਜਾਂ `*`, ਕ੍ਰਮਬੱਧ ਸੂਚੀਆਂ ਲਈ `1.` ਦੀ ਵਰਤੋਂ ਕਰੋ
- ਲਿੰਕ: ਵਰਣਨਾਤਮਕ ਪਾਠ ਨਾਲ ਪੂਰੇ GitHub URLs ਦੀ ਵਰਤੋਂ ਕਰੋ
- ਚਿੱਤਰ: `/images/` ਡਾਇਰੈਕਟਰੀ ਵਿੱਚ ਸਟੋਰ ਕਰੋ, ਵਰਣਨਾਤਮਕ alt ਪਾਠ ਦੀ ਵਰਤੋਂ ਕਰੋ
- ਕੋਡ ਬਲਾਕ: ਜਿੱਥੇ ਲਾਗੂ ਹੋਵੇ, ਤਿੰਨ ਬੈਕਟਿਕਸ ਨਾਲ ਭਾਸ਼ਾ ਪਛਾਣਕਰਤਾ ਦੀ ਵਰਤੋਂ ਕਰੋ

### ਸਮੱਗਰੀ ਗਾਈਡਲਾਈਨਸ

- ਪਾਠਾਂ ਨੂੰ ਕੇਂਦਰਿਤ ਅਤੇ ਸੰਖੇਪ ਰੱਖੋ (30-60 ਮਿੰਟ ਪੜ੍ਹਨ ਦਾ ਸਮਾਂ)
- ਸਪਸ਼ਟ, ਸ਼ੁਰੂਆਤੀ-ਮਿਤਰਵਾਨ ਭਾਸ਼ਾ ਦੀ ਵਰਤੋਂ ਕਰੋ
- ਵਿਕਰੇਤਾ-ਵਿਸ਼ੇਸ਼ ਟੂਲ ਨਿਰਦੇਸ਼ਾਂ ਤੋਂ ਬਚੋ (ਪਾਠਕ੍ਰਮ ਵਿਕਰੇਤਾ-ਤਟਸਥ ਹੈ)
- ਹਰ ਮੋਡੀਊਲ ਦੇ ਸ਼ੁਰੂ ਵਿੱਚ ਸਿੱਖਣ ਦੇ ਉਦੇਸ਼ ਸ਼ਾਮਲ ਕਰੋ
- ਜਿੱਥੇ ਲਾਗੂ ਹੋਵੇ, ਬਾਹਰੀ Microsoft Learn ਸਰੋਤਾਂ ਨਾਲ ਲਿੰਕ ਕਰੋ
- ਸਮੱਗਰੀ ਨੂੰ ਸਿੱਖਣਯੋਗ ਬਣਾਓ, ਪ੍ਰਚਾਰਕ ਨਹੀਂ

### ਫਾਈਲ ਨਾਮਕਰਨ

- ਫਾਰਮੈਟ ਦੀ ਵਰਤੋਂ ਕਰੋ: `[Module].[Lesson] [Title].md`
- ਉਦਾਹਰਨ: `1.1 The CIA triad and other key concepts.md`
- ਕਵਿਜ ਫਾਈਲਾਂ: `[Module].[Last] End of module quiz.md`
- ਫਾਈਲਨਾਂ ਵਿੱਚ ਖਾਲੀ ਜਗ੍ਹਾ ਦੀ ਵਰਤੋਂ ਕਰੋ (ਮੌਜੂਦਾ ਰੀਤੀ)

## GitHub ਵਰਕਫਲੋਜ਼

### Co-op Translator (co-op-translator.yml)

**ਟ੍ਰਿਗਰ:** `main` ਸ਼ਾਖਾ ਵਿੱਚ ਪੇਸ਼ ਕਰੋ  
**ਉਦੇਸ਼:** ਨਵੀਂ/ਸੋਧੀ ਗਈ Markdown ਫਾਈਲਾਂ ਨੂੰ 50+ ਭਾਸ਼ਾਵਾਂ ਵਿੱਚ ਆਟੋਮੈਟਿਕ ਤੌਰ 'ਤੇ ਅਨੁਵਾਦ ਕਰਦਾ ਹੈ

**ਲੋੜੀਂਦੇ ਵਾਤਾਵਰਣ ਵੈਰੀਏਬਲ:**
- Azure AI ਸੇਵਾ ਪ੍ਰਮਾਣ ਪੱਤਰ (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI ਪ੍ਰਮਾਣ ਪੱਤਰ (ਵਿਕਲਪਿਕ ਵਿਕਲਪ)
- OpenAI ਪ੍ਰਮਾਣ ਪੱਤਰ (ਵਿਕਲਪਿਕ ਵਿਕਲਪ)

### Deploy (deploy.yaml)

**ਟ੍ਰਿਗਰ:** README.md ਵਿੱਚ ਬਦਲਾਅ ਹੋਣ 'ਤੇ `main` ਸ਼ਾਖਾ ਵਿੱਚ ਪੇਸ਼ ਕਰੋ  
**ਉਦੇਸ਼:** ਸਥਿਰ ਸਾਈਟ ਨੂੰ GitHub Pages 'ਤੇ ਤੈਨਾਤ ਕਰਦਾ ਹੈ  
**ਆਉਟਪੁੱਟ:** GitHub Pages ਸਾਈਟ ਨੂੰ ਅਪਡੇਟ ਕਰਦਾ ਹੈ

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**ਟ੍ਰਿਗਰ:** ਸੰਰਚਿਤ ਸ਼ਾਖਾ ਵਿੱਚ ਪੇਸ਼ ਕਰੋ  
**ਉਦੇਸ਼:** Jekyll ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਸਾਈਟ ਬਣਾਉਂਦਾ ਅਤੇ ਤੈਨਾਤ ਕਰਦਾ ਹੈ

## ਪੂਲ ਰਿਕਵੈਸਟ ਗਾਈਡਲਾਈਨਸ

### ਪੇਸ਼ ਕਰਨ ਤੋਂ ਪਹਿਲਾਂ

1. **ਸਮੱਗਰੀ ਸਮੀਖਿਆ:** ਸਾਇਬਰਸੁਰੱਖਿਆ ਧਾਰਨਾਵਾਂ ਦੀ ਸਹੀਤਾ ਅਤੇ ਸਪਸ਼ਟਤਾ ਨੂੰ ਯਕੀਨੀ ਬਣਾਓ
2. **ਫਾਰਮੈਟਿੰਗ:** ਯਕੀਨੀ ਬਣਾਓ ਕਿ Markdown ਫਾਰਮੈਟਿੰਗ ਸਹੀ ਤੌਰ 'ਤੇ ਰੇਂਡਰ ਹੁੰਦੀ ਹੈ
3. **ਲਿੰਕ:** ਸਾਰੇ ਅੰਦਰੂਨੀ ਅਤੇ ਬਾਹਰੀ ਲਿੰਕਾਂ ਦੀ ਜਾਂਚ ਕਰੋ
4. **ਚਿੱਤਰ:** ਯਕੀਨੀ ਬਣਾਓ ਕਿ ਸਾਰੇ ਚਿੱਤਰ ਲੋਡ ਹੁੰਦੇ ਹਨ ਅਤੇ ਵਰਣਨਾਤਮਕ alt ਪਾਠ ਹੈ
5. **ਸਥਿਰਤਾ:** ਮੌਜੂਦਾ ਸਮੱਗਰੀ ਸਟ੍ਰਕਚਰ ਅਤੇ ਸ਼ੈਲੀ ਦੀ ਪਾਲਣਾ ਕਰੋ

### PR ਸਿਰਲੇਖ ਫਾਰਮੈਟ

ਵਰਣਨਾਤਮਕ ਸਿਰਲੇਖ ਦੀ ਵਰਤੋਂ ਕਰੋ:
- `Add: [ਨਵੀਂ ਸਮੱਗਰੀ ਦਾ ਵਰਣਨ]`
- `Update: [Module/Lesson] - [ਸੰਖੇਪ ਵਰਣਨ]`
- `Fix: [ਮੁੱਦੇ ਦਾ ਵਰਣਨ]`
- `Docs: [ਦਸਤਾਵੇਜ਼ ਬਦਲਾਅ]`

### ਲੋੜੀਂਦੇ ਚੈੱਕ

- ਸਮੱਗਰੀ ਦੀ ਸਹੀਤਾ (ਹੱਥੋਂ ਸਮੀਖਿਆ)
- Markdown ਫਾਰਮੈਟਿੰਗ ਵੈਧਤਾ
- ਲਿੰਕ ਦੀ ਜਾਂਚ
- ਅਨੁਵਾਦ ਵਰਕਫਲੋ ਪੂਰਾ ਹੋਣਾ (`main` ਸ਼ਾਖਾ ਮਰਜ ਲਈ)

### ਸਮੀਖਿਆ ਪ੍ਰਕਿਰਿਆ

1. ਘੱਟੋ-ਘੱਟ ਇੱਕ ਮੇਂਟੇਨਰ ਸਮੀਖਿਆ ਲੋੜੀਂਦੀ ਹੈ
2. ਸੁਰੱਖਿਆ ਧਾਰਨਾਵਾਂ ਦੀ ਤਕਨੀਕੀ ਸਹੀਤਾ 'ਤੇ ਧਿਆਨ ਦਿਓ
3. ਪਹੁੰਚਯੋਗਤਾ ਅਤੇ ਸ਼ੁਰੂਆਤੀ-ਮਿਤਰਵਾਨਤਾ ਦੀ ਜਾਂਚ ਕਰੋ
4. ਯਕੀਨੀ ਬਣਾਓ ਕਿ ਵਿਕਰੇਤਾ ਤਟਸਥਤਾ ਬਣਾਈ ਰੱਖੀ ਗਈ ਹੈ

## ਆਮ ਕੰਮ

### ਨਵਾਂ ਪਾਠ ਜੋੜਨਾ

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

### ਮੌਜੂਦਾ ਸਮੱਗਰੀ ਨੂੰ ਅਪਡੇਟ ਕਰਨਾ

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### ਚਿੱਤਰ ਜੋੜਨਾ

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.pa.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## ਟੈਸਟਿੰਗ ਅਤੇ ਵੈਧਤਾ

### ਸਮੱਗਰੀ ਵੈਧਤਾ

ਕਿਉਂਕਿ ਇਹ ਇੱਕ ਦਸਤਾਵੇਜ਼ ਪ੍ਰੋਜੈਕਟ ਹੈ, ਟੈਸਟਿੰਗ ਇਸ 'ਤੇ ਕੇਂਦਰਿਤ ਹੈ:

1. **Markdown ਰੇਂਡਰਿੰਗ:** Docsify ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਸਥਾਨਕ ਤੌਰ 'ਤੇ ਬਦਲਾਅ ਦੇਖੋ
2. **ਲਿੰਕ ਵੈਧਤਾ:** ਸਾਰੇ ਲਿੰਕਾਂ 'ਤੇ ਹੱਥੋਂ ਕਲਿੱਕ ਕਰੋ
3. **ਚਿੱਤਰ ਲੋਡਿੰਗ:** ਯਕੀਨੀ ਬਣਾਓ ਕਿ ਸਾਰੇ ਚਿੱਤਰ ਸਹੀ ਤੌਰ 'ਤੇ ਦਿਖਾਈ ਦੇ ਰਹੇ ਹਨ
4. **ਅਨੁਵਾਦ:** ਜਾਂਚ ਕਰੋ ਕਿ ਫਾਈਲਾਂ ਅਨੁਵਾਦਕ ਵਰਕਫਲੋ ਦੁਆਰਾ ਚੁਣੀਆਂ ਗਈਆਂ ਹਨ (ਆਟੋਮੈਟਿਕ)
5. **ਪਹੁੰਚਯੋਗਤਾ:** ਸਹੀ ਸਿਰਲੇਖ ਹਾਇਰਾਰਕੀ ਅਤੇ alt ਪਾਠ ਨੂੰ ਯਕੀਨੀ ਬਣਾਓ

### ਸਥਾਨਕ ਪ੍ਰੀਵਿਊ

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### ਪ੍ਰੀ-ਕਮਿਟ ਚੈੱਕਲਿਸਟ

- [ ] Markdown ਫਾਈਲਾਂ ਸਹੀ ਸਿੰਟੈਕਸ ਦੀ ਵਰਤੋਂ ਕਰਦੀਆਂ ਹਨ
- [ ] ਸਾਰੇ ਲਿੰਕ ਵੈਧ ਹਨ ਅਤੇ ਜਿੱਥੇ ਸੰਭਵ ਹੋ HTTPS ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹਨ
- [ ] ਚਿੱਤਰਾਂ ਵਿੱਚ ਵਰਣਨਾਤਮਕ alt ਪਾਠ ਹੈ
- [ ] ਸਮੱਗਰੀ ਸ਼ੁਰੂਆਤੀ-ਮਿਤਰਵਾਨ ਅਤੇ ਸਹੀ ਹੈ
- [ ] ਵਿਕਰੇਤਾ-ਤਟਸਥ ਭਾਸ਼ਾ ਬਣਾਈ ਰੱਖੀ ਗਈ ਹੈ
- [ ] README.md ਅਪਡੇਟ ਕੀਤਾ ਜੇ ਮੋਡੀਊਲ ਜੋੜ/ਹਟਾਏ ਗਏ ਹਨ
- [ ] ਫਾਈਲ ਨਾਮਕਰਨ ਰੀਤੀਆਂ ਦੀ ਪਾਲਣਾ ਕੀਤੀ ਗਈ ਹੈ

## ਸੁਰੱਖਿਆ ਵਿਚਾਰ

- **ਸਮੱਗਰੀ ਵਿੱਚ ਕੋਈ ਰਾਜ਼ ਨਹੀਂ:** API ਕੁੰਜੀਆਂ, ਪਾਸਵਰਡ, ਜਾਂ ਸੰਵੇਦਨਸ਼ੀਲ ਡਾਟਾ ਕਦੇ ਵੀ ਕਮਿਟ ਨਾ ਕਰੋ
- **ਲਿੰਕ ਵੈਧਤਾ:** ਯਕੀਨੀ ਬਣਾਓ ਕਿ ਸਾਰੇ ਬਾਹਰੀ ਲਿੰਕ ਭਰੋਸੇਯੋਗ ਸਰੋਤਾਂ ਨੂੰ ਹਨ
- **ਚਿੱਤਰ ਸਮੱਗਰੀ:** ਯਕੀਨੀ ਬਣਾਓ ਕਿ ਚਿੱਤਰਾਂ ਵਿੱਚ ਸੰਵੇਦਨਸ਼ੀਲ ਜਾਣਕਾਰੀ ਨਹੀਂ ਹੈ
- **ਅਨੁਵਾਦ ਵਰਕਫਲੋ:** ਸਹੀ ਪ੍ਰਮਾਣਿਕਤਾ ਨਾਲ Azure AI ਸੇਵਾਵਾਂ ਦੀ ਵਰਤੋਂ ਕਰਦਾ ਹੈ
- **SECURITY.md:** SECURITY.md ਵਿੱਚ ਅਸੁਰੱਖਿਆ ਰਿਪੋਰਟਿੰਗ ਪ੍ਰਕਿਰਿਆ ਦੀ ਪਾਲਣਾ ਕਰੋ

## ਵਾਧੂ ਸਰੋਤ

### ਸੰਬੰਧਿਤ ਮਾਈਕਰੋਸਾਫਟ ਕੋਰਸ

ਇਹ ਪਾਠਕ੍ਰਮ ਮਾਈਕਰੋਸਾਫਟ ਸਿੱਖਣ ਸਰੋਤਾਂ ਦੇ ਵੱਡੇ ਸੰਗ੍ਰਹਿ ਦਾ ਹਿੱਸਾ ਹੈ:
- ਸ਼ੁਰੂਆਤ ਕਰਨ ਵਾਲਿਆਂ ਲਈ ਜਨਰੇਟਿਵ AI
- ਸ਼ੁਰੂਆਤ ਕਰਨ ਵਾਲਿਆਂ ਲਈ AI
- ਸ਼ੁਰੂਆਤ ਕਰਨ ਵਾਲਿਆਂ ਲਈ ਡਾਟਾ ਸਾਇੰਸ
- ਸ਼ੁਰੂਆਤ ਕਰਨ ਵਾਲਿਆਂ ਲਈ ML
- ਸ਼ੁਰੂਆਤ ਕਰਨ ਵਾਲਿਆਂ ਲਈ ਵੈੱਬ ਡਿਵੈਲਪਮੈਂਟ
- ਸ਼ੁਰੂਆਤ ਕਰਨ ਵਾਲਿਆਂ ਲਈ IoT

### ਬਾਹਰੀ ਸਿੱਖਣ ਪਾਥ

Security-101 ਪੂਰਾ ਕਰਨ ਤੋਂ ਬਾਅਦ:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## ਯੋਗਦਾਨ

1. **GitHub 'ਤੇ ਰਿਪੋਜ਼ਟਰੀ ਨੂੰ ਫੋਰਕ ਕਰੋ**
2. **ਆਪਣੇ ਬਦਲਾਅ ਲਈ ਇੱਕ ਫੀਚਰ ਸ਼ਾਖਾ ਬਣਾਓ**
3. **ਉਪਰੋਕਤ ਗਾਈਡਲਾਈਨਸ ਦੀ ਪਾਲਣਾ ਕਰਦੇ ਹੋਏ ਆਪਣੇ ਬਦਲਾਅ ਕਰੋ**
4. **ਸਥਾਨਕ ਤੌਰ 'ਤੇ ਟੈਸਟ ਕਰੋ** ਯਕੀਨੀ ਬਣਾਉਣ ਲਈ ਕਿ ਸਭ ਕੁਝ ਸਹੀ ਤੌਰ 'ਤੇ ਰੇਂਡਰ ਹੁੰਦਾ ਹੈ
5. **ਪੂਲ ਰਿਕਵੈਸਟ ਪੇਸ਼ ਕਰੋ** ਸਪਸ਼ਟ ਬਦਲਾਅ ਵਰਣਨ ਦੇ ਨਾਲ
6. **ਮੇਂਟੇਨਰਾਂ ਤੋਂ ਪ੍ਰਤੀਕ੍ਰਿਆ ਦਾ ਜਵਾਬ ਦਿਓ**

## ਆਮ ਮੁੱਦੇ ਅਤੇ ਸਮੱਸਿਆ ਹੱਲ

### ਅਨੁਵਾਦ ਕੰਮ ਨਹੀਂ ਕਰ ਰਿਹਾ

- ਯਕੀਨੀ ਬਣਾਓ ਕਿ ਬਦਲਾਅ `main` ਸ਼ਾਖਾ ਵਿੱਚ ਪੇਸ਼ ਕੀਤੇ ਗਏ ਹਨ
- GitHub Actions ਟੈਬ ਵਿੱਚ ਵਰਕਫਲੋ ਸਥਿਤੀ ਦੀ ਜਾਂਚ ਕਰੋ
- ਯਕੀਨੀ ਬਣਾਓ ਕਿ ਅਨੁਵਾਦ ਵਰਕਫਲੋ ਰਾਜ਼ ਸੰਰਚਿਤ ਕੀਤੇ ਗਏ

---

**ਅਸਵੀਕਰਤੀ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ AI ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀ ਹੋਣ ਦੀ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਦਿਓ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸੁਚਤਤਾਵਾਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਇਸ ਦਸਤਾਵੇਜ਼ ਦਾ ਮੂਲ ਰੂਪ ਇਸਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਅਧਿਕਾਰਤ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਪੈਦਾ ਹੋਣ ਵਾਲੇ ਕਿਸੇ ਵੀ ਗਲਤਫਹਿਮੀ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।