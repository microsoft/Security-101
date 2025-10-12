<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:34:53+00:00",
  "source_file": "AGENTS.md",
  "language_code": "pl"
}
-->
# AGENTS.md

## Przegląd projektu

**Security-101** to przyjazny dla początkujących kurs cyberbezpieczeństwa stworzony przez Microsoft. Projekt jest zasobem edukacyjnym opartym na dokumentacji, który uczy podstawowych pojęć związanych z cyberbezpieczeństwem poprzez uporządkowane moduły. Jest niezależny od dostawców i zaprojektowany tak, aby można go było ukończyć w krótkich lekcjach (30-60 minut każda).

**Kluczowe technologie:**
- Markdown do tworzenia treści
- Docsify do generowania statycznych stron
- GitHub Pages do hostowania
- Co-op Translator do obsługi wielu języków (ponad 50 języków)
- GitHub Actions do CI/CD

**Architektura:**
- Treści edukacyjne zorganizowane w 8 głównych modułów, każdy z podlekcjami
- Statyczna strona HTML z Docsify renderującym treści Markdown
- Zautomatyzowany proces tłumaczenia przy użyciu usług Azure AI
- Brak narzędzi budowania lub menedżerów pakietów wymaganych dla podstawowych treści

## Struktura repozytorium

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

## Polecenia konfiguracji

Jest to projekt dokumentacyjny, który nie wymaga instalacji zależności. Aby pracować z treścią:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Przepływ pracy deweloperskiej

### Wyświetlanie treści lokalnie

Projekt korzysta z Docsify do renderowania. Aby zobaczyć zmiany:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Struktura treści

Moduły są numerowane sekwencyjnie:
- **Moduł 1:** Podstawowe pojęcia bezpieczeństwa (1.1-1.7)
- **Moduł 2:** Zarządzanie tożsamością i dostępem (2.1-2.4)
- **Moduł 3:** Bezpieczeństwo sieci (3.1-3.4)
- **Moduł 4:** Operacje bezpieczeństwa (4.1-4.4)
- **Moduł 5:** Bezpieczeństwo aplikacji (5.1-5.3)
- **Moduł 6:** Bezpieczeństwo infrastruktury (6.1-6.3)
- **Moduł 7:** Bezpieczeństwo danych (7.1-7.3)
- **Moduł 8:** Bezpieczeństwo AI (8.1-8.4)

Każdy moduł kończy się plikiem quizu (np. "1.7 End of module quiz.md").

### Wprowadzanie zmian w treści

1. Edytuj pliki Markdown bezpośrednio w katalogu głównym
2. Przestrzegaj istniejącej konwencji nazewnictwa: `[module].[lesson] [Title].md`
3. Zaktualizuj tabelę w README.md, jeśli dodajesz/usuwasz moduły
4. Dodaj obrazy do katalogu `/images/`
5. Odnoś się do obrazów za pomocą ścieżek względnych: `![Opis](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.pl.png)`

## Przepływ pracy tłumaczenia

**Automatyczne tłumaczenie:**
- Tłumaczenia są obsługiwane automatycznie przez GitHub Action Co-op Translator
- Po przesłaniu zmian do gałęzi `main`, przepływ pracy tłumaczy treści na ponad 50 języków
- Przetłumaczone pliki są przechowywane w `/translations/[language_code]/`
- Metadane tłumaczenia są zachowywane w YAML frontmatter

**Obsługiwane języki:** arabski, bengalski, bułgarski, birmański, chiński (uproszczony, tradycyjny), chorwacki, czeski, duński, holenderski, estoński, fiński, francuski, niemiecki, grecki, hebrajski, hindi, węgierski, indonezyjski, włoski, japoński, koreański, litewski, malajski, marathi, nepalski, norweski, perski, polski, portugalski, pendżabski, rumuński, rosyjski, serbski, słowacki, słoweński, hiszpański, suahili, szwedzki, tagalog, tamilski, tajski, turecki, ukraiński, urdu, wietnamski i inne.

**Nie edytuj ręcznie plików tłumaczeń** - zostaną one nadpisane przez automatyczny przepływ pracy.

## Wytyczne dotyczące stylu kodu

### Konwencje Markdown

- Używaj standardowej składni Markdown
- Nagłówki: Używaj `#` dla głównego tytułu, `##` dla sekcji, `###` dla podsekcji
- Listy: Używaj `-` lub `*` dla list nieuporządkowanych, `1.` dla list uporządkowanych
- Linki: Używaj opisowego tekstu z pełnymi adresami URL GitHub dla odnośników
- Obrazy: Przechowuj w katalogu `/images/`, używaj opisowego tekstu alternatywnego
- Bloki kodu: Używaj potrójnych backticków z identyfikatorem języka, jeśli to możliwe

### Wytyczne dotyczące treści

- Lekcje powinny być zwięzłe i skoncentrowane (czas czytania 30-60 minut)
- Używaj jasnego, przyjaznego dla początkujących języka
- Unikaj instrukcji dotyczących narzędzi specyficznych dla dostawców (kurs jest niezależny od dostawców)
- Na początku każdego modułu zamieść cele nauki
- Linkuj do zewnętrznych zasobów Microsoft Learn, jeśli to odpowiednie
- Upewnij się, że treści są edukacyjne, a nie promocyjne

### Nazewnictwo plików

- Używaj formatu: `[Module].[Lesson] [Title].md`
- Przykład: `1.1 The CIA triad and other key concepts.md`
- Pliki quizów: `[Module].[Last] End of module quiz.md`
- Używaj spacji w nazwach plików (istniejąca konwencja)

## Przepływy pracy GitHub

### Co-op Translator (co-op-translator.yml)

**Wyzwalacz:** Przesłanie do gałęzi `main`  
**Cel:** Automatyczne tłumaczenie nowych/zmodyfikowanych plików Markdown na ponad 50 języków

**Wymagane zmienne środowiskowe:**
- Poświadczenia usługi Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Poświadczenia Azure OpenAI (opcjonalna alternatywa)
- Poświadczenia OpenAI (opcjonalna alternatywa)

### Deploy (deploy.yaml)

**Wyzwalacz:** Przesłanie do gałęzi `main`, gdy README.md zostanie zmienione  
**Cel:** Publikacja statycznej strony na GitHub Pages  
**Wynik:** Aktualizacja strony GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Wyzwalacz:** Przesłanie do skonfigurowanej gałęzi  
**Cel:** Budowanie i publikacja strony za pomocą Jekyll

## Wytyczne dotyczące pull requestów

### Przed przesłaniem

1. **Przegląd treści:** Upewnij się, że pojęcia związane z cyberbezpieczeństwem są dokładne i jasne
2. **Formatowanie:** Sprawdź, czy formatowanie Markdown renderuje się poprawnie
3. **Linki:** Przetestuj wszystkie linki wewnętrzne i zewnętrzne
4. **Obrazy:** Upewnij się, że wszystkie obrazy się ładują i mają opisowy tekst alternatywny
5. **Spójność:** Przestrzegaj istniejącej struktury i stylu treści

### Format tytułu PR

Używaj opisowych tytułów:
- `Add: [Opis nowej treści]`
- `Update: [Moduł/Lekcja] - [Krótki opis]`
- `Fix: [Opis problemu]`
- `Docs: [Zmiany w dokumentacji]`

### Wymagane kontrole

- Dokładność treści (przegląd ręczny)
- Walidacja formatowania Markdown
- Weryfikacja linków
- Zakończenie przepływu pracy tłumaczenia (dla merge'ów do gałęzi `main`)

### Proces przeglądu

1. Wymagany przegląd przez co najmniej jednego opiekuna
2. Skupienie na technicznej dokładności pojęć związanych z bezpieczeństwem
3. Weryfikacja dostępności i przyjazności dla początkujących
4. Upewnienie się, że neutralność wobec dostawców jest zachowana

## Typowe zadania

### Dodawanie nowej lekcji

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

### Aktualizacja istniejącej treści

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Dodawanie obrazów

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.pl.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testowanie i walidacja

### Walidacja treści

Ponieważ jest to projekt dokumentacyjny, testowanie koncentruje się na:

1. **Renderowanie Markdown:** Wyświetlanie zmian lokalnie za pomocą Docsify
2. **Weryfikacja linków:** Ręczne kliknięcie wszystkich linków
3. **Ładowanie obrazów:** Upewnienie się, że wszystkie obrazy wyświetlają się poprawnie
4. **Tłumaczenie:** Sprawdzenie, czy pliki są przechwytywane przez przepływ pracy tłumacza (automatyczne)
5. **Dostępność:** Upewnienie się, że hierarchia nagłówków i tekst alternatywny są poprawne

### Lokalny podgląd

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Lista kontrolna przed commit'em

- [ ] Pliki Markdown używają poprawnej składni
- [ ] Wszystkie linki są ważne i używają HTTPS, jeśli to możliwe
- [ ] Obrazy mają opisowy tekst alternatywny
- [ ] Treści są przyjazne dla początkujących i dokładne
- [ ] Neutralny język wobec dostawców jest zachowany
- [ ] README.md zaktualizowane, jeśli dodano/usunięto moduły
- [ ] Nazewnictwo plików zgodne z konwencjami

## Rozważania dotyczące bezpieczeństwa

- **Brak tajemnic w treści:** Nigdy nie commituj kluczy API, haseł ani danych wrażliwych
- **Weryfikacja linków:** Upewnij się, że wszystkie zewnętrzne linki prowadzą do zaufanych źródeł
- **Treści obrazów:** Upewnij się, że obrazy nie zawierają informacji wrażliwych
- **Przepływ pracy tłumaczenia:** Korzysta z usług Azure AI z odpowiednią autoryzacją
- **SECURITY.md:** Przestrzegaj procesu zgłaszania luk opisanych w SECURITY.md

## Dodatkowe zasoby

### Powiązane kursy Microsoft

Ten kurs jest częścią większej kolekcji zasobów edukacyjnych Microsoft:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Zewnętrzne ścieżki nauki

Po ukończeniu Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Egzamin SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Współtworzenie

1. **Fork repozytorium** na GitHub
2. **Utwórz gałąź funkcji** dla swoich zmian
3. **Wprowadź zmiany** zgodnie z powyższymi wytycznymi
4. **Przetestuj lokalnie**, aby upewnić się, że wszystko renderuje się poprawnie
5. **Prześlij pull request** z jasnym opisem zmian
6. **Odpowiedz na uwagi** od opiekunów

## Typowe problemy i rozwiązywanie

### Tłumaczenia nie działają

- Upewnij się, że zmiany zostały przesłane do gałęzi `main`
- Sprawdź zakładkę GitHub Actions dla statusu przepływu pracy
- Zweryfikuj konfigurację tajemnic przepływu pracy tłumaczenia
- Tłumaczenie odbywa się automatycznie; nie edytuj ręcznie plików tłumaczeń

### Obrazy nie ładują się

- Zweryfikuj, czy ścieżka obrazu używa ukośników: `images/filename.png`
- Sprawdź, czy plik obrazu został przesłany do repozytorium
- Upewnij się, że nazwa pliku obrazu jest dokładna (wielkość liter ma znaczenie)
- Używaj ścieżek względnych, a nie adresów URL

### Docsify nie renderuje

- Sprawdź, czy `index.html` znajduje się w katalogu głównym
- Zweryfikuj, czy linki CDN Docsify są dostępne
- Upewnij się, że pliki Markdown używają standardowej składni
- Sprawdź konsolę przeglądarki pod kątem błędów JavaScript

### Linki nie działają

- Używaj pełnych adresów URL GitHub dla odnośników między lekcjami
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Testuj linki w widoku renderowanym, a nie tylko w surowym Markdown

## Utrzymanie projektu

### Regularne zadania

- Przegląd i scalanie wkładów społeczności
- Aktualizacja treści dla dokładności w miarę ewolucji krajobrazu bezpieczeństwa
- Monitorowanie przepływu pracy tłumaczenia pod kątem błędów
- Odpowiadanie na zgłoszenia i dyskusje
- Aktualizacja zewnętrznych linków

### Kontrola wersji

- Gałąź `main` jest chroniona i wymaga przeglądów PR
- Wszystkie zmiany przechodzą przez proces pull request
- Pliki tłumaczeń są generowane automatycznie, nie edytuj ich ręcznie
- Używaj znaczących wiadomości commitów

## Uwagi dla agentów AI kodujących

- **To jest projekt dokumentacyjny** - skup się na jakości treści, a nie kodzie
- **Nie modyfikuj plików tłumaczeń** - są generowane automatycznie
- **Zachowaj konwencje nazewnictwa plików** - używaj spacji w nazwach plików zgodnie z istniejącym wzorcem
- **Zaktualizuj README.md** podczas dodawania/usuwania modułów, aby utrzymać tabelę w synchronizacji
- **Testuj lokalnie** przed przesłaniem PR, aby upewnić się, że Markdown renderuje się poprawnie
- **Przestrzegaj istniejącego stylu treści** - zachowaj przyjazny dla początkujących, neutralny wobec dostawców ton
- **Nie wymaga procesu budowania** - prosty serwer HTTP wystarczy do lokalnego rozwoju
- **Szanuj strukturę modułów** - każdy moduł ma spójne numerowanie i organizację

---

**Zastrzeżenie**:  
Ten dokument został przetłumaczony za pomocą usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Chociaż dokładamy wszelkich starań, aby tłumaczenie było precyzyjne, prosimy pamiętać, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w jego języku źródłowym powinien być uznawany za wiarygodne źródło. W przypadku informacji o kluczowym znaczeniu zaleca się skorzystanie z profesjonalnego tłumaczenia przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z użycia tego tłumaczenia.