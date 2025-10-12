<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:28:41+00:00",
  "source_file": "AGENTS.md",
  "language_code": "ja"
}
-->
# AGENTS.md

## プロジェクト概要

**Security-101**は、Microsoftが提供する初心者向けのサイバーセキュリティカリキュラムです。このプロジェクトは、構造化されたモジュールを通じて基本的なサイバーセキュリティの概念を学べるドキュメントベースの学習リソースです。特定のベンダーに依存せず、30～60分程度の短いレッスンで完了できるよう設計されています。

**主な技術:**
- コンテンツ作成にMarkdownを使用
- Docsifyによる静的サイト生成
- GitHub Pagesでホスティング
- Co-op Translatorによる多言語対応（50以上の言語）
- GitHub ActionsによるCI/CD

**アーキテクチャ:**
- 教育コンテンツは8つの主要モジュールに整理され、それぞれにサブレッスンが含まれる
- DocsifyがMarkdownコンテンツをレンダリングする静的HTMLサイト
- Azure AIサービスを使用した自動翻訳ワークフロー
- コアコンテンツにはビルドツールやパッケージマネージャは不要

## リポジトリ構造

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

## セットアップコマンド

このプロジェクトはドキュメントベースであり、インストールする依存関係はありません。コンテンツを操作するには以下を実行してください:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## 開発ワークフロー

### ローカルでコンテンツを表示

このプロジェクトはDocsifyを使用してレンダリングします。変更をプレビューするには:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### コンテンツ構造

モジュールは順番に番号付けされています:
- **モジュール1:** 基本的なセキュリティ概念 (1.1-1.7)
- **モジュール2:** アイデンティティとアクセス管理 (2.1-2.4)
- **モジュール3:** ネットワークセキュリティ (3.1-3.4)
- **モジュール4:** セキュリティ運用 (4.1-4.4)
- **モジュール5:** アプリケーションセキュリティ (5.1-5.3)
- **モジュール6:** インフラセキュリティ (6.1-6.3)
- **モジュール7:** データセキュリティ (7.1-7.3)
- **モジュール8:** AIセキュリティ (8.1-8.4)

各モジュールの最後にはクイズファイルがあります（例: "1.7 End of module quiz.md"）。

### コンテンツ変更の手順

1. ルートディレクトリ内でMarkdownファイルを直接編集
2. 既存の命名規則に従う: `[module].[lesson] [Title].md`
3. モジュールを追加または削除する場合はREADME.mdの表を更新
4. 画像は`/images/`ディレクトリに追加
5. 相対パスを使用して画像を参照: `![説明](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.ja.png)`

## 翻訳ワークフロー

**自動翻訳:**
- 翻訳はCo-op Translator GitHub Actionによって自動的に処理されます
- `main`ブランチに変更をプッシュすると、ワークフローがコンテンツを50以上の言語に翻訳します
- 翻訳されたファイルは`/translations/[language_code]/`に保存されます
- 翻訳メタデータはYAMLフロントマターに保持されます

**対応言語:** アラビア語、ベンガル語、ブルガリア語、ビルマ語、中国語（簡体字、繁体字）、クロアチア語、チェコ語、デンマーク語、オランダ語、エストニア語、フィンランド語、フランス語、ドイツ語、ギリシャ語、ヘブライ語、ヒンディー語、ハンガリー語、インドネシア語、イタリア語、日本語、韓国語、リトアニア語、マレー語、マラーティー語、ネパール語、ノルウェー語、ペルシャ語、ポーランド語、ポルトガル語、パンジャブ語、ルーマニア語、ロシア語、セルビア語、スロバキア語、スロベニア語、スペイン語、スワヒリ語、スウェーデン語、タガログ語、タミル語、タイ語、トルコ語、ウクライナ語、ウルドゥー語、ベトナム語など。

**翻訳ファイルを手動で編集しないでください** - 自動ワークフローによって上書きされます。

## コードスタイルガイドライン

### Markdownの規則

- 標準的なMarkdown構文を使用
- 見出し: メインタイトルには`#`、セクションには`##`、サブセクションには`###`を使用
- リスト: 箇条書きには`-`または`*`、番号付きリストには`1.`を使用
- リンク: 説明的なテキストと完全なGitHub URLを使用してクロスリファレンスを作成
- 画像: `/images/`ディレクトリに保存し、説明的なaltテキストを使用
- コードブロック: 必要に応じて言語識別子付きの三重バックティックを使用

### コンテンツガイドライン

- レッスンは集中し、簡潔に（30～60分で読める内容）
- 明確で初心者に優しい言葉を使用
- ベンダー固有のツールの説明を避ける（カリキュラムはベンダーに依存しない）
- 各モジュールの冒頭に学習目標を含める
- 適切な場合はMicrosoft Learnの外部リソースへのリンクを追加
- コンテンツは教育的であり、宣伝的でないことを確認

### ファイル命名

- フォーマット: `[Module].[Lesson] [Title].md`
- 例: `1.1 The CIA triad and other key concepts.md`
- クイズファイル: `[Module].[Last] End of module quiz.md`
- ファイル名にはスペースを使用（既存の規則に従う）

## GitHubワークフロー

### Co-op Translator (co-op-translator.yml)

**トリガー:** `main`ブランチへのプッシュ  
**目的:** 新規または変更されたMarkdownファイルを50以上の言語に自動翻訳

**必要な環境変数:**
- Azure AIサービスの認証情報 (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI認証情報（オプションの代替）
- OpenAI認証情報（オプションの代替）

### デプロイ (deploy.yaml)

**トリガー:** README.mdが変更された際の`main`ブランチへのプッシュ  
**目的:** 静的サイトをGitHub Pagesにデプロイ  
**出力:** GitHub Pagesサイトの更新

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**トリガー:** 設定されたブランチへのプッシュ  
**目的:** Jekyllを使用してサイトをビルドおよびデプロイ

## プルリクエストガイドライン

### 提出前

1. **コンテンツレビュー:** サイバーセキュリティの概念の正確性と明確性を確認
2. **フォーマット:** Markdownのフォーマットが正しくレンダリングされることを確認
3. **リンク:** すべての内部および外部リンクをテスト
4. **画像:** すべての画像が読み込まれ、説明的なaltテキストがあることを確認
5. **一貫性:** 既存のコンテンツ構造とスタイルに従う

### PRタイトルフォーマット

説明的なタイトルを使用:
- `Add: [新しいコンテンツの説明]`
- `Update: [モジュール/レッスン] - [簡単な説明]`
- `Fix: [問題の説明]`
- `Docs: [ドキュメントの変更]`

### 必須チェック

- コンテンツの正確性（手動レビュー）
- Markdownフォーマットの検証
- リンクの確認
- 翻訳ワークフローの完了（`main`ブランチへのマージ時）

### レビュープロセス

1. 少なくとも1人のメンテナーによるレビューが必要
2. セキュリティ概念の技術的正確性に重点を置く
3. アクセシビリティと初心者向けの内容を確認
4. ベンダー中立性が維持されていることを確認

## 共通タスク

### 新しいレッスンの追加

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

### 既存コンテンツの更新

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### 画像の追加

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.ja.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## テストと検証

### コンテンツ検証

このプロジェクトはドキュメントベースであるため、テストは以下に重点を置きます:

1. **Markdownレンダリング:** Docsifyを使用してローカルで変更を表示
2. **リンク検証:** すべてのリンクを手動でクリックして確認
3. **画像の読み込み:** すべての画像が正しく表示されることを確認
4. **翻訳:** 翻訳ワークフローがファイルを検出することを確認（自動）
5. **アクセシビリティ:** 適切な見出し階層とaltテキストを確認

### ローカルプレビュー

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### コミット前チェックリスト

- [ ] Markdownファイルが正しい構文を使用している
- [ ] すべてのリンクが有効であり、可能な限りHTTPSを使用している
- [ ] 画像に説明的なaltテキストがある
- [ ] コンテンツが初心者向けで正確である
- [ ] ベンダー中立的な言語が維持されている
- [ ] モジュールを追加または削除する場合はREADME.mdを更新
- [ ] ファイル命名が規則に従っている

## セキュリティに関する考慮事項

- **コンテンツに秘密情報を含めない:** APIキー、パスワード、機密データをコミットしない
- **リンク検証:** すべての外部リンクが信頼できるソースであることを確認
- **画像コンテンツ:** 画像に機密情報が含まれていないことを確認
- **翻訳ワークフロー:** 適切な認証を使用してAzure AIサービスを利用
- **SECURITY.md:** SECURITY.mdに記載された脆弱性報告プロセスに従う

## 追加リソース

### 関連するMicrosoftコース

このカリキュラムはMicrosoftの教育リソースの一部です:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### 外部学習パス

Security-101修了後:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## コントリビューション

1. **リポジトリをフォーク**する（GitHub上で）
2. **フィーチャーブランチを作成**して変更を行う
3. **変更を加える**（上記のガイドラインに従う）
4. **ローカルでテスト**してすべてが正しくレンダリングされることを確認
5. **プルリクエストを提出**し、変更内容を明確に記述
6. **メンテナーからのフィードバックに対応**

## よくある問題とトラブルシューティング

### 翻訳が機能しない

- 変更が`main`ブランチにプッシュされていることを確認
- GitHub Actionsタブでワークフローのステータスを確認
- 翻訳ワークフローの秘密情報が設定されていることを確認
- 翻訳は自動的に行われるため、翻訳ファイルを手動で編集しないでください

### 画像が読み込まれない

- 画像パスがスラッシュを使用していることを確認: `images/filename.png`
- 画像ファイルがリポジトリにコミットされていることを確認
- 画像ファイル名が完全に一致していることを確認（大文字小文字を区別）
- 絶対URLではなく相対パスを使用

### Docsifyがレンダリングされない

- `index.html`がルートに存在することを確認
- Docsify CDNリンクがアクセス可能であることを確認
- Markdownファイルが標準的な構文を使用していることを確認
- ブラウザコンソールでJavaScriptエラーを確認

### リンクが機能しない

- レッスン間のクロスリファレンスには完全なGitHub URLを使用
- フォーマット: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- 生のMarkdownではなくレンダリングされたビューでリンクをテスト

## プロジェクトの保守

### 定期的なタスク

- コミュニティからのコントリビューションをレビューおよびマージ
- セキュリティの状況に応じてコンテンツを更新
- 翻訳ワークフローのエラーを監視
- 問題やディスカッションに対応
- 外部リンクを最新の状態に保つ

### バージョン管理

- `main`ブランチは保護されており、PRレビューが必要
- すべての変更はプルリクエストプロセスを通じて行われる
- 翻訳ファイルは自動生成されるため、手動で編集しない
- 意味のあるコミットメッセージを使用

## AIコーディングエージェントへの注意事項

- **これはドキュメントプロジェクトです** - コードではなくコンテンツの品質に重点を置いてください
- **翻訳ファイルを変更しないでください** - 自動生成されます
- **ファイル命名規則を守ってください** - 既存のパターンに従い、ファイル名にスペースを使用
- **README.mdを更新**してモジュールを追加または削除した場合、表を同期
- **ローカルでテスト**してMarkdownが正しくレンダリングされることを確認
- **既存のコンテンツスタイルに従う** - 初心者向けでベンダー中立的なトーンを維持
- **ビルドプロセスは不要** - シンプルなHTTPサーバーでローカル開発が可能
- **モジュール構造を尊重** - 各モジュールは一貫した番号付けと構成を持つ

---

**免責事項**:  
この文書は、AI翻訳サービス[Co-op Translator](https://github.com/Azure/co-op-translator)を使用して翻訳されています。正確性を追求しておりますが、自動翻訳には誤りや不正確な部分が含まれる可能性があります。元の言語で記載された文書を正式な情報源としてお考えください。重要な情報については、専門の人間による翻訳を推奨します。この翻訳の使用に起因する誤解や誤解釈について、当方は一切の責任を負いません。