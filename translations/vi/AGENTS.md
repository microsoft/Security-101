<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:40:17+00:00",
  "source_file": "AGENTS.md",
  "language_code": "vi"
}
-->
# AGENTS.md

## Tổng quan dự án

**Security-101** là một chương trình học an ninh mạng dành cho người mới bắt đầu được Microsoft tạo ra. Dự án này là một tài liệu học tập giúp giảng dạy các khái niệm cơ bản về an ninh mạng thông qua các mô-đun có cấu trúc. Nó không phụ thuộc vào nhà cung cấp cụ thể và được thiết kế để hoàn thành trong các bài học nhỏ (mỗi bài từ 30-60 phút).

**Công nghệ chính:**
- Markdown để tạo nội dung
- Docsify để tạo trang tĩnh
- GitHub Pages để lưu trữ
- Co-op Translator để hỗ trợ đa ngôn ngữ (hơn 50 ngôn ngữ)
- GitHub Actions cho CI/CD

**Kiến trúc:**
- Nội dung giáo dục được tổ chức thành 8 mô-đun chính, mỗi mô-đun có các bài học nhỏ
- Trang web HTML tĩnh với Docsify hiển thị nội dung Markdown
- Quy trình dịch tự động sử dụng dịch vụ Azure AI
- Không yêu cầu công cụ build hoặc trình quản lý gói cho nội dung cốt lõi

## Cấu trúc kho lưu trữ

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

## Lệnh thiết lập

Đây là một dự án tài liệu không yêu cầu cài đặt phụ thuộc. Để làm việc với nội dung:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Quy trình phát triển

### Xem nội dung cục bộ

Dự án sử dụng Docsify để hiển thị. Để xem trước các thay đổi:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Cấu trúc nội dung

Các mô-đun được đánh số tuần tự:
- **Mô-đun 1:** Các khái niệm cơ bản về an ninh (1.1-1.7)
- **Mô-đun 2:** Quản lý danh tính & truy cập (2.1-2.4)
- **Mô-đun 3:** An ninh mạng (3.1-3.4)
- **Mô-đun 4:** Hoạt động an ninh (4.1-4.4)
- **Mô-đun 5:** An ninh ứng dụng (5.1-5.3)
- **Mô-đun 6:** An ninh hạ tầng (6.1-6.3)
- **Mô-đun 7:** An ninh dữ liệu (7.1-7.3)
- **Mô-đun 8:** An ninh AI (8.1-8.4)

Mỗi mô-đun kết thúc bằng một tệp câu hỏi kiểm tra (ví dụ: "1.7 End of module quiz.md").

### Thay đổi nội dung

1. Chỉnh sửa các tệp Markdown trực tiếp trong thư mục gốc
2. Tuân theo quy ước đặt tên hiện có: `[module].[lesson] [Title].md`
3. Cập nhật bảng trong README.md nếu thêm/xóa mô-đun
4. Thêm hình ảnh vào thư mục `/images/`
5. Tham chiếu hình ảnh bằng đường dẫn tương đối: `![Mô tả](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.vi.png)`

## Quy trình dịch thuật

**Dịch tự động:**
- Các bản dịch được xử lý tự động bởi Co-op Translator GitHub Action
- Khi bạn đẩy thay đổi lên nhánh `main`, quy trình sẽ dịch nội dung sang hơn 50 ngôn ngữ
- Các tệp dịch được lưu trữ trong `/translations/[language_code]/`
- Siêu dữ liệu dịch được bảo toàn trong YAML frontmatter

**Ngôn ngữ được hỗ trợ:** Tiếng Ả Rập, Bengali, Bulgaria, Miến Điện, Trung Quốc (Giản thể, Phồn thể), Croatia, Séc, Đan Mạch, Hà Lan, Estonia, Phần Lan, Pháp, Đức, Hy Lạp, Do Thái, Hindi, Hungary, Indonesia, Ý, Nhật Bản, Hàn Quốc, Litva, Mã Lai, Marathi, Nepal, Na Uy, Ba Tư, Ba Lan, Bồ Đào Nha, Punjabi, Romania, Nga, Serbia, Slovak, Slovenia, Tây Ban Nha, Swahili, Thụy Điển, Tagalog, Tamil, Thái, Thổ Nhĩ Kỳ, Ukraina, Urdu, Việt Nam, và nhiều ngôn ngữ khác.

**Không chỉnh sửa thủ công các tệp dịch** - chúng sẽ bị ghi đè bởi quy trình tự động.

## Hướng dẫn phong cách mã

### Quy ước Markdown

- Sử dụng cú pháp Markdown tiêu chuẩn
- Tiêu đề: Sử dụng `#` cho tiêu đề chính, `##` cho các phần, `###` cho các phần con
- Danh sách: Sử dụng `-` hoặc `*` cho danh sách không thứ tự, `1.` cho danh sách có thứ tự
- Liên kết: Sử dụng văn bản mô tả với URL GitHub đầy đủ cho các tham chiếu chéo
- Hình ảnh: Lưu trữ trong thư mục `/images/`, sử dụng văn bản thay thế mô tả
- Khối mã: Sử dụng ba dấu backtick với định danh ngôn ngữ khi áp dụng

### Hướng dẫn nội dung

- Giữ bài học tập trung và ngắn gọn (thời gian đọc 30-60 phút)
- Sử dụng ngôn ngữ rõ ràng, thân thiện với người mới bắt đầu
- Tránh hướng dẫn công cụ cụ thể của nhà cung cấp (chương trình học không phụ thuộc nhà cung cấp)
- Bao gồm mục tiêu học tập ở đầu mỗi mô-đun
- Liên kết đến các tài nguyên Microsoft Learn bên ngoài khi phù hợp
- Đảm bảo nội dung mang tính giáo dục, không mang tính quảng cáo

### Quy ước đặt tên tệp

- Sử dụng định dạng: `[Module].[Lesson] [Title].md`
- Ví dụ: `1.1 The CIA triad and other key concepts.md`
- Tệp câu hỏi: `[Module].[Last] End of module quiz.md`
- Sử dụng khoảng trắng trong tên tệp (theo quy ước hiện có)

## Quy trình GitHub

### Co-op Translator (co-op-translator.yml)

**Kích hoạt:** Đẩy lên nhánh `main`  
**Mục đích:** Tự động dịch các tệp Markdown mới/sửa đổi sang hơn 50 ngôn ngữ

**Biến môi trường cần thiết:**
- Thông tin xác thực dịch vụ Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Thông tin xác thực Azure OpenAI (tùy chọn thay thế)
- Thông tin xác thực OpenAI (tùy chọn thay thế)

### Deploy (deploy.yaml)

**Kích hoạt:** Đẩy lên nhánh `main` khi README.md thay đổi  
**Mục đích:** Triển khai trang tĩnh lên GitHub Pages  
**Kết quả:** Cập nhật trang GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Kích hoạt:** Đẩy lên nhánh được cấu hình  
**Mục đích:** Xây dựng và triển khai trang bằng Jekyll

## Hướng dẫn Pull Request

### Trước khi gửi

1. **Xem xét nội dung:** Đảm bảo tính chính xác và rõ ràng của các khái niệm an ninh mạng
2. **Định dạng:** Xác minh định dạng Markdown hiển thị đúng
3. **Liên kết:** Kiểm tra tất cả các liên kết nội bộ và bên ngoài
4. **Hình ảnh:** Đảm bảo tất cả hình ảnh tải được và có văn bản thay thế mô tả
5. **Tính nhất quán:** Tuân theo cấu trúc và phong cách nội dung hiện có

### Định dạng tiêu đề PR

Sử dụng tiêu đề mô tả:
- `Add: [Mô tả nội dung mới]`
- `Update: [Module/Lesson] - [Mô tả ngắn gọn]`
- `Fix: [Mô tả vấn đề]`
- `Docs: [Thay đổi tài liệu]`

### Kiểm tra bắt buộc

- Tính chính xác nội dung (xem xét thủ công)
- Xác thực định dạng Markdown
- Xác minh liên kết
- Hoàn thành quy trình dịch thuật (đối với các lần gộp vào nhánh `main`)

### Quy trình xem xét

1. Yêu cầu ít nhất một người duyệt từ nhóm bảo trì
2. Tập trung vào tính chính xác kỹ thuật của các khái niệm an ninh
3. Xác minh khả năng tiếp cận và tính thân thiện với người mới bắt đầu
4. Đảm bảo tính trung lập với nhà cung cấp

## Nhiệm vụ phổ biến

### Thêm bài học mới

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

### Cập nhật nội dung hiện có

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Thêm hình ảnh

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.vi.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Kiểm tra và xác thực

### Xác thực nội dung

Vì đây là một dự án tài liệu, việc kiểm tra tập trung vào:

1. **Hiển thị Markdown:** Xem các thay đổi cục bộ bằng Docsify
2. **Xác minh liên kết:** Nhấp qua tất cả các liên kết thủ công
3. **Tải hình ảnh:** Xác minh tất cả hình ảnh hiển thị đúng
4. **Dịch thuật:** Kiểm tra rằng các tệp được quy trình dịch thuật nhận diện (tự động)
5. **Khả năng tiếp cận:** Đảm bảo cấu trúc tiêu đề hợp lý và văn bản thay thế

### Xem trước cục bộ

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Danh sách kiểm tra trước khi commit

- [ ] Các tệp Markdown sử dụng cú pháp đúng
- [ ] Tất cả các liên kết hợp lệ và sử dụng HTTPS nếu có thể
- [ ] Hình ảnh có văn bản thay thế mô tả
- [ ] Nội dung thân thiện với người mới bắt đầu và chính xác
- [ ] Ngôn ngữ trung lập với nhà cung cấp được duy trì
- [ ] README.md được cập nhật nếu thêm/xóa mô-đun
- [ ] Tên tệp tuân theo quy ước

## Cân nhắc về an ninh

- **Không có thông tin bí mật trong nội dung:** Không bao giờ commit khóa API, mật khẩu hoặc dữ liệu nhạy cảm
- **Xác minh liên kết:** Đảm bảo tất cả các liên kết bên ngoài dẫn đến nguồn đáng tin cậy
- **Nội dung hình ảnh:** Xác minh hình ảnh không chứa thông tin nhạy cảm
- **Quy trình dịch thuật:** Sử dụng dịch vụ Azure AI với xác thực đúng
- **SECURITY.md:** Tuân theo quy trình báo cáo lỗ hổng trong SECURITY.md

## Tài nguyên bổ sung

### Các khóa học liên quan của Microsoft

Chương trình học này là một phần của bộ sưu tập tài nguyên giáo dục lớn hơn của Microsoft:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Lộ trình học tập bên ngoài

Sau khi hoàn thành Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Đóng góp

1. **Fork kho lưu trữ** trên GitHub
2. **Tạo nhánh tính năng** cho các thay đổi của bạn
3. **Thực hiện thay đổi** theo các hướng dẫn ở trên
4. **Kiểm tra cục bộ** để đảm bảo mọi thứ hiển thị đúng
5. **Gửi pull request** với mô tả rõ ràng về các thay đổi
6. **Phản hồi ý kiến** từ nhóm bảo trì

## Các vấn đề phổ biến và cách khắc phục

### Dịch thuật không hoạt động

- Đảm bảo các thay đổi được đẩy lên nhánh `main`
- Kiểm tra tab GitHub Actions để xem trạng thái quy trình
- Xác minh cấu hình bí mật của quy trình dịch thuật
- Dịch thuật diễn ra tự động; không chỉnh sửa thủ công các tệp dịch

### Hình ảnh không tải

- Xác minh đường dẫn hình ảnh sử dụng dấu gạch chéo: `images/filename.png`
- Kiểm tra rằng tệp hình ảnh đã được commit vào kho lưu trữ
- Đảm bảo tên tệp hình ảnh khớp chính xác (phân biệt chữ hoa chữ thường)
- Sử dụng đường dẫn tương đối, không sử dụng URL tuyệt đối

### Docsify không hiển thị

- Kiểm tra rằng `index.html` có trong thư mục gốc
- Xác minh các liên kết CDN của Docsify có thể truy cập
- Đảm bảo các tệp Markdown sử dụng cú pháp tiêu chuẩn
- Kiểm tra bảng điều khiển trình duyệt để tìm lỗi JavaScript

### Liên kết không hoạt động

- Sử dụng URL GitHub đầy đủ cho các tham chiếu chéo giữa các bài học
- Định dạng: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Kiểm tra liên kết trong chế độ xem hiển thị, không chỉ trong Markdown thô

## Bảo trì dự án

### Nhiệm vụ thường xuyên

- Xem xét và hợp nhất các đóng góp từ cộng đồng
- Cập nhật nội dung để đảm bảo tính chính xác khi bối cảnh an ninh thay đổi
- Giám sát quy trình dịch thuật để phát hiện lỗi
- Phản hồi các vấn đề và thảo luận
- Giữ các liên kết bên ngoài luôn cập nhật

### Quản lý phiên bản

- Nhánh `main` được bảo vệ và yêu cầu xem xét PR
- Tất cả các thay đổi phải thông qua quy trình pull request
- Các tệp dịch được tạo tự động, không chỉnh sửa thủ công
- Sử dụng thông điệp commit có ý nghĩa

## Ghi chú cho các tác nhân AI Coding

- **Đây là một dự án tài liệu** - tập trung vào chất lượng nội dung, không phải mã
- **Không chỉnh sửa các tệp dịch** - chúng được tạo tự động
- **Bảo toàn quy ước đặt tên tệp** - sử dụng khoảng trắng trong tên tệp theo mẫu hiện có
- **Cập nhật README.md** khi thêm/xóa mô-đun để giữ bảng đồng bộ
- **Kiểm tra cục bộ** trước khi gửi PR để đảm bảo Markdown hiển thị đúng
- **Tuân theo phong cách nội dung hiện có** - duy trì giọng điệu thân thiện với người mới bắt đầu, trung lập với nhà cung cấp
- **Không yêu cầu quy trình build** - máy chủ HTTP đơn giản là đủ cho phát triển cục bộ
- **Tôn trọng cấu trúc mô-đun** - mỗi mô-đun có số thứ tự và tổ chức nhất quán

---

**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ bản địa nên được coi là nguồn thông tin chính thức. Đối với các thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp của con người. Chúng tôi không chịu trách nhiệm cho bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.