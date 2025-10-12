<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:42:27+00:00",
  "source_file": "AGENTS.md",
  "language_code": "sw"
}
-->
# AGENTS.md

## Muhtasari wa Mradi

**Security-101** ni mtaala wa usalama wa mtandao kwa wanaoanza uliotengenezwa na Microsoft. Mradi huu ni rasilimali ya kujifunza inayotegemea nyaraka ambayo inafundisha dhana za msingi za usalama wa mtandao kupitia moduli zilizopangwa kwa utaratibu. Haitegemei muuzaji yeyote na imeundwa kukamilika kwa masomo mafupi (dakika 30-60 kila moja).

**Teknolojia Muhimu:**
- Markdown kwa maudhui
- Docsify kwa kizazi cha tovuti tuli
- GitHub Pages kwa ajili ya kuhifadhi
- Co-op Translator kwa msaada wa lugha nyingi (lugha 50+)
- GitHub Actions kwa CI/CD

**Muundo wa Usanifu:**
- Maudhui ya elimu yamepangwa katika moduli kuu 8, kila moja ikiwa na masomo madogo
- Tovuti tuli ya HTML na Docsify inayotafsiri maudhui ya Markdown
- Mtiririko wa kazi wa kutafsiri kiotomatiki kwa kutumia huduma za Azure AI
- Hakuna zana za ujenzi au wasimamizi wa kifurushi zinazohitajika kwa maudhui ya msingi

## Muundo wa Hifadhi

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

## Amri za Kuanzisha

Huu ni mradi wa nyaraka bila utegemezi wa kufunga. Ili kufanya kazi na maudhui:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Mtiririko wa Maendeleo

### Kuangalia Maudhui Kwenye Kompyuta Yako

Mradi huu unatumia Docsify kwa kutafsiri. Ili kuangalia mabadiliko:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Muundo wa Maudhui

Moduli zimepangwa kwa namba mfululizo:
- **Moduli ya 1:** Dhana za msingi za usalama (1.1-1.7)
- **Moduli ya 2:** Usimamizi wa utambulisho na ufikiaji (2.1-2.4)
- **Moduli ya 3:** Usalama wa mtandao (3.1-3.4)
- **Moduli ya 4:** Uendeshaji wa usalama (4.1-4.4)
- **Moduli ya 5:** Usalama wa programu (5.1-5.3)
- **Moduli ya 6:** Usalama wa miundombinu (6.1-6.3)
- **Moduli ya 7:** Usalama wa data (7.1-7.3)
- **Moduli ya 8:** Usalama wa AI (8.1-8.4)

Kila moduli inamalizika na faili ya jaribio (mfano, "1.7 End of module quiz.md").

### Kufanya Mabadiliko ya Maudhui

1. Hariri faili za Markdown moja kwa moja kwenye saraka kuu
2. Fuata muundo wa majina uliopo: `[module].[lesson] [Title].md`
3. Sasisha jedwali la README.md ikiwa unaongeza/kutoa moduli
4. Ongeza picha kwenye saraka ya `/images/`
5. Rejelea picha kwa kutumia njia za jamaa: `![Maelezo](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.sw.png)`

## Mtiririko wa Tafsiri

**Tafsiri ya Kiotomatiki:**
- Tafsiri zinafanywa kiotomatiki na Co-op Translator GitHub Action
- Unapopakia mabadiliko kwenye tawi la `main`, mtiririko wa kazi hutafsiri maudhui kwa lugha 50+
- Faili zilizotafsiriwa huhifadhiwa kwenye `/translations/[language_code]/`
- Metadata ya tafsiri huhifadhiwa kwenye YAML frontmatter

**Lugha Zinazoungwa Mkono:** Kiarabu, Kibengali, Kibulgaria, Kiburma, Kichina (Rahisi, Jadi), Kikroeshia, Kicheki, Kideni, Kiholanzi, Kiestonia, Kifini, Kifaransa, Kijerumani, Kigiriki, Kiebrania, Kihindi, Kihungari, Kiindonesia, Kiitaliano, Kijapani, Kikorea, Kilithuania, Kimala, Kihindi, Kinepali, Kinorwe, Kiajemi, Kipolandi, Kireno, Kipunjabi, Kiromania, Kirusi, Kiserbia, Kislovakia, Kislovenia, Kihispania, Kiswahili, Kiswidi, Kitaliano, Kitamil, Kithai, Kituruki, Kiukreni, Kiurdu, Kivietinamu, na zaidi.

**USIHARIRI faili za tafsiri kwa mkono** - zitafutwa na mtiririko wa kazi wa kiotomatiki.

## Miongozo ya Mtindo wa Nambari

### Misingi ya Markdown

- Tumia sintaksia ya kawaida ya Markdown
- Vichwa: Tumia `#` kwa kichwa kikuu, `##` kwa sehemu, `###` kwa sehemu ndogo
- Orodha: Tumia `-` au `*` kwa orodha zisizo na mpangilio, `1.` kwa orodha zenye mpangilio
- Viungo: Tumia maandishi ya maelezo na URL kamili za GitHub kwa marejeleo ya ndani
- Picha: Hifadhi kwenye saraka ya `/images/`, tumia maandishi ya maelezo
- Vitalu vya nambari: Tumia alama tatu za nyuma na kitambulisho cha lugha inapohitajika

### Miongozo ya Maudhui

- Weka masomo yakiwa mafupi na yenye kueleweka (dakika 30-60 za kusoma)
- Tumia lugha rahisi na rafiki kwa wanaoanza
- Epuka maelekezo ya zana maalum za muuzaji (mtaala haubagui muuzaji)
- Jumuisha malengo ya kujifunza mwanzoni mwa kila moduli
- Rejelea rasilimali za nje za Microsoft Learn inapofaa
- Hakikisha maudhui ni ya kielimu, si ya kibiashara

### Jina la Faili

- Tumia muundo: `[Module].[Lesson] [Title].md`
- Mfano: `1.1 The CIA triad and other key concepts.md`
- Faili za jaribio: `[Module].[Last] End of module quiz.md`
- Tumia nafasi kwenye majina ya faili (kama ilivyo kwenye muundo uliopo)

## Mtiririko wa Kazi wa GitHub

### Co-op Translator (co-op-translator.yml)

**Kichocheo:** Kupakia kwenye tawi la `main`  
**Madhumuni:** Kutafsiri kiotomatiki faili mpya/zilizorekebishwa za Markdown kwa lugha 50+

**Vigezo vya Mazingira Vinavyohitajika:**
- Kitambulisho cha huduma ya Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Kitambulisho cha Azure OpenAI (mbadala wa hiari)
- Kitambulisho cha OpenAI (mbadala wa hiari)

### Kuweka (deploy.yaml)

**Kichocheo:** Kupakia kwenye tawi la `main` wakati README.md inabadilika  
**Madhumuni:** Kuweka tovuti tuli kwenye GitHub Pages  
**Matokeo:** Husasisha tovuti ya GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Kichocheo:** Kupakia kwenye tawi lililowekwa  
**Madhumuni:** Kujenga na kuweka tovuti kwa kutumia Jekyll

## Miongozo ya Maombi ya Kuvuta

### Kabla ya Kuwasilisha

1. **Mapitio ya Maudhui:** Hakikisha usahihi na uwazi wa dhana za usalama wa mtandao
2. **Muundo:** Hakikisha muundo wa Markdown unajitokeza vizuri
3. **Viungo:** Jaribu viungo vyote vya ndani na vya nje
4. **Picha:** Hakikisha picha zote zinaonekana na zina maandishi ya maelezo
5. **Ulinganifu:** Fuata muundo na mtindo wa maudhui uliopo

### Muundo wa Kichwa cha PR

Tumia vichwa vya kuelezea:
- `Ongeza: [Maelezo ya maudhui mapya]`
- `Sasisha: [Module/Lesson] - [Maelezo mafupi]`
- `Sahihisha: [Maelezo ya tatizo]`
- `Docs: [Mabadiliko ya nyaraka]`

### Ukaguzi Unaohitajika

- Usahihi wa maudhui (ukaguzi wa mikono)
- Uthibitishaji wa muundo wa Markdown
- Uthibitishaji wa viungo
- Kukamilika kwa mtiririko wa kazi wa tafsiri (kwa miunganiko ya tawi la `main`)

### Mchakato wa Mapitio

1. Angalau ukaguzi mmoja wa msimamizi unahitajika
2. Lenga usahihi wa kiufundi wa dhana za usalama
3. Hakikisha upatikanaji na urahisi wa kueleweka kwa wanaoanza
4. Hakikisha kutokuwepo kwa upendeleo wa muuzaji

## Majukumu ya Kawaida

### Kuongeza Somo Jipya

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

### Kusasisha Maudhui Yaliyopo

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Kuongeza Picha

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.sw.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Upimaji na Uthibitishaji

### Uthibitishaji wa Maudhui

Kwa kuwa huu ni mradi wa nyaraka, upimaji unalenga:

1. **Utoaji wa Markdown:** Angalia mabadiliko kwenye kompyuta yako kwa kutumia Docsify
2. **Uthibitishaji wa Viungo:** Bonyeza viungo vyote kwa mkono
3. **Upakiaji wa Picha:** Hakikisha picha zote zinaonekana vizuri
4. **Tafsiri:** Hakikisha faili zinachukuliwa na mtiririko wa kazi wa tafsiri (kiotomatiki)
5. **Upatikanaji:** Hakikisha mpangilio wa vichwa na maandishi ya maelezo ya picha ni sahihi

### Onyesho la Kwenye Kompyuta

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Orodha ya Kukagua Kabla ya Kujitolea

- [ ] Faili za Markdown zinatumia sintaksia sahihi
- [ ] Viungo vyote ni halali na vinatumia HTTPS inapowezekana
- [ ] Picha zina maandishi ya maelezo
- [ ] Maudhui ni rafiki kwa wanaoanza na ni sahihi
- [ ] Lugha isiyo na upendeleo wa muuzaji inazingatiwa
- [ ] README.md imesasishwa ikiwa kuna kuongeza/kutoa moduli
- [ ] Majina ya faili yanafuata miongozo

## Masuala ya Usalama

- **Hakuna siri kwenye maudhui:** Kamwe usihifadhi funguo za API, nywila, au data nyeti
- **Uthibitishaji wa viungo:** Hakikisha viungo vyote vya nje vinaelekeza kwenye vyanzo vya kuaminika
- **Maudhui ya picha:** Hakikisha picha hazina taarifa nyeti
- **Mtiririko wa kazi wa tafsiri:** Unatumia huduma za Azure AI zenye uthibitishaji sahihi
- **SECURITY.md:** Fuata mchakato wa kuripoti udhaifu katika SECURITY.md

## Rasilimali za Ziada

### Kozi Zinazohusiana za Microsoft

Mtaala huu ni sehemu ya mkusanyiko mkubwa wa rasilimali za elimu za Microsoft:
- AI ya Kizazi kwa Wanaoanza
- AI kwa Wanaoanza
- Sayansi ya Takwimu kwa Wanaoanza
- ML kwa Wanaoanza
- Maendeleo ya Wavuti kwa Wanaoanza
- IoT kwa Wanaoanza

### Njia za Kujifunza za Nje

Baada ya kukamilisha Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Mtihani SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Kuchangia

1. **Nakili hifadhi** kwenye GitHub
2. **Tengeneza tawi la kipengele** kwa mabadiliko yako
3. **Fanya mabadiliko yako** ukifuata miongozo hapo juu
4. **Pima kwenye kompyuta yako** kuhakikisha kila kitu kinaonekana vizuri
5. **Wasilisha ombi la kuvuta** na maelezo wazi ya mabadiliko
6. **Jibu maoni** kutoka kwa wasimamizi

## Masuala ya Kawaida na Utatuzi

### Tafsiri Hazifanyi Kazi

- Hakikisha mabadiliko yamepakiwa kwenye tawi la `main`
- Angalia kichupo cha GitHub Actions kwa hali ya mtiririko wa kazi
- Hakikisha siri za mtiririko wa kazi wa tafsiri zimewekwa
- Tafsiri hufanyika kiotomatiki; usihariri faili za tafsiri kwa mkono

### Picha Hazionekani

- Hakikisha njia ya picha inatumia mistari ya mbele: `images/filename.png`
- Hakikisha faili ya picha imehifadhiwa kwenye hifadhi
- Hakikisha jina la faili ya picha linapatana kabisa (ni nyeti kwa herufi kubwa na ndogo)
- Tumia njia za jamaa, si URL kamili

### Docsify Haifanyi Kazi

- Hakikisha `index.html` ipo kwenye mzizi
- Hakikisha viungo vya CDN vya Docsify vinapatikana
- Hakikisha faili za Markdown zinatumia sintaksia ya kawaida
- Angalia makosa ya JavaScript kwenye kivinjari

### Viungo Havifanyi Kazi

- Tumia URL kamili za GitHub kwa marejeleo kati ya masomo
- Muundo: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Jaribu viungo katika mwonekano uliotafsiriwa, si tu kwenye Markdown ya kawaida

## Matengenezo ya Mradi

### Majukumu ya Kawaida

- Pitia na unganisha michango ya jamii
- Sasisha maudhui kwa usahihi kadri mazingira ya usalama yanavyobadilika
- Fuata mtiririko wa kazi wa tafsiri kwa makosa
- Jibu masuala na mijadala
- Weka viungo vya nje vikiwa vya kisasa

### Udhibiti wa Toleo

- Tawi la `main` limehifadhiwa na linahitaji mapitio ya PR
- Mabadiliko yote yanapitia mchakato wa ombi la kuvuta
- Faili za tafsiri zinatengenezwa kiotomatiki, usizihariri kwa mkono
- Tumia ujumbe wa kujitolea wenye maana

## Vidokezo kwa Mawakala wa AI wa Uandishi wa Nambari

- **Huu ni mradi wa nyaraka** - zingatia ubora wa maudhui, si nambari
- **Usihariri faili za tafsiri** - zinatengenezwa kiotomatiki
- **Hifadhi muundo wa majina ya faili** - tumia nafasi kwenye majina ya faili kama ilivyo kwenye muundo uliopo
- **Sasisha README.md** unapoongeza/kutoa moduli ili kuweka jedwali linalolingana
- **Pima kwenye kompyuta yako** kabla ya kuwasilisha PRs kuhakikisha Markdown inajitokeza vizuri
- **Fuata mtindo wa maudhui uliopo** - weka lugha rahisi na isiyo na upendeleo wa muuzaji
- **Hakuna mchakato wa ujenzi unaohitajika** - seva rahisi ya HTTP inatosha kwa maendeleo ya ndani
- **Heshimu muundo wa moduli** - kila moduli ina namba na mpangilio thabiti

---

**Kanusho**:  
Hati hii imetafsiriwa kwa kutumia huduma ya kutafsiri ya AI [Co-op Translator](https://github.com/Azure/co-op-translator). Ingawa tunajitahidi kuhakikisha usahihi, tafadhali fahamu kuwa tafsiri za kiotomatiki zinaweza kuwa na makosa au kutokuwa sahihi. Hati ya asili katika lugha yake ya awali inapaswa kuzingatiwa kama chanzo cha mamlaka. Kwa taarifa muhimu, tafsiri ya kitaalamu ya binadamu inapendekezwa. Hatutawajibika kwa kutoelewana au tafsiri zisizo sahihi zinazotokana na matumizi ya tafsiri hii.