<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:41:29+00:00",
  "source_file": "AGENTS.md",
  "language_code": "ms"
}
-->
# AGENTS.md

## Gambaran Projek

**Security-101** adalah kurikulum keselamatan siber mesra pemula yang dicipta oleh Microsoft. Projek ini merupakan sumber pembelajaran berasaskan dokumentasi yang mengajar konsep asas keselamatan siber melalui modul yang terstruktur. Ia bebas vendor dan direka untuk diselesaikan dalam pelajaran kecil (30-60 minit setiap satu).

**Teknologi Utama:**
- Markdown untuk kandungan
- Docsify untuk penjanaan laman statik
- GitHub Pages untuk hosting
- Co-op Translator untuk sokongan pelbagai bahasa (50+ bahasa)
- GitHub Actions untuk CI/CD

**Senibina:**
- Kandungan pendidikan diatur dalam 8 modul utama, setiap satu dengan sub-pelajaran
- Laman HTML statik dengan Docsify yang memaparkan kandungan Markdown
- Aliran kerja terjemahan automatik menggunakan perkhidmatan Azure AI
- Tiada alat binaan atau pengurus pakej diperlukan untuk kandungan teras

## Struktur Repositori

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

## Perintah Persediaan

Ini adalah projek dokumentasi tanpa kebergantungan untuk dipasang. Untuk bekerja dengan kandungan:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Aliran Kerja Pembangunan

### Melihat Kandungan Secara Tempatan

Projek ini menggunakan Docsify untuk paparan. Untuk pratonton perubahan:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Struktur Kandungan

Modul diberi nombor secara berurutan:
- **Modul 1:** Konsep keselamatan asas (1.1-1.7)
- **Modul 2:** Pengurusan identiti & akses (2.1-2.4)
- **Modul 3:** Keselamatan rangkaian (3.1-3.4)
- **Modul 4:** Operasi keselamatan (4.1-4.4)
- **Modul 5:** Keselamatan aplikasi (5.1-5.3)
- **Modul 6:** Keselamatan infrastruktur (6.1-6.3)
- **Modul 7:** Keselamatan data (7.1-7.3)
- **Modul 8:** Keselamatan AI (8.1-8.4)

Setiap modul diakhiri dengan fail kuiz (contoh: "1.7 End of module quiz.md").

### Membuat Perubahan Kandungan

1. Edit fail Markdown secara langsung di direktori root
2. Ikuti konvensyen penamaan sedia ada: `[module].[lesson] [Title].md`
3. Kemas kini jadual README.md jika menambah/membuang modul
4. Tambah imej ke direktori `/images/`
5. Rujuk imej menggunakan laluan relatif: `![Deskripsi](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.ms.png)`

## Aliran Kerja Terjemahan

**Terjemahan Automatik:**
- Terjemahan dikendalikan secara automatik oleh Co-op Translator GitHub Action
- Apabila anda menolak perubahan ke cawangan `main`, aliran kerja menterjemahkan kandungan ke 50+ bahasa
- Fail terjemahan disimpan dalam `/translations/[language_code]/`
- Metadata terjemahan dipelihara dalam YAML frontmatter

**Bahasa yang Disokong:** Arab, Bengali, Bulgaria, Burma, Cina (Ringkas, Tradisional), Croatia, Czech, Denmark, Belanda, Estonia, Finland, Perancis, Jerman, Yunani, Ibrani, Hindi, Hungary, Indonesia, Itali, Jepun, Korea, Lithuania, Melayu, Marathi, Nepali, Norway, Parsi, Poland, Portugis, Punjabi, Romania, Rusia, Serbia, Slovak, Slovenia, Sepanyol, Swahili, Sweden, Tagalog, Tamil, Thai, Turki, Ukraine, Urdu, Vietnam, dan banyak lagi.

**Jangan edit fail terjemahan secara manual** - ia akan ditulis semula oleh aliran kerja automatik.

## Garis Panduan Gaya Kod

### Konvensyen Markdown

- Gunakan sintaks Markdown standard
- Tajuk: Gunakan `#` untuk tajuk utama, `##` untuk bahagian, `###` untuk sub-bahagian
- Senarai: Gunakan `-` atau `*` untuk senarai tidak bernombor, `1.` untuk senarai bernombor
- Pautan: Gunakan teks deskriptif dengan URL GitHub penuh untuk rujukan silang
- Imej: Simpan dalam direktori `/images/`, gunakan teks alt yang deskriptif
- Blok kod: Gunakan tanda backtick tiga dengan pengenal bahasa apabila sesuai

### Garis Panduan Kandungan

- Pastikan pelajaran fokus dan ringkas (masa bacaan 30-60 minit)
- Gunakan bahasa yang jelas dan mesra pemula
- Elakkan arahan alat vendor tertentu (kurikulum bebas vendor)
- Sertakan objektif pembelajaran di awal setiap modul
- Pautkan ke sumber Microsoft Learn luaran jika sesuai
- Pastikan kandungan bersifat pendidikan, bukan promosi

### Penamaan Fail

- Gunakan format: `[Module].[Lesson] [Title].md`
- Contoh: `1.1 The CIA triad and other key concepts.md`
- Fail kuiz: `[Module].[Last] End of module quiz.md`
- Gunakan ruang dalam nama fail (konvensyen sedia ada)

## Aliran Kerja GitHub

### Co-op Translator (co-op-translator.yml)

**Pencetus:** Push ke cawangan `main`  
**Tujuan:** Menterjemahkan fail Markdown baru/diubah ke 50+ bahasa secara automatik

**Pembolehubah Persekitaran Diperlukan:**
- Kredensial Perkhidmatan Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Kredensial Azure OpenAI (alternatif pilihan)
- Kredensial OpenAI (alternatif pilihan)

### Deploy (deploy.yaml)

**Pencetus:** Push ke cawangan `main` apabila README.md berubah  
**Tujuan:** Melancarkan laman statik ke GitHub Pages  
**Output:** Mengemas kini laman GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Pencetus:** Push ke cawangan yang dikonfigurasi  
**Tujuan:** Membina dan melancarkan laman menggunakan Jekyll

## Garis Panduan Permintaan Tarik

### Sebelum Menghantar

1. **Semakan Kandungan:** Pastikan ketepatan dan kejelasan konsep keselamatan siber
2. **Pemformatan:** Sahkan pemformatan Markdown dipaparkan dengan betul
3. **Pautan:** Uji semua pautan dalaman dan luaran
4. **Imej:** Pastikan semua imej dimuat dan mempunyai teks alt yang deskriptif
5. **Konsistensi:** Ikuti struktur dan gaya kandungan sedia ada

### Format Tajuk PR

Gunakan tajuk deskriptif:
- `Add: [Deskripsi kandungan baru]`
- `Update: [Modul/Pelajaran] - [Deskripsi ringkas]`
- `Fix: [Deskripsi isu]`
- `Docs: [Perubahan dokumentasi]`

### Semakan Diperlukan

- Ketepatan kandungan (semakan manual)
- Pengesahan pemformatan Markdown
- Pengesahan pautan
- Penyelesaian aliran kerja terjemahan (untuk gabungan cawangan `main`)

### Proses Semakan

1. Sekurang-kurangnya satu semakan oleh penyelenggara diperlukan
2. Fokus pada ketepatan teknikal konsep keselamatan
3. Sahkan kebolehaksesan dan mesra pemula
4. Pastikan neutraliti vendor dikekalkan

## Tugas Biasa

### Menambah Pelajaran Baru

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

### Mengemas Kini Kandungan Sedia Ada

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Menambah Imej

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.ms.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Pengujian dan Pengesahan

### Pengesahan Kandungan

Oleh kerana ini adalah projek dokumentasi, pengujian memberi tumpuan kepada:

1. **Paparan Markdown:** Lihat perubahan secara tempatan menggunakan Docsify
2. **Pengesahan Pautan:** Klik secara manual semua pautan
3. **Pemaparan Imej:** Sahkan semua imej dipaparkan dengan betul
4. **Terjemahan:** Periksa bahawa fail diambil oleh aliran kerja penterjemah (automatik)
5. **Kebolehaksesan:** Pastikan hierarki tajuk dan teks alt yang betul

### Pratonton Tempatan

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Senarai Semak Pra-komit

- [ ] Fail Markdown menggunakan sintaks yang betul
- [ ] Semua pautan adalah sah dan menggunakan HTTPS jika boleh
- [ ] Imej mempunyai teks alt yang deskriptif
- [ ] Kandungan mesra pemula dan tepat
- [ ] Bahasa neutral vendor dikekalkan
- [ ] README.md dikemas kini jika menambah/membuang modul
- [ ] Penamaan fail mengikuti konvensyen

## Pertimbangan Keselamatan

- **Tiada rahsia dalam kandungan:** Jangan sekali-kali komit kunci API, kata laluan, atau data sensitif
- **Pengesahan pautan:** Pastikan semua pautan luaran menuju ke sumber yang dipercayai
- **Kandungan imej:** Sahkan imej tidak mengandungi maklumat sensitif
- **Aliran kerja terjemahan:** Menggunakan perkhidmatan Azure AI dengan pengesahan yang betul
- **SECURITY.md:** Ikuti proses pelaporan kerentanan dalam SECURITY.md

## Sumber Tambahan

### Kursus Berkaitan Microsoft

Kurikulum ini adalah sebahagian daripada koleksi sumber pendidikan Microsoft yang lebih besar:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Laluan Pembelajaran Luaran

Selepas melengkapkan Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Menyumbang

1. **Fork repositori** di GitHub
2. **Buat cawangan ciri** untuk perubahan anda
3. **Lakukan perubahan anda** mengikut garis panduan di atas
4. **Uji secara tempatan** untuk memastikan semuanya dipaparkan dengan betul
5. **Hantar permintaan tarik** dengan deskripsi perubahan yang jelas
6. **Balas maklum balas** daripada penyelenggara

## Isu Biasa dan Penyelesaian Masalah

### Terjemahan Tidak Berfungsi

- Pastikan perubahan ditolak ke cawangan `main`
- Periksa tab GitHub Actions untuk status aliran kerja
- Sahkan rahsia aliran kerja terjemahan dikonfigurasi
- Terjemahan berlaku secara automatik; jangan edit fail terjemahan secara manual

### Imej Tidak Dimuat

- Sahkan laluan imej menggunakan garis miring ke depan: `images/filename.png`
- Periksa bahawa fail imej dikomit ke repositori
- Pastikan nama fail imej sepadan dengan tepat (case-sensitive)
- Gunakan laluan relatif, bukan URL mutlak

### Docsify Tidak Memaparkan

- Periksa bahawa `index.html` ada di root
- Sahkan pautan CDN Docsify boleh diakses
- Pastikan fail Markdown menggunakan sintaks standard
- Periksa konsol pelayar untuk ralat JavaScript

### Pautan Tidak Berfungsi

- Gunakan URL GitHub penuh untuk rujukan silang antara pelajaran
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Uji pautan dalam paparan yang dipaparkan, bukan hanya dalam Markdown mentah

## Penyelenggaraan Projek

### Tugas Berkala

- Semak dan gabungkan sumbangan komuniti
- Kemas kini kandungan untuk ketepatan apabila landskap keselamatan berkembang
- Pantau aliran kerja terjemahan untuk ralat
- Balas isu dan perbincangan
- Kekalkan pautan luaran terkini

### Kawalan Versi

- Cawangan `main` dilindungi dan memerlukan semakan PR
- Semua perubahan melalui proses permintaan tarik
- Fail terjemahan dijana secara automatik, jangan edit secara manual
- Gunakan mesej komit yang bermakna

## Nota untuk Ejen Pengkodan AI

- **Ini adalah projek dokumentasi** - fokus pada kualiti kandungan, bukan kod
- **Jangan ubah fail terjemahan** - ia dijana secara automatik
- **Kekalkan konvensyen penamaan fail** - gunakan ruang dalam nama fail mengikut corak sedia ada
- **Kemas kini README.md** apabila menambah/membuang modul untuk memastikan jadual selaras
- **Uji secara tempatan** sebelum menghantar PR untuk memastikan Markdown dipaparkan dengan betul
- **Ikuti gaya kandungan sedia ada** - kekalkan nada mesra pemula, bebas vendor
- **Tiada proses binaan diperlukan** - pelayan HTTP mudah mencukupi untuk pembangunan tempatan
- **Hormati struktur modul** - setiap modul mempunyai penomboran dan organisasi yang konsisten

---

**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk memastikan ketepatan, sila ambil perhatian bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidaktepatan. Dokumen asal dalam bahasa asalnya harus dianggap sebagai sumber yang berwibawa. Untuk maklumat yang kritikal, terjemahan manusia profesional adalah disyorkan. Kami tidak bertanggungjawab atas sebarang salah faham atau salah tafsir yang timbul daripada penggunaan terjemahan ini.