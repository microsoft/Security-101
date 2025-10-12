<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:38:40+00:00",
  "source_file": "AGENTS.md",
  "language_code": "fi"
}
-->
# AGENTS.md

## Projektin yleiskatsaus

**Security-101** on Microsoftin luoma kyberturvallisuuden peruskurssi aloittelijoille. Projekti on dokumentaatioon perustuva oppimisresurssi, joka opettaa kyberturvallisuuden peruskäsitteitä jäsenneltyjen moduulien avulla. Se on riippumaton toimittajista ja suunniteltu suoritettavaksi pienissä oppitunneissa (30–60 minuuttia kerrallaan).

**Keskeiset teknologiat:**
- Sisältö Markdown-muodossa
- Docsify staattisen sivuston luomiseen
- GitHub Pages isännöintiin
- Co-op Translator monikieliseen tukeen (yli 50 kieltä)
- GitHub Actions CI/CD-prosessiin

**Arkkitehtuuri:**
- Opetussisältö jaettu 8 päämoduuliin, joista jokaisessa on aliluentoja
- Staattinen HTML-sivusto, jossa Docsify renderöi Markdown-sisällön
- Automaattinen käännösprosessi Azure AI -palveluiden avulla
- Ei vaadi rakennustyökaluja tai pakettien hallintaa ydinsisällölle

## Repositorion rakenne

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

## Asennuskomennot

Tämä on dokumentaatioprojekti, joka ei vaadi riippuvuuksien asentamista. Sisällön kanssa työskentelyyn:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Kehitysprosessi

### Sisällön tarkastelu paikallisesti

Projekti käyttää Docsifyä renderöintiin. Muutosten esikatseluun:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Sisällön rakenne

Moduulit on numeroitu järjestyksessä:
- **Moduuli 1:** Perusturvallisuuden käsitteet (1.1–1.7)
- **Moduuli 2:** Identiteetti ja pääsynhallinta (2.1–2.4)
- **Moduuli 3:** Verkkoturvallisuus (3.1–3.4)
- **Moduuli 4:** Turvallisuustoiminnot (4.1–4.4)
- **Moduuli 5:** Sovellusturvallisuus (5.1–5.3)
- **Moduuli 6:** Infrastruktuurin turvallisuus (6.1–6.3)
- **Moduuli 7:** Dataturvallisuus (7.1–7.3)
- **Moduuli 8:** AI-turvallisuus (8.1–8.4)

Jokainen moduuli päättyy quiz-tiedostoon (esim. "1.7 End of module quiz.md").

### Sisällön muokkaaminen

1. Muokkaa Markdown-tiedostoja suoraan juurihakemistossa
2. Noudata olemassa olevaa nimeämiskäytäntöä: `[moduuli].[oppitunti] [Otsikko].md`
3. Päivitä README.md-taulukko, jos lisäät tai poistat moduuleja
4. Lisää kuvat `/images/`-hakemistoon
5. Viittaa kuviin suhteellisilla poluilla: `![Kuvaus](../../translated_images/tiedostonimi.db422130e08e17b08f6e90f521a616c6432a7368ca45671df319a6fbc4bf2378.fi.png)`

## Käännösprosessi

**Automaattinen käännös:**
- Käännökset hoidetaan automaattisesti Co-op Translator GitHub Actionin avulla
- Kun teet muutoksia `main`-haaraan, työnkulku kääntää sisällön yli 50 kielelle
- Käännetyt tiedostot tallennetaan `/translations/[language_code]/`-hakemistoon
- Käännösten metadata säilytetään YAML-etuliitteessä

**Tuetut kielet:** Arabia, bengali, bulgaria, burma, kiina (yksinkertaistettu, perinteinen), kroatia, tšekki, tanska, hollanti, viro, suomi, ranska, saksa, kreikka, heprea, hindi, unkari, indonesia, italia, japani, korea, liettua, malaiji, marathi, nepali, norja, persia, puola, portugali, pandžabi, romania, venäjä, serbia, slovakki, sloveeni, espanja, swahili, ruotsi, tagalog, tamili, thai, turkki, ukraina, urdu, vietnam ja muita.

**Älä muokkaa käännöstiedostoja manuaalisesti** - ne korvataan automaattisella työnkululla.

## Koodityyliohjeet

### Markdown-käytännöt

- Käytä standardia Markdown-syntaksia
- Otsikot: Käytä `#` pääotsikolle, `##` osioille, `###` aliosioille
- Listat: Käytä `-` tai `*` luetteloille, `1.` numeroiduille listauksille
- Linkit: Käytä kuvailevaa tekstiä ja täydellisiä GitHub-URL-osoitteita viittauksille
- Kuvat: Tallenna `/images/`-hakemistoon, käytä kuvailevaa alt-tekstiä
- Koodilohkot: Käytä kolmoistakaisia ja kielitunnistetta, kun soveltuu

### Sisältökäytännöt

- Pidä oppitunnit keskittyneinä ja tiiviinä (30–60 minuutin lukuaika)
- Käytä selkeää, aloittelijaystävällistä kieltä
- Vältä toimittajakohtaisia työkalujen ohjeita (kurssi on riippumaton toimittajista)
- Sisällytä oppimistavoitteet jokaisen moduulin alkuun
- Linkitä ulkoisiin Microsoft Learn -resursseihin, kun soveltuu
- Varmista, että sisältö on opettavaista, ei mainostavaa

### Tiedoston nimeäminen

- Käytä muotoa: `[Moduuli].[Oppitunti] [Otsikko].md`
- Esimerkki: `1.1 The CIA triad and other key concepts.md`
- Quiz-tiedostot: `[Moduuli].[Viimeinen] End of module quiz.md`
- Käytä tiedostonimissä välilyöntejä (olemassa oleva käytäntö)

## GitHub-työnkulut

### Co-op Translator (co-op-translator.yml)

**Laukaisu:** Push `main`-haaraan  
**Tarkoitus:** Kääntää uudet/muokatut Markdown-tiedostot automaattisesti yli 50 kielelle

**Vaaditut ympäristömuuttujat:**
- Azure AI -palvelun tunnukset (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI -tunnukset (valinnainen vaihtoehto)
- OpenAI-tunnukset (valinnainen vaihtoehto)

### Deploy (deploy.yaml)

**Laukaisu:** Push `main`-haaraan, kun README.md muuttuu  
**Tarkoitus:** Julkaisee staattisen sivuston GitHub Pagesiin  
**Tuotos:** Päivittää GitHub Pages -sivuston

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Laukaisu:** Push määritettyyn haaraan  
**Tarkoitus:** Rakentaa ja julkaisee sivuston Jekyllin avulla

## Pull Request -ohjeet

### Ennen lähettämistä

1. **Sisällön tarkistus:** Varmista kyberturvallisuuden käsitteiden tarkkuus ja selkeys
2. **Muotoilu:** Tarkista, että Markdown-muotoilu renderöityy oikein
3. **Linkit:** Testaa kaikki sisäiset ja ulkoiset linkit
4. **Kuvat:** Varmista, että kaikki kuvat latautuvat ja niillä on kuvaileva alt-teksti
5. **Johdonmukaisuus:** Noudata olemassa olevaa sisältörakennetta ja tyyliä

### PR-otsikon muoto

Käytä kuvailevia otsikoita:
- `Add: [Uuden sisällön kuvaus]`
- `Update: [Moduuli/Oppitunti] - [Lyhyt kuvaus]`
- `Fix: [Ongelman kuvaus]`
- `Docs: [Dokumentaatiomuutokset]`

### Vaaditut tarkistukset

- Sisällön tarkkuus (manuaalinen tarkistus)
- Markdown-muotoilun validointi
- Linkkien tarkistus
- Käännöstyönkulun valmistuminen (`main`-haaran yhdistämistä varten)

### Tarkistusprosessi

1. Vähintään yksi ylläpitäjän tarkistus vaaditaan
2. Keskity kyberturvallisuuden käsitteiden tekniseen tarkkuuteen
3. Varmista saavutettavuus ja aloittelijaystävällisyys
4. Varmista, että riippumattomuus toimittajista säilyy

## Yleiset tehtävät

### Uuden oppitunnin lisääminen

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

### Olemassa olevan sisällön päivittäminen

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Kuvien lisääminen

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.fi.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testaus ja validointi

### Sisällön validointi

Koska tämä on dokumentaatioprojekti, testaus keskittyy:

1. **Markdown-renderöinti:** Tarkastele muutoksia paikallisesti Docsifyllä
2. **Linkkien validointi:** Klikkaa kaikkia linkkejä manuaalisesti
3. **Kuvien lataus:** Varmista, että kaikki kuvat näkyvät oikein
4. **Käännös:** Tarkista, että tiedostot poimitaan käännöstyönkulussa (automaattinen)
5. **Saavutettavuus:** Varmista oikea otsikkohierarkia ja alt-teksti

### Paikallinen esikatselu

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Ennen sitoutumista -tarkistuslista

- [ ] Markdown-tiedostot käyttävät oikeaa syntaksia
- [ ] Kaikki linkit ovat kelvollisia ja käyttävät HTTPS:ää, jos mahdollista
- [ ] Kuvilla on kuvaileva alt-teksti
- [ ] Sisältö on aloittelijaystävällistä ja tarkkaa
- [ ] Riippumaton toimittajista
- [ ] README.md päivitetty, jos moduuleja lisätään/poistetaan
- [ ] Tiedostonimien käytäntöjä noudatetaan

## Turvallisuushuomiot

- **Ei salaisuuksia sisällössä:** Älä koskaan sitoudu API-avaimia, salasanoja tai arkaluontoisia tietoja
- **Linkkien validointi:** Varmista, että kaikki ulkoiset linkit johtavat luotettaviin lähteisiin
- **Kuvien sisältö:** Varmista, että kuvat eivät sisällä arkaluontoista tietoa
- **Käännöstyönkulku:** Käyttää Azure AI -palveluita asianmukaisella todennuksella
- **SECURITY.md:** Noudata SECURITY.md-tiedostossa kuvattua haavoittuvuuksien raportointiprosessia

## Lisäresurssit

### Liittyvät Microsoft-kurssit

Tämä kurssi on osa laajempaa Microsoftin koulutusresurssien kokoelmaa:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Ulkoiset oppimispolut

Security-101:n suorittamisen jälkeen:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Osallistuminen

1. **Forkkaa repositorio** GitHubissa
2. **Luo ominaisuushaara** muutoksillesi
3. **Tee muutokset** noudattaen yllä olevia ohjeita
4. **Testaa paikallisesti** varmistaaksesi, että kaikki renderöityy oikein
5. **Lähetä pull request** selkeällä muutosten kuvauksella
6. **Vastaa ylläpitäjien palautteeseen**

## Yleiset ongelmat ja vianmääritys

### Käännökset eivät toimi

- Varmista, että muutokset on työnnetty `main`-haaraan
- Tarkista GitHub Actions -välilehdeltä työnkulun tila
- Varmista, että käännöstyönkulun salaisuudet on määritetty
- Käännös tapahtuu automaattisesti; älä muokkaa käännöstiedostoja manuaalisesti

### Kuvat eivät lataudu

- Varmista, että kuvan polku käyttää etuviivoja: `images/tiedostonimi.png`
- Tarkista, että kuvatiedosto on sitoutettu repositorioon
- Varmista, että kuvatiedoston nimi täsmää tarkasti (kirjainkoko huomioiden)
- Käytä suhteellisia polkuja, älä absoluuttisia URL-osoitteita

### Docsify ei renderöi

- Tarkista, että `index.html` on juurihakemistossa
- Varmista, että Docsify CDN-linkit ovat käytettävissä
- Varmista, että Markdown-tiedostot käyttävät standardisyntaksia
- Tarkista selaimen konsolista JavaScript-virheet

### Linkit eivät toimi

- Käytä täydellisiä GitHub-URL-osoitteita viittauksille oppituntien välillä
- Muoto: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testaa linkit renderöidyssä näkymässä, ei pelkästään raakamuodossa

## Projektin ylläpito

### Säännölliset tehtävät

- Tarkista ja yhdistä yhteisön kontribuutiot
- Päivitä sisältöä tarkkuuden varmistamiseksi, kun turvallisuusympäristö kehittyy
- Seuraa käännöstyönkulun virheitä
- Vastaa ongelmiin ja keskusteluihin
- Pidä ulkoiset linkit ajan tasalla

### Versionhallinta

- `main`-haara on suojattu ja vaatii PR-tarkistuksia
- Kaikki muutokset käyvät läpi pull request -prosessin
- Käännöstiedostot luodaan automaattisesti, älä muokkaa niitä manuaalisesti
- Käytä merkityksellisiä commit-viestejä

## Huomautuksia AI-koodausagenteille

- **Tämä on dokumentaatioprojekti** - keskity sisällön laatuun, ei koodiin
- **Älä muokkaa käännöstiedostoja** - ne luodaan automaattisesti
- **Säilytä tiedostonimeämiskäytännöt** - käytä välilyöntejä tiedostonimissä olemassa olevan mallin mukaisesti
- **Päivitä README.md** lisätessäsi/poistaessasi moduuleja, jotta taulukko pysyy synkronoituna
- **Testaa paikallisesti** ennen PR:n lähettämistä varmistaaksesi, että Markdown renderöityy oikein
- **Noudata olemassa olevaa sisältötyyliä** - säilytä aloittelijaystävällinen, riippumaton sävy
- **Ei rakennusprosessia vaadita** - yksinkertainen HTTP-palvelin riittää paikalliseen kehitykseen
- **Kunnioita moduulirakennetta** - jokaisella moduulilla on johdonmukainen numerointi ja organisointi

---

**Vastuuvapauslauseke**:  
Tämä asiakirja on käännetty käyttämällä tekoälypohjaista käännöspalvelua [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, huomioithan, että automaattiset käännökset voivat sisältää virheitä tai epätarkkuuksia. Alkuperäistä asiakirjaa sen alkuperäisellä kielellä tulisi pitää ensisijaisena lähteenä. Kriittisen tiedon osalta suositellaan ammattimaista ihmiskäännöstä. Emme ole vastuussa väärinkäsityksistä tai virhetulkinnoista, jotka johtuvat tämän käännöksen käytöstä.