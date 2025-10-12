<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:35:28+00:00",
  "source_file": "AGENTS.md",
  "language_code": "tr"
}
-->
# AGENTS.md

## Proje Genel Bakış

**Security-101**, Microsoft tarafından oluşturulan, yeni başlayanlar için uygun bir siber güvenlik müfredatıdır. Proje, yapılandırılmış modüller aracılığıyla temel siber güvenlik kavramlarını öğreten, dokümantasyon tabanlı bir öğrenme kaynağıdır. Satıcıdan bağımsızdır ve her biri 30-60 dakika süren küçük dersler şeklinde tamamlanacak şekilde tasarlanmıştır.

**Ana Teknolojiler:**
- İçerik için Markdown
- Statik site oluşturma için Docsify
- Barındırma için GitHub Pages
- Çok dilli destek için Co-op Translator (50+ dil)
- CI/CD için GitHub Actions

**Mimari:**
- Her biri alt derslere sahip 8 ana modülde düzenlenmiş eğitim içeriği
- Markdown içeriğini işleyen Docsify ile statik HTML sitesi
- Azure AI hizmetlerini kullanarak otomatik çeviri iş akışı
- Çekirdek içerik için yapı araçları veya paket yöneticileri gerekmiyor

## Depo Yapısı

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

## Kurulum Komutları

Bu bir bağımlılık gerektirmeyen bir dokümantasyon projesidir. İçerikle çalışmak için:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Geliştirme İş Akışı

### İçeriği Yerel Olarak Görüntüleme

Proje, Docsify kullanarak içerik oluşturur. Değişiklikleri önizlemek için:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### İçerik Yapısı

Modüller sıralı olarak numaralandırılmıştır:
- **Modül 1:** Temel güvenlik kavramları (1.1-1.7)
- **Modül 2:** Kimlik ve erişim yönetimi (2.1-2.4)
- **Modül 3:** Ağ güvenliği (3.1-3.4)
- **Modül 4:** Güvenlik operasyonları (4.1-4.4)
- **Modül 5:** Uygulama güvenliği (5.1-5.3)
- **Modül 6:** Altyapı güvenliği (6.1-6.3)
- **Modül 7:** Veri güvenliği (7.1-7.3)
- **Modül 8:** Yapay zeka güvenliği (8.1-8.4)

Her modül, bir sınav dosyası ile sona erer (örneğin, "1.7 Modül sonu sınavı.md").

### İçerik Değişiklikleri Yapma

1. Markdown dosyalarını doğrudan kök dizinde düzenleyin
2. Mevcut adlandırma kurallarına uyun: `[modül].[ders] [Başlık].md`
3. Modül ekleme/çıkarma durumunda README.md tablosunu güncelleyin
4. Görselleri `/images/` dizinine ekleyin
5. Görselleri göreceli yollar kullanarak referans alın: `![Açıklama](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.tr.png)`

## Çeviri İş Akışı

**Otomatik Çeviri:**
- Çeviriler, Co-op Translator GitHub Action tarafından otomatik olarak gerçekleştirilir
- `main` dalına değişiklikler gönderildiğinde, iş akışı içeriği 50+ dile çevirir
- Çevrilen dosyalar `/translations/[language_code]/` dizininde saklanır
- Çeviri meta verileri YAML ön bilgisi olarak korunur

**Desteklenen Diller:** Arapça, Bengalce, Bulgarca, Burmaca, Çince (Basitleştirilmiş, Geleneksel), Hırvatça, Çekçe, Danca, Felemenkçe, Estonca, Fince, Fransızca, Almanca, Yunanca, İbranice, Hintçe, Macarca, Endonezce, İtalyanca, Japonca, Korece, Litvanca, Malayca, Marathi, Nepalce, Norveççe, Farsça, Lehçe, Portekizce, Pencapça, Rumence, Rusça, Sırpça, Slovakça, Slovence, İspanyolca, Svahili, İsveççe, Tagalog, Tamilce, Tayca, Türkçe, Ukraynaca, Urduca, Vietnamca ve daha fazlası.

**Çeviri dosyalarını manuel olarak düzenlemeyin** - otomatik iş akışı tarafından üzerine yazılacaktır.

## Kod Stili Yönergeleri

### Markdown Kuralları

- Standart Markdown sözdizimini kullanın
- Başlıklar: Ana başlık için `#`, bölümler için `##`, alt bölümler için `###` kullanın
- Listeler: Sırasız listeler için `-` veya `*`, sıralı listeler için `1.` kullanın
- Bağlantılar: Dersler arası referanslar için açıklayıcı metin ve tam GitHub URL'leri kullanın
- Görseller: `/images/` dizininde saklayın, açıklayıcı alt metin kullanın
- Kod blokları: Uygun olduğunda dil tanımlayıcı ile üçlü tırnak işareti kullanın

### İçerik Yönergeleri

- Dersleri odaklı ve özlü tutun (30-60 dakikalık okuma süresi)
- Açık, yeni başlayanlara uygun bir dil kullanın
- Satıcıya özgü araç talimatlarından kaçının (müfredat satıcıdan bağımsızdır)
- Her modülün başında öğrenme hedeflerini ekleyin
- Uygun olduğunda Microsoft Learn kaynaklarına bağlantı verin
- İçeriğin eğitici olmasını sağlayın, tanıtım amaçlı olmamalı

### Dosya Adlandırma

- Format kullanın: `[Modül].[Ders] [Başlık].md`
- Örnek: `1.1 CIA üçlüsü ve diğer anahtar kavramlar.md`
- Sınav dosyaları: `[Modül].[Son] Modül sonu sınavı.md`
- Dosya adlarında boşluk kullanın (mevcut kurala uygun olarak)

## GitHub İş Akışları

### Co-op Translator (co-op-translator.yml)

**Tetikleyici:** `main` dalına gönderim  
**Amaç:** Yeni/düzenlenmiş Markdown dosyalarını otomatik olarak 50+ dile çevirir

**Gerekli Ortam Değişkenleri:**
- Azure AI Hizmeti kimlik bilgileri (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI kimlik bilgileri (isteğe bağlı alternatif)
- OpenAI kimlik bilgileri (isteğe bağlı alternatif)

### Dağıtım (deploy.yaml)

**Tetikleyici:** README.md değiştiğinde `main` dalına gönderim  
**Amaç:** Statik siteyi GitHub Pages'e dağıtmak  
**Çıktı:** GitHub Pages sitesini günceller

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Tetikleyici:** Yapılandırılmış dalına gönderim  
**Amaç:** Jekyll kullanarak siteyi oluşturur ve dağıtır

## Çekme İsteği Yönergeleri

### Göndermeden Önce

1. **İçerik İncelemesi:** Siber güvenlik kavramlarının doğruluğunu ve açıklığını kontrol edin
2. **Formatlama:** Markdown formatının doğru şekilde görüntülendiğini doğrulayın
3. **Bağlantılar:** Tüm dahili ve harici bağlantıları test edin
4. **Görseller:** Tüm görsellerin yüklendiğinden ve açıklayıcı alt metinlere sahip olduğundan emin olun
5. **Tutarlılık:** Mevcut içerik yapısı ve stiline uyun

### Çekme İsteği Başlık Formatı

Açıklayıcı başlıklar kullanın:
- `Ekle: [Yeni içerik açıklaması]`
- `Güncelle: [Modül/Ders] - [Kısa açıklama]`
- `Düzelt: [Sorun açıklaması]`
- `Doküman: [Dokümantasyon değişiklikleri]`

### Gerekli Kontroller

- İçerik doğruluğu (manuel inceleme)
- Markdown formatlama doğrulaması
- Bağlantı doğrulaması
- Çeviri iş akışı tamamlanması (ana dal birleştirmeleri için)

### İnceleme Süreci

1. En az bir sorumlu tarafından inceleme yapılması gerekiyor
2. Siber güvenlik kavramlarının teknik doğruluğuna odaklanın
3. Erişilebilirlik ve yeni başlayanlara uygunluğu doğrulayın
4. Satıcı tarafsızlığının korunduğundan emin olun

## Yaygın Görevler

### Yeni Bir Ders Ekleme

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

### Mevcut İçeriği Güncelleme

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Görsel Ekleme

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.tr.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Test ve Doğrulama

### İçerik Doğrulama

Bu bir dokümantasyon projesi olduğundan, testler şu konulara odaklanır:

1. **Markdown İşleme:** Değişiklikleri yerel olarak Docsify kullanarak görüntüleyin
2. **Bağlantı Doğrulama:** Tüm bağlantılara manuel olarak tıklayın
3. **Görsel Yükleme:** Tüm görsellerin doğru şekilde görüntülendiğini doğrulayın
4. **Çeviri:** Dosyaların çevirmen iş akışı tarafından alındığını kontrol edin (otomatik)
5. **Erişilebilirlik:** Doğru başlık hiyerarşisi ve alt metinlerin olduğundan emin olun

### Yerel Önizleme

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Ön Taahhüt Kontrol Listesi

- [ ] Markdown dosyaları doğru sözdizimini kullanıyor
- [ ] Tüm bağlantılar geçerli ve mümkünse HTTPS kullanıyor
- [ ] Görseller açıklayıcı alt metinlere sahip
- [ ] İçerik yeni başlayanlara uygun ve doğru
- [ ] Satıcıdan bağımsız bir dil kullanılıyor
- [ ] Modül ekleme/çıkarma durumunda README.md güncellendi
- [ ] Dosya adlandırma kurallarına uyuluyor

## Güvenlik Hususları

- **İçerikte gizli bilgi yok:** API anahtarları, şifreler veya hassas veriler asla yüklenmemeli
- **Bağlantı doğrulama:** Tüm harici bağlantıların güvenilir kaynaklara olduğundan emin olun
- **Görsel içerik:** Görsellerin hassas bilgi içermediğini doğrulayın
- **Çeviri iş akışı:** Azure AI hizmetlerini uygun kimlik doğrulama ile kullanır
- **SECURITY.md:** SECURITY.md'deki güvenlik açığı raporlama sürecine uyun

## Ek Kaynaklar

### İlgili Microsoft Kursları

Bu müfredat, Microsoft eğitim kaynaklarının daha geniş bir koleksiyonunun parçasıdır:
- Yeni Başlayanlar için Üretken Yapay Zeka
- Yeni Başlayanlar için Yapay Zeka
- Yeni Başlayanlar için Veri Bilimi
- Yeni Başlayanlar için Makine Öğrenimi
- Yeni Başlayanlar için Web Geliştirme
- Yeni Başlayanlar için IoT

### Harici Öğrenme Yolları

Security-101'i tamamladıktan sonra:
- [Microsoft Güvenlik, Uyumluluk ve Kimlik Temelleri](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Sınav SC-900: Microsoft Güvenlik, Uyumluluk ve Kimlik Temelleri](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Katkıda Bulunma

1. **Depoyu çatallayın** GitHub'da
2. **Değişiklikleriniz için bir özellik dalı oluşturun**
3. **Değişikliklerinizi yapın** yukarıdaki yönergeleri takip ederek
4. **Yerel olarak test edin** her şeyin doğru şekilde görüntülendiğinden emin olun
5. **Açıklayıcı bir değişiklik açıklamasıyla çekme isteği gönderin**
6. **Sorumluların geri bildirimlerine yanıt verin**

## Yaygın Sorunlar ve Sorun Giderme

### Çeviriler Çalışmıyor

- Değişikliklerin `main` dalına gönderildiğinden emin olun
- GitHub Actions sekmesinde iş akışı durumunu kontrol edin
- Çeviri iş akışı için gerekli bilgilerin yapılandırıldığını doğrulayın
- Çeviri otomatik olarak gerçekleşir; çeviri dosyalarını manuel olarak düzenlemeyin

### Görseller Yüklenmiyor

- Görsel yolunun ileri eğik çizgi kullandığını doğrulayın: `images/filename.png`
- Görsel dosyasının depoya yüklendiğini kontrol edin
- Görsel dosya adının tam olarak eşleştiğinden emin olun (büyük/küçük harf duyarlı)
- Mutlak URL'ler yerine göreceli yollar kullanın

### Docsify İşlemiyor

- `index.html` dosyasının kök dizinde bulunduğunu kontrol edin
- Docsify CDN bağlantılarının erişilebilir olduğunu doğrulayın
- Markdown dosyalarının standart sözdizimini kullandığından emin olun
- Tarayıcı konsolunda JavaScript hatalarını kontrol edin

### Bağlantılar Çalışmıyor

- Dersler arası referanslar için tam GitHub URL'leri kullanın
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Bağlantıları yalnızca ham Markdown'da değil, işlenmiş görünümde test edin

## Proje Bakımı

### Düzenli Görevler

- Topluluk katkılarını gözden geçirin ve birleştirin
- Güvenlik ortamı geliştikçe içeriği doğruluk açısından güncelleyin
- Çeviri iş akışını hatalar için izleyin
- Sorulara ve tartışmalara yanıt verin
- Harici bağlantıları güncel tutun

### Sürüm Kontrolü

- `main` dalı korumalıdır ve PR incelemeleri gerektirir
- Tüm değişiklikler çekme isteği sürecinden geçer
- Çeviri dosyaları otomatik olarak oluşturulur, manuel olarak düzenlemeyin
- Anlamlı taahhüt mesajları kullanın

## AI Kodlama Ajanları için Notlar

- **Bu bir dokümantasyon projesidir** - kod kalitesinden ziyade içerik kalitesine odaklanın
- **Çeviri dosyalarını değiştirmeyin** - otomatik olarak oluşturulurlar
- **Dosya adlandırma kurallarını koruyun** - mevcut desenlere uygun olarak dosya adlarında boşluk kullanın
- **README.md'yi güncelleyin** modül ekleme/çıkarma durumunda tabloyu senkronize tutmak için
- **Yerel olarak test edin** PR göndermeden önce Markdown'ın doğru şekilde işlendiğinden emin olun
- **Mevcut içerik stilini takip edin** - yeni başlayanlara uygun, satıcıdan bağımsız bir ton koruyun
- **Yapı süreci gerekmez** - yerel geliştirme için basit bir HTTP sunucusu yeterlidir
- **Modül yapısına saygı gösterin** - her modül tutarlı bir numaralandırma ve organizasyona sahiptir

---

**Feragatname**:  
Bu belge, AI çeviri hizmeti [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstersek de, otomatik çevirilerin hata veya yanlışlıklar içerebileceğini lütfen unutmayın. Belgenin orijinal dili, yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanımından kaynaklanan yanlış anlamalar veya yanlış yorumlamalar için sorumluluk kabul etmiyoruz.