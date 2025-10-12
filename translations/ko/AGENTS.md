<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:29:15+00:00",
  "source_file": "AGENTS.md",
  "language_code": "ko"
}
-->
# AGENTS.md

## 프로젝트 개요

**Security-101**은 Microsoft에서 만든 초보자 친화적인 사이버 보안 커리큘럼입니다. 이 프로젝트는 문서 기반 학습 자료로, 구조화된 모듈을 통해 기본적인 사이버 보안 개념을 가르칩니다. 특정 벤더에 종속되지 않으며, 각 레슨은 30~60분 내에 완료할 수 있도록 설계되었습니다.

**주요 기술:**
- 콘텐츠 작성에 Markdown 사용
- Docsify를 통한 정적 사이트 생성
- GitHub Pages를 이용한 호스팅
- Co-op Translator를 통한 다국어 지원 (50개 이상의 언어)
- GitHub Actions를 이용한 CI/CD

**아키텍처:**
- 8개의 주요 모듈로 구성된 교육 콘텐츠, 각 모듈은 하위 레슨 포함
- Docsify가 Markdown 콘텐츠를 렌더링하는 정적 HTML 사이트
- Azure AI 서비스를 이용한 자동 번역 워크플로우
- 핵심 콘텐츠에는 빌드 도구나 패키지 매니저가 필요하지 않음

## 저장소 구조

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

## 설정 명령어

이 프로젝트는 문서 기반으로, 설치해야 할 종속성이 없습니다. 콘텐츠 작업을 위해:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## 개발 워크플로우

### 로컬에서 콘텐츠 보기

이 프로젝트는 Docsify를 사용하여 렌더링합니다. 변경 사항을 미리 보기 위해:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### 콘텐츠 구조

모듈은 순차적으로 번호가 매겨집니다:
- **모듈 1:** 기본 보안 개념 (1.1-1.7)
- **모듈 2:** ID 및 접근 관리 (2.1-2.4)
- **모듈 3:** 네트워크 보안 (3.1-3.4)
- **모듈 4:** 보안 운영 (4.1-4.4)
- **모듈 5:** 애플리케이션 보안 (5.1-5.3)
- **모듈 6:** 인프라 보안 (6.1-6.3)
- **모듈 7:** 데이터 보안 (7.1-7.3)
- **모듈 8:** AI 보안 (8.1-8.4)

각 모듈은 퀴즈 파일로 끝납니다 (예: "1.7 End of module quiz.md").

### 콘텐츠 변경 방법

1. 루트 디렉토리에서 Markdown 파일을 직접 편집
2. 기존 이름 규칙을 따름: `[module].[lesson] [Title].md`
3. 모듈 추가/삭제 시 README.md 테이블 업데이트
4. 이미지는 `/images/` 디렉토리에 추가
5. 상대 경로를 사용하여 이미지 참조: `![설명](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.ko.png)`

## 번역 워크플로우

**자동 번역:**
- 번역은 Co-op Translator GitHub Action에 의해 자동으로 처리됩니다
- `main` 브랜치에 변경 사항을 푸시하면 워크플로우가 콘텐츠를 50개 이상의 언어로 번역합니다
- 번역된 파일은 `/translations/[language_code]/`에 저장됩니다
- 번역 메타데이터는 YAML frontmatter에 보존됩니다

**지원 언어:** 아랍어, 벵골어, 불가리아어, 버마어, 중국어(간체, 번체), 크로아티아어, 체코어, 덴마크어, 네덜란드어, 에스토니아어, 핀란드어, 프랑스어, 독일어, 그리스어, 히브리어, 힌디어, 헝가리어, 인도네시아어, 이탈리아어, 일본어, 한국어, 리투아니아어, 말레이어, 마라티어, 네팔어, 노르웨이어, 페르시아어, 폴란드어, 포르투갈어, 펀자브어, 루마니아어, 러시아어, 세르비아어, 슬로바키아어, 슬로베니아어, 스페인어, 스와힐리어, 스웨덴어, 타갈로그어, 타밀어, 태국어, 터키어, 우크라이나어, 우르두어, 베트남어 등.

**번역 파일을 수동으로 편집하지 마십시오** - 자동 워크플로우에 의해 덮어쓰여질 것입니다.

## 코드 스타일 가이드라인

### Markdown 규칙

- 표준 Markdown 문법 사용
- 제목: 메인 타이틀에는 `#`, 섹션에는 `##`, 하위 섹션에는 `###` 사용
- 목록: 순서 없는 목록에는 `-` 또는 `*`, 순서 있는 목록에는 `1.` 사용
- 링크: 설명 텍스트와 전체 GitHub URL을 사용하여 교차 참조
- 이미지: `/images/` 디렉토리에 저장하고 설명적인 alt 텍스트 사용
- 코드 블록: 가능하면 언어 식별자를 사용하여 삼중 백틱으로 표시

### 콘텐츠 가이드라인

- 레슨은 집중적이고 간결하게 유지 (30~60분 읽기 시간)
- 명확하고 초보자 친화적인 언어 사용
- 특정 벤더 도구 지침은 피함 (커리큘럼은 벤더에 종속되지 않음)
- 각 모듈 시작 시 학습 목표 포함
- 적절한 경우 외부 Microsoft Learn 리소스 링크 추가
- 교육적이고 홍보적이지 않은 콘텐츠 보장

### 파일 이름 규칙

- 형식: `[Module].[Lesson] [Title].md`
- 예: `1.1 The CIA triad and other key concepts.md`
- 퀴즈 파일: `[Module].[Last] End of module quiz.md`
- 파일 이름에 공백 사용 (기존 규칙)

## GitHub 워크플로우

### Co-op Translator (co-op-translator.yml)

**트리거:** `main` 브랜치에 푸시  
**목적:** 새로 추가되거나 수정된 Markdown 파일을 50개 이상의 언어로 자동 번역

**필요한 환경 변수:**
- Azure AI 서비스 자격 증명 (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI 자격 증명 (선택적 대안)
- OpenAI 자격 증명 (선택적 대안)

### 배포 (deploy.yaml)

**트리거:** README.md 변경 시 `main` 브랜치에 푸시  
**목적:** 정적 사이트를 GitHub Pages에 배포  
**출력:** GitHub Pages 사이트 업데이트

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**트리거:** 설정된 브랜치에 푸시  
**목적:** Jekyll을 사용하여 사이트 빌드 및 배포

## Pull Request 가이드라인

### 제출 전

1. **콘텐츠 검토:** 사이버 보안 개념의 정확성과 명확성 확인
2. **포맷팅:** Markdown 포맷팅이 올바르게 렌더링되는지 확인
3. **링크:** 모든 내부 및 외부 링크 테스트
4. **이미지:** 모든 이미지가 로드되고 설명적인 alt 텍스트가 있는지 확인
5. **일관성:** 기존 콘텐츠 구조와 스타일 준수

### PR 제목 형식

설명적인 제목 사용:
- `Add: [새 콘텐츠 설명]`
- `Update: [모듈/레슨] - [간단한 설명]`
- `Fix: [문제 설명]`
- `Docs: [문서 변경 사항]`

### 필수 확인 사항

- 콘텐츠 정확성 (수동 검토)
- Markdown 포맷팅 유효성 검사
- 링크 검증
- 번역 워크플로우 완료 (for `main` 브랜치 병합)

### 검토 프로세스

1. 최소 한 명의 유지 관리자가 검토 필요
2. 보안 개념의 기술적 정확성에 중점
3. 접근성과 초보자 친화성 확인
4. 벤더 중립성 유지 보장

## 일반 작업

### 새 레슨 추가

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

### 기존 콘텐츠 업데이트

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### 이미지 추가

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.ko.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## 테스트 및 검증

### 콘텐츠 검증

이 프로젝트는 문서 기반이므로 테스트는 다음에 중점을 둡니다:

1. **Markdown 렌더링:** Docsify를 사용하여 로컬에서 변경 사항 보기
2. **링크 검증:** 모든 링크를 수동으로 클릭하여 확인
3. **이미지 로딩:** 모든 이미지가 올바르게 표시되는지 확인
4. **번역:** 번역 워크플로우가 파일을 선택했는지 확인 (자동화됨)
5. **접근성:** 올바른 제목 계층 구조와 alt 텍스트 보장

### 로컬 미리보기

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### 커밋 전 체크리스트

- [ ] Markdown 파일이 올바른 문법을 사용했는지 확인
- [ ] 모든 링크가 유효하며 가능한 경우 HTTPS를 사용하는지 확인
- [ ] 이미지에 설명적인 alt 텍스트가 있는지 확인
- [ ] 콘텐츠가 초보자 친화적이고 정확한지 확인
- [ ] 벤더 중립적 언어가 유지되었는지 확인
- [ ] 모듈 추가/삭제 시 README.md 업데이트
- [ ] 파일 이름이 규칙을 따르는지 확인

## 보안 고려 사항

- **콘텐츠에 비밀 정보 없음:** API 키, 비밀번호 또는 민감한 데이터를 커밋하지 않음
- **링크 검증:** 모든 외부 링크가 신뢰할 수 있는 소스로 연결되는지 확인
- **이미지 콘텐츠:** 이미지에 민감한 정보가 포함되지 않았는지 확인
- **번역 워크플로우:** 적절한 인증을 사용하여 Azure AI 서비스 활용
- **SECURITY.md:** SECURITY.md의 취약점 보고 프로세스 준수

## 추가 리소스

### 관련 Microsoft 강좌

이 커리큘럼은 Microsoft 교육 리소스의 일부입니다:
- 초보자를 위한 생성형 AI
- 초보자를 위한 AI
- 초보자를 위한 데이터 과학
- 초보자를 위한 머신 러닝
- 초보자를 위한 웹 개발
- 초보자를 위한 IoT

### 외부 학습 경로

Security-101 완료 후:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## 기여 방법

1. GitHub에서 **저장소를 포크**합니다
2. 변경 사항을 위한 **기능 브랜치 생성**
3. 위 가이드라인을 따라 **변경 사항 적용**
4. **로컬 테스트**를 통해 모든 것이 올바르게 렌더링되는지 확인
5. **명확한 변경 설명**과 함께 Pull Request 제출
6. 유지 관리자의 **피드백에 응답**

## 일반적인 문제 및 문제 해결

### 번역이 작동하지 않음

- 변경 사항이 `main` 브랜치에 푸시되었는지 확인
- GitHub Actions 탭에서 워크플로우 상태 확인
- 번역 워크플로우 비밀이 구성되었는지 확인
- 번역은 자동으로 이루어지며 번역 파일을 수동으로 편집하지 마십시오

### 이미지가 로드되지 않음

- 이미지 경로가 슬래시를 사용했는지 확인: `images/filename.png`
- 이미지 파일이 저장소에 커밋되었는지 확인
- 이미지 파일 이름이 정확히 일치하는지 확인 (대소문자 구분)
- 절대 URL이 아닌 상대 경로 사용

### Docsify가 렌더링되지 않음

- 루트에 `index.html`이 있는지 확인
- Docsify CDN 링크가 접근 가능한지 확인
- Markdown 파일이 표준 문법을 사용하는지 확인
- 브라우저 콘솔에서 JavaScript 오류 확인

### 링크가 작동하지 않음

- 레슨 간 교차 참조를 위해 전체 GitHub URL 사용
- 형식: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- 렌더링된 보기에서 링크를 테스트, 원시 Markdown에서만 테스트하지 않음

## 프로젝트 유지 관리

### 정기 작업

- 커뮤니티 기여 검토 및 병합
- 보안 환경 변화에 따라 콘텐츠 정확성 업데이트
- 번역 워크플로우 오류 모니터링
- 문제 및 논의에 응답
- 외부 링크 최신 상태 유지

### 버전 관리

- `main` 브랜치는 보호되며 PR 검토가 필요
- 모든 변경 사항은 Pull Request 프로세스를 거침
- 번역 파일은 자동 생성되며 수동으로 편집하지 않음
- 의미 있는 커밋 메시지 사용

## AI 코딩 에이전트를 위한 참고 사항

- **이 프로젝트는 문서 기반입니다** - 코드가 아닌 콘텐츠 품질에 집중
- **번역 파일을 수정하지 마십시오** - 자동 생성됩니다
- **파일 이름 규칙을 준수하십시오** - 기존 패턴에 따라 파일 이름에 공백 사용
- **README.md 업데이트** - 모듈 추가/삭제 시 테이블 동기화 유지
- **로컬 테스트** - PR 제출 전에 Markdown이 올바르게 렌더링되는지 확인
- **기존 콘텐츠 스타일 준수** - 초보자 친화적이고 벤더 중립적 톤 유지
- **빌드 프로세스 필요 없음** - 로컬 개발에는 간단한 HTTP 서버로 충분
- **모듈 구조 준수** - 각 모듈은 일관된 번호 매기기와 조직을 가짐

---

**면책 조항**:  
이 문서는 AI 번역 서비스 [Co-op Translator](https://github.com/Azure/co-op-translator)를 사용하여 번역되었습니다. 정확성을 위해 최선을 다하고 있으나, 자동 번역에는 오류나 부정확성이 포함될 수 있습니다. 원본 문서의 원어 버전을 권위 있는 자료로 간주해야 합니다. 중요한 정보의 경우, 전문적인 인간 번역을 권장합니다. 이 번역 사용으로 인해 발생하는 오해나 잘못된 해석에 대해 당사는 책임을 지지 않습니다.