<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:41:02+00:00",
  "source_file": "AGENTS.md",
  "language_code": "id"
}
-->
# AGENTS.md

## Gambaran Proyek

**Security-101** adalah kurikulum keamanan siber yang ramah pemula yang dibuat oleh Microsoft. Proyek ini merupakan sumber pembelajaran berbasis dokumentasi yang mengajarkan konsep dasar keamanan siber melalui modul-modul yang terstruktur. Kurikulum ini tidak bergantung pada vendor tertentu dan dirancang untuk diselesaikan dalam pelajaran singkat (30-60 menit setiap pelajaran).

**Teknologi Utama:**
- Markdown untuk konten
- Docsify untuk pembuatan situs statis
- GitHub Pages untuk hosting
- Co-op Translator untuk dukungan multi-bahasa (50+ bahasa)
- GitHub Actions untuk CI/CD

**Arsitektur:**
- Konten edukasi diorganisasi dalam 8 modul utama, masing-masing dengan sub-pelajaran
- Situs HTML statis dengan Docsify yang merender konten Markdown
- Alur kerja terjemahan otomatis menggunakan layanan Azure AI
- Tidak memerlukan alat build atau pengelola paket untuk konten inti

## Struktur Repository

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

## Perintah Setup

Ini adalah proyek dokumentasi tanpa dependensi yang perlu diinstal. Untuk bekerja dengan konten:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Alur Kerja Pengembangan

### Melihat Konten Secara Lokal

Proyek ini menggunakan Docsify untuk merender. Untuk melihat pratinjau perubahan:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Struktur Konten

Modul-modul diberi nomor secara berurutan:
- **Modul 1:** Konsep dasar keamanan (1.1-1.7)
- **Modul 2:** Manajemen identitas & akses (2.1-2.4)
- **Modul 3:** Keamanan jaringan (3.1-3.4)
- **Modul 4:** Operasi keamanan (4.1-4.4)
- **Modul 5:** Keamanan aplikasi (5.1-5.3)
- **Modul 6:** Keamanan infrastruktur (6.1-6.3)
- **Modul 7:** Keamanan data (7.1-7.3)
- **Modul 8:** Keamanan AI (8.1-8.4)

Setiap modul diakhiri dengan file kuis (misalnya, "1.7 End of module quiz.md").

### Membuat Perubahan pada Konten

1. Edit file Markdown langsung di direktori root
2. Ikuti konvensi penamaan yang ada: `[modul].[pelajaran] [Judul].md`
3. Perbarui tabel README.md jika menambah/menghapus modul
4. Tambahkan gambar ke direktori `/images/`
5. Referensi gambar menggunakan jalur relatif: `![Deskripsi](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.id.png)`

## Alur Kerja Terjemahan

**Terjemahan Otomatis:**
- Terjemahan ditangani secara otomatis oleh Co-op Translator GitHub Action
- Ketika Anda mendorong perubahan ke cabang `main`, alur kerja menerjemahkan konten ke lebih dari 50 bahasa
- File terjemahan disimpan di `/translations/[kode_bahasa]/`
- Metadata terjemahan dipertahankan dalam YAML frontmatter

**Bahasa yang Didukung:** Arab, Bengali, Bulgaria, Burma, Cina (Sederhana, Tradisional), Kroasia, Ceko, Denmark, Belanda, Estonia, Finlandia, Prancis, Jerman, Yunani, Ibrani, Hindi, Hungaria, Indonesia, Italia, Jepang, Korea, Lithuania, Melayu, Marathi, Nepali, Norwegia, Persia, Polandia, Portugis, Punjabi, Rumania, Rusia, Serbia, Slovak, Slovenia, Spanyol, Swahili, Swedia, Tagalog, Tamil, Thai, Turki, Ukraina, Urdu, Vietnam, dan lainnya.

**Jangan edit file terjemahan secara manual** - file tersebut akan ditimpa oleh alur kerja otomatis.

## Panduan Gaya Kode

### Konvensi Markdown

- Gunakan sintaks Markdown standar
- Judul: Gunakan `#` untuk judul utama, `##` untuk bagian, `###` untuk sub-bagian
- Daftar: Gunakan `-` atau `*` untuk daftar tidak berurutan, `1.` untuk daftar berurutan
- Tautan: Gunakan teks deskriptif dengan URL GitHub lengkap untuk referensi silang
- Gambar: Simpan di direktori `/images/`, gunakan teks alt yang deskriptif
- Blok kode: Gunakan tanda backtick tiga dengan pengidentifikasi bahasa jika berlaku

### Panduan Konten

- Jaga pelajaran tetap fokus dan ringkas (waktu baca 30-60 menit)
- Gunakan bahasa yang jelas dan ramah pemula
- Hindari instruksi alat spesifik vendor (kurikulum ini tidak bergantung pada vendor)
- Sertakan tujuan pembelajaran di awal setiap modul
- Tautkan ke sumber Microsoft Learn eksternal jika sesuai
- Pastikan konten bersifat edukatif, bukan promosi

### Penamaan File

- Gunakan format: `[Modul].[Pelajaran] [Judul].md`
- Contoh: `1.1 The CIA triad and other key concepts.md`
- File kuis: `[Modul].[Terakhir] End of module quiz.md`
- Gunakan spasi dalam nama file (konvensi yang ada)

## Alur Kerja GitHub

### Co-op Translator (co-op-translator.yml)

**Pemicu:** Push ke cabang `main`  
**Tujuan:** Menerjemahkan file Markdown baru/yang dimodifikasi ke lebih dari 50 bahasa secara otomatis

**Variabel Lingkungan yang Diperlukan:**
- Kredensial Layanan Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Kredensial Azure OpenAI (alternatif opsional)
- Kredensial OpenAI (alternatif opsional)

### Deploy (deploy.yaml)

**Pemicu:** Push ke cabang `main` saat README.md berubah  
**Tujuan:** Menerapkan situs statis ke GitHub Pages  
**Output:** Memperbarui situs GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Pemicu:** Push ke cabang yang dikonfigurasi  
**Tujuan:** Membangun dan menerapkan situs menggunakan Jekyll

## Panduan Pull Request

### Sebelum Mengirimkan

1. **Tinjauan Konten:** Pastikan keakuratan dan kejelasan konsep keamanan siber
2. **Pemformatan:** Verifikasi bahwa pemformatan Markdown dirender dengan benar
3. **Tautan:** Uji semua tautan internal dan eksternal
4. **Gambar:** Pastikan semua gambar dimuat dan memiliki teks alt yang deskriptif
5. **Konsistensi:** Ikuti struktur dan gaya konten yang ada

### Format Judul PR

Gunakan judul yang deskriptif:
- `Add: [Deskripsi konten baru]`
- `Update: [Modul/Pelajaran] - [Deskripsi singkat]`
- `Fix: [Deskripsi masalah]`
- `Docs: [Perubahan dokumentasi]`

### Pemeriksaan yang Diperlukan

- Keakuratan konten (tinjauan manual)
- Validasi pemformatan Markdown
- Verifikasi tautan
- Penyelesaian alur kerja terjemahan (untuk penggabungan cabang `main`)

### Proses Tinjauan

1. Setidaknya satu tinjauan dari pemelihara diperlukan
2. Fokus pada keakuratan teknis konsep keamanan
3. Verifikasi aksesibilitas dan keramahan pemula
4. Pastikan netralitas vendor dipertahankan

## Tugas Umum

### Menambahkan Pelajaran Baru

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

### Memperbarui Konten yang Ada

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Menambahkan Gambar

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.id.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Pengujian dan Validasi

### Validasi Konten

Karena ini adalah proyek dokumentasi, pengujian berfokus pada:

1. **Rendering Markdown:** Lihat perubahan secara lokal menggunakan Docsify
2. **Validasi Tautan:** Klik secara manual semua tautan
3. **Pemuatan Gambar:** Verifikasi semua gambar ditampilkan dengan benar
4. **Terjemahan:** Periksa bahwa file diambil oleh alur kerja penerjemah (otomatis)
5. **Aksesibilitas:** Pastikan hierarki judul dan teks alt yang sesuai

### Pratinjau Lokal

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Daftar Periksa Pra-komit

- [ ] File Markdown menggunakan sintaks yang benar
- [ ] Semua tautan valid dan menggunakan HTTPS jika memungkinkan
- [ ] Gambar memiliki teks alt yang deskriptif
- [ ] Konten ramah pemula dan akurat
- [ ] Bahasa netral vendor dipertahankan
- [ ] README.md diperbarui jika menambah/menghapus modul
- [ ] Penamaan file mengikuti konvensi

## Pertimbangan Keamanan

- **Tidak ada rahasia dalam konten:** Jangan pernah mengkomitkan kunci API, kata sandi, atau data sensitif
- **Validasi tautan:** Pastikan semua tautan eksternal menuju sumber yang terpercaya
- **Konten gambar:** Verifikasi gambar tidak mengandung informasi sensitif
- **Alur kerja terjemahan:** Menggunakan layanan Azure AI dengan autentikasi yang tepat
- **SECURITY.md:** Ikuti proses pelaporan kerentanan dalam SECURITY.md

## Sumber Daya Tambahan

### Kursus Terkait Microsoft

Kurikulum ini adalah bagian dari koleksi sumber daya pendidikan Microsoft yang lebih besar:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Jalur Pembelajaran Eksternal

Setelah menyelesaikan Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Kontribusi

1. **Fork repository** di GitHub
2. **Buat cabang fitur** untuk perubahan Anda
3. **Lakukan perubahan** sesuai panduan di atas
4. **Uji secara lokal** untuk memastikan semuanya dirender dengan benar
5. **Kirimkan pull request** dengan deskripsi perubahan yang jelas
6. **Tanggapi umpan balik** dari pemelihara

## Masalah Umum dan Pemecahan Masalah

### Terjemahan Tidak Berfungsi

- Pastikan perubahan didorong ke cabang `main`
- Periksa tab GitHub Actions untuk status alur kerja
- Verifikasi rahasia alur kerja terjemahan dikonfigurasi
- Terjemahan terjadi secara otomatis; jangan edit file terjemahan secara manual

### Gambar Tidak Dimuat

- Verifikasi jalur gambar menggunakan garis miring maju: `images/filename.png`
- Periksa bahwa file gambar dikomit ke repository
- Pastikan nama file gambar cocok persis (case-sensitive)
- Gunakan jalur relatif, bukan URL absolut

### Docsify Tidak Merender

- Periksa bahwa `index.html` ada di root
- Verifikasi tautan CDN Docsify dapat diakses
- Pastikan file Markdown menggunakan sintaks standar
- Periksa konsol browser untuk kesalahan JavaScript

### Tautan Tidak Berfungsi

- Gunakan URL GitHub lengkap untuk referensi silang antar pelajaran
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Uji tautan dalam tampilan yang dirender, bukan hanya dalam Markdown mentah

## Pemeliharaan Proyek

### Tugas Reguler

- Tinjau dan gabungkan kontribusi komunitas
- Perbarui konten untuk keakuratan seiring perkembangan lanskap keamanan
- Pantau alur kerja terjemahan untuk kesalahan
- Tanggapi masalah dan diskusi
- Jaga tautan eksternal tetap terkini

### Kontrol Versi

- Cabang `main` dilindungi dan memerlukan tinjauan PR
- Semua perubahan melalui proses pull request
- File terjemahan dihasilkan secara otomatis, jangan edit secara manual
- Gunakan pesan komit yang bermakna

## Catatan untuk Agen Pemrograman AI

- **Ini adalah proyek dokumentasi** - fokus pada kualitas konten, bukan kode
- **Jangan modifikasi file terjemahan** - file tersebut dihasilkan secara otomatis
- **Pertahankan konvensi penamaan file** - gunakan spasi dalam nama file sesuai pola yang ada
- **Perbarui README.md** saat menambah/menghapus modul untuk menjaga tabel tetap sinkron
- **Uji secara lokal** sebelum mengirimkan PR untuk memastikan Markdown dirender dengan benar
- **Ikuti gaya konten yang ada** - pertahankan nada ramah pemula dan netral vendor
- **Tidak diperlukan proses build** - server HTTP sederhana sudah cukup untuk pengembangan lokal
- **Hormati struktur modul** - setiap modul memiliki penomoran dan organisasi yang konsisten

---

**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan layanan penerjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berupaya untuk memberikan hasil yang akurat, harap diketahui bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang otoritatif. Untuk informasi yang bersifat kritis, disarankan menggunakan jasa penerjemahan manusia profesional. Kami tidak bertanggung jawab atas kesalahpahaman atau penafsiran yang keliru yang timbul dari penggunaan terjemahan ini.