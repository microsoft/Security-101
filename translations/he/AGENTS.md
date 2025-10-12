<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:39:44+00:00",
  "source_file": "AGENTS.md",
  "language_code": "he"
}
-->
# AGENTS.md

## סקירת הפרויקט

**Security-101** הוא תוכנית לימוד סייבר למתחילים שפותחה על ידי מיקרוסופט. הפרויקט הוא משאב לימודי מבוסס תיעוד שמלמד מושגי יסוד בסייבר דרך מודולים מובנים. התוכנית אינה תלויה בספק מסוים ומיועדת להשלמה בשיעורים קצרים (30-60 דקות כל אחד).

**טכנולוגיות עיקריות:**
- Markdown לתוכן
- Docsify ליצירת אתר סטטי
- GitHub Pages לאירוח
- Co-op Translator לתמיכה בריבוי שפות (50+ שפות)
- GitHub Actions ל-CI/CD

**ארכיטקטורה:**
- תוכן לימודי מאורגן ב-8 מודולים עיקריים, כל אחד עם שיעורי משנה
- אתר HTML סטטי עם Docsify שמציג תוכן Markdown
- תהליך תרגום אוטומטי באמצעות שירותי Azure AI
- אין צורך בכלי בנייה או מנהלי חבילות עבור התוכן המרכזי

## מבנה המאגר

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

## פקודות התקנה

זהו פרויקט תיעוד ללא תלות להתקנה. לעבודה עם התוכן:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## תהליך הפיתוח

### צפייה בתוכן באופן מקומי

הפרויקט משתמש ב-Docsify להצגת התוכן. כדי להציג שינויים:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### מבנה התוכן

המודולים ממוספרים באופן רציף:
- **מודול 1:** מושגי יסוד באבטחה (1.1-1.7)
- **מודול 2:** ניהול זהויות וגישה (2.1-2.4)
- **מודול 3:** אבטחת רשת (3.1-3.4)
- **מודול 4:** תפעול אבטחה (4.1-4.4)
- **מודול 5:** אבטחת אפליקציות (5.1-5.3)
- **מודול 6:** אבטחת תשתיות (6.1-6.3)
- **מודול 7:** אבטחת נתונים (7.1-7.3)
- **מודול 8:** אבטחת AI (8.1-8.4)

כל מודול מסתיים בקובץ מבחן (לדוגמה, "1.7 End of module quiz.md").

### ביצוע שינויים בתוכן

1. ערכו קבצי Markdown ישירות בתיקיית השורש
2. עקבו אחר תבנית השמות הקיימת: `[module].[lesson] [Title].md`
3. עדכנו את טבלת README.md אם מוסיפים/מסירים מודולים
4. הוסיפו תמונות לתיקיית `/images/`
5. התייחסו לתמונות באמצעות נתיבים יחסיים: `![תיאור](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.he.png)`

## תהליך התרגום

**תרגום אוטומטי:**
- התרגומים מתבצעים אוטומטית על ידי Co-op Translator GitHub Action
- כאשר אתם דוחפים שינויים לענף `main`, התהליך מתרגם את התוכן ל-50+ שפות
- קבצי התרגום נשמרים ב-`/translations/[language_code]/`
- מטא-נתונים של התרגום נשמרים ב-YAML frontmatter

**שפות נתמכות:** ערבית, בנגלית, בולגרית, בורמזית, סינית (פשוטה, מסורתית), קרואטית, צ'כית, דנית, הולנדית, אסטונית, פינית, צרפתית, גרמנית, יוונית, עברית, הינדי, הונגרית, אינדונזית, איטלקית, יפנית, קוריאנית, ליטאית, מלאית, מראטהי, נפאלית, נורווגית, פרסית, פולנית, פורטוגזית, פונג'בית, רומנית, רוסית, סרבית, סלובקית, סלובנית, ספרדית, סוואהילית, שוודית, טאגאלוג, טמילית, תאית, טורקית, אוקראינית, אורדו, וייטנאמית ועוד.

**אל תערכו ידנית קבצי תרגום** - הם יוחלפו על ידי התהליך האוטומטי.

## הנחיות לסגנון קוד

### תבניות Markdown

- השתמשו בתחביר Markdown סטנדרטי
- כותרות: השתמשו ב-`#` לכותרת ראשית, `##` לסעיפים, `###` לתת-סעיפים
- רשימות: השתמשו ב-`-` או `*` לרשימות לא מסודרות, `1.` לרשימות מסודרות
- קישורים: השתמשו בטקסט תיאורי עם כתובות GitHub מלאות להפניות פנימיות
- תמונות: אחסנו בתיקיית `/images/`, השתמשו בטקסט אלטרנטיבי תיאורי
- קטעי קוד: השתמשו בשלושה גרשיים עם מזהה שפה כשמתאים

### הנחיות לתוכן

- שמרו על שיעורים ממוקדים ותמציתיים (30-60 דקות קריאה)
- השתמשו בשפה ברורה וידידותית למתחילים
- הימנעו מהוראות לכלים ספציפיים לספק (התוכנית אינה תלויה בספק)
- כללו מטרות לימוד בתחילת כל מודול
- קישרו למשאבי Microsoft Learn חיצוניים כשמתאים
- ודאו שהתוכן חינוכי ולא שיווקי

### תבנית שמות קבצים

- השתמשו בפורמט: `[Module].[Lesson] [Title].md`
- דוגמה: `1.1 The CIA triad and other key concepts.md`
- קבצי מבחן: `[Module].[Last] End of module quiz.md`
- השתמשו ברווחים בשמות קבצים (תבנית קיימת)

## תהליכי GitHub

### Co-op Translator (co-op-translator.yml)

**Trigger:** דחיפה לענף `main`  
**מטרה:** מתרגם אוטומטית קבצי Markdown חדשים/מעודכנים ל-50+ שפות

**משתני סביבה נדרשים:**
- אישורי שירות Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- אישורי Azure OpenAI (חלופה אופציונלית)
- אישורי OpenAI (חלופה אופציונלית)

### Deploy (deploy.yaml)

**Trigger:** דחיפה לענף `main` כאשר README.md משתנה  
**מטרה:** מפרסם אתר סטטי ל-GitHub Pages  
**Output:** מעדכן את אתר GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** דחיפה לענף מוגדר  
**מטרה:** בונה ומפרסם אתר באמצעות Jekyll

## הנחיות לבקשות משיכה

### לפני הגשה

1. **סקירת תוכן:** ודאו דיוק ובהירות של מושגי סייבר
2. **עיצוב:** בדקו שפורמט Markdown מוצג כראוי
3. **קישורים:** בדקו את כל הקישורים הפנימיים והחיצוניים
4. **תמונות:** ודאו שכל התמונות נטענות ויש להן טקסט אלטרנטיבי תיאורי
5. **עקביות:** עקבו אחר מבנה וסגנון התוכן הקיים

### פורמט כותרת PR

השתמשו בכותרות תיאוריות:
- `Add: [תיאור תוכן חדש]`
- `Update: [מודול/שיעור] - [תיאור קצר]`
- `Fix: [תיאור בעיה]`
- `Docs: [שינויים בתיעוד]`

### בדיקות נדרשות

- דיוק תוכן (סקירה ידנית)
- אימות פורמט Markdown
- בדיקת קישורים
- השלמת תהליך תרגום (למיזוגים לענף `main`)

### תהליך סקירה

1. נדרשת סקירה של לפחות אחד מהמתחזקים
2. התמקדות בדיוק טכני של מושגי אבטחה
3. בדיקת נגישות וידידותיות למתחילים
4. שמירה על ניטרליות ספק

## משימות נפוצות

### הוספת שיעור חדש

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

### עדכון תוכן קיים

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### הוספת תמונות

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.he.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## בדיקות ואימות

### אימות תוכן

מכיוון שזהו פרויקט תיעוד, הבדיקות מתמקדות ב:

1. **הצגת Markdown:** צפייה בשינויים באופן מקומי באמצעות Docsify
2. **אימות קישורים:** לחיצה ידנית על כל הקישורים
3. **טעינת תמונות:** בדיקת הצגת כל התמונות
4. **תרגום:** בדיקת קליטת קבצים על ידי תהליך התרגום (אוטומטי)
5. **נגישות:** שמירה על היררכיית כותרות נכונה וטקסט אלטרנטיבי

### תצוגה מקומית

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### רשימת בדיקות לפני התחייבות

- [ ] קבצי Markdown משתמשים בתחביר נכון
- [ ] כל הקישורים תקפים ומשתמשים ב-HTTPS כשאפשר
- [ ] לתמונות יש טקסט אלטרנטיבי תיאורי
- [ ] התוכן ידידותי למתחילים ומדויק
- [ ] שפה ניטרלית לספק נשמרת
- [ ] README.md מעודכן אם מוסיפים/מסירים מודולים
- [ ] שמות קבצים עוקבים אחר תבניות

## שיקולי אבטחה

- **אין סודות בתוכן:** לעולם אל תתחייבו מפתחות API, סיסמאות או נתונים רגישים
- **אימות קישורים:** ודאו שכל הקישורים החיצוניים מובילים למקורות אמינים
- **תוכן תמונות:** בדקו שהתמונות אינן מכילות מידע רגיש
- **תהליך תרגום:** משתמש בשירותי Azure AI עם אימות מתאים
- **SECURITY.md:** עקבו אחר תהליך דיווח על פגיעויות ב-SECURITY.md

## משאבים נוספים

### קורסים קשורים של Microsoft

תוכנית לימוד זו היא חלק מאוסף רחב יותר של משאבי לימוד של Microsoft:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### מסלולי לימוד חיצוניים

לאחר השלמת Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## תרומה

1. **פצלו את המאגר** ב-GitHub
2. **צרו ענף פיצ'ר** לשינויים שלכם
3. **בצעו את השינויים** בהתאם להנחיות לעיל
4. **בדקו באופן מקומי** כדי לוודא שהכול מוצג כראוי
5. **הגישו בקשת משיכה** עם תיאור ברור של השינויים
6. **הגיבו למשוב** מהמתחזקים

## בעיות נפוצות ופתרון תקלות

### תרגומים לא עובדים

- ודאו שהשינויים נדחפו לענף `main`
- בדקו את לשונית GitHub Actions למצב התהליך
- אימתו שהסודות של תהליך התרגום מוגדרים
- התרגום מתבצע אוטומטית; אל תערכו ידנית קבצי תרגום

### תמונות לא נטענות

- ודאו שהנתיב לתמונה משתמש בקווים נטויים קדימה: `images/filename.png`
- בדקו שקובץ התמונה התחייב למאגר
- ודאו ששם הקובץ תואם בדיוק (רגיש לאותיות גדולות/קטנות)
- השתמשו בנתיבים יחסיים, לא בכתובות URL מוחלטות

### Docsify לא מציג

- בדקו ש-`index.html` נמצא בתיקיית השורש
- אימתו שכתובות ה-CDN של Docsify נגישות
- ודאו שקבצי Markdown משתמשים בתחביר סטנדרטי
- בדקו את קונסולת הדפדפן לשגיאות JavaScript

### קישורים לא עובדים

- השתמשו בכתובות GitHub מלאות להפניות פנימיות בין שיעורים
- פורמט: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- בדקו קישורים בתצוגה מוצגת, לא רק ב-Markdown גולמי

## תחזוקת הפרויקט

### משימות שוטפות

- סקירה ומיזוג תרומות מהקהילה
- עדכון תוכן לדיוק ככל שנוף האבטחה מתפתח
- מעקב אחר תהליך התרגום לשגיאות
- תגובה לבעיות ודיונים
- שמירה על קישורים חיצוניים מעודכנים

### בקרת גרסאות

- ענף `main` מוגן ודורש סקירות PR
- כל השינויים עוברים תהליך בקשת משיכה
- קבצי תרגום נוצרים אוטומטית, אל תערכו ידנית
- השתמשו בהודעות התחייבות משמעותיות

## הערות לסוכני קידוד AI

- **זהו פרויקט תיעוד** - התמקדות באיכות התוכן, לא בקוד
- **אל תשנו קבצי תרגום** - הם נוצרים אוטומטית
- **שמרו על תבניות שמות קבצים** - השתמשו ברווחים בשמות קבצים בהתאם לתבנית הקיימת
- **עדכנו README.md** כאשר מוסיפים/מסירים מודולים כדי לשמור על הטבלה מסונכרנת
- **בדקו באופן מקומי** לפני הגשת PRs כדי לוודא ש-Markdown מוצג כראוי
- **עקבו אחר סגנון התוכן הקיים** - שמרו על טון ידידותי למתחילים וניטרלי לספק
- **אין צורך בתהליך בנייה** - שרת HTTP פשוט מספיק לפיתוח מקומי
- **כבדו את מבנה המודול** - לכל מודול יש מספרים וארגון עקביים

---

**כתב ויתור**:  
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש לקחת בחשבון שתרגומים אוטומטיים עשויים להכיל שגיאות או אי דיוקים. המסמך המקורי בשפתו המקורית צריך להיחשב כמקור סמכותי. עבור מידע קריטי, מומלץ להשתמש בתרגום מקצועי על ידי אדם. אנו לא נושאים באחריות לאי הבנות או לפרשנויות שגויות הנובעות משימוש בתרגום זה.