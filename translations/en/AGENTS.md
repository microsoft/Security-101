<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:23:10+00:00",
  "source_file": "AGENTS.md",
  "language_code": "en"
}
-->
# AGENTS.md

## Project Overview

**Security-101** is a beginner-friendly cybersecurity curriculum developed by Microsoft. This project is a documentation-based learning resource that introduces fundamental cybersecurity concepts through structured modules. It is vendor-neutral and designed to be completed in short lessons (30-60 minutes each).

**Key Technologies:**
- Markdown for content
- Docsify for static site generation
- GitHub Pages for hosting
- Co-op Translator for multilingual support (50+ languages)
- GitHub Actions for CI/CD

**Architecture:**
- Educational content divided into 8 main modules, each containing sub-lessons
- Static HTML site with Docsify rendering Markdown content
- Automated translation workflow powered by Azure AI services
- No build tools or package managers required for core content

## Repository Structure

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

## Setup Commands

This is a documentation project with no dependencies to install. To work with the content:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Development Workflow

### Viewing Content Locally

The project uses Docsify for rendering. To preview changes:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Content Structure

Modules are organized sequentially:
- **Module 1:** Basic security concepts (1.1-1.7)
- **Module 2:** Identity & access management (2.1-2.4)
- **Module 3:** Network security (3.1-3.4)
- **Module 4:** Security operations (4.1-4.4)
- **Module 5:** Application security (5.1-5.3)
- **Module 6:** Infrastructure security (6.1-6.3)
- **Module 7:** Data security (7.1-7.3)
- **Module 8:** AI security (8.1-8.4)

Each module concludes with a quiz file (e.g., "1.7 End of module quiz.md").

### Making Content Changes

1. Edit Markdown files directly in the root directory
2. Follow the existing naming convention: `[module].[lesson] [Title].md`
3. Update the README.md table if adding or removing modules
4. Add images to the `/images/` directory
5. Reference images using relative paths: `![Description](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.en.png)`

## Translation Workflow

**Automated Translation:**
- Translations are automatically managed by the Co-op Translator GitHub Action
- When changes are pushed to the `main` branch, the workflow translates content into 50+ languages
- Translated files are stored in `/translations/[language_code]/`
- Translation metadata is maintained in YAML frontmatter

**Supported Languages:** Arabic, Bengali, Bulgarian, Burmese, Chinese (Simplified, Traditional), Croatian, Czech, Danish, Dutch, Estonian, Finnish, French, German, Greek, Hebrew, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean, Lithuanian, Malay, Marathi, Nepali, Norwegian, Persian, Polish, Portuguese, Punjabi, Romanian, Russian, Serbian, Slovak, Slovenian, Spanish, Swahili, Swedish, Tagalog, Tamil, Thai, Turkish, Ukrainian, Urdu, Vietnamese, and more.

**Do NOT manually edit translation files** - they will be overwritten by the automated workflow.

## Code Style Guidelines

### Markdown Conventions

- Use standard Markdown syntax
- Headings: Use `#` for main titles, `##` for sections, `###` for subsections
- Lists: Use `-` or `*` for unordered lists, `1.` for ordered lists
- Links: Use descriptive text with full GitHub URLs for cross-references
- Images: Store in the `/images/` directory, use descriptive alt text
- Code blocks: Use triple backticks with a language identifier when applicable

### Content Guidelines

- Keep lessons concise and focused (30-60 minute read time)
- Use clear, beginner-friendly language
- Avoid instructions for vendor-specific tools (curriculum is vendor-neutral)
- Include learning objectives at the beginning of each module
- Link to external Microsoft Learn resources when relevant
- Ensure content is educational, not promotional

### File Naming

- Use the format: `[Module].[Lesson] [Title].md`
- Example: `1.1 The CIA triad and other key concepts.md`
- Quiz files: `[Module].[Last] End of module quiz.md`
- Use spaces in filenames (as per existing convention)

## GitHub Workflows

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push to `main` branch  
**Purpose:** Automatically translates new or modified Markdown files into 50+ languages

**Environment Variables Required:**
- Azure AI Service credentials (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI credentials (optional alternative)
- OpenAI credentials (optional alternative)

### Deploy (deploy.yaml)

**Trigger:** Push to `main` branch when README.md changes  
**Purpose:** Deploys the static site to GitHub Pages  
**Output:** Updates the GitHub Pages site

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push to the configured branch  
**Purpose:** Builds and deploys the site using Jekyll

## Pull Request Guidelines

### Before Submitting

1. **Content Review:** Ensure the accuracy and clarity of cybersecurity concepts
2. **Formatting:** Verify that Markdown formatting renders correctly
3. **Links:** Test all internal and external links
4. **Images:** Ensure all images load properly and have descriptive alt text
5. **Consistency:** Follow the existing content structure and style

### PR Title Format

Use descriptive titles:
- `Add: [New content description]`
- `Update: [Module/Lesson] - [Brief description]`
- `Fix: [Issue description]`
- `Docs: [Documentation changes]`

### Required Checks

- Content accuracy (manual review)
- Markdown formatting validation
- Link verification
- Translation workflow completion (for `main` branch merges)

### Review Process

1. At least one maintainer review is required
2. Focus on the technical accuracy of security concepts
3. Verify accessibility and beginner-friendliness
4. Ensure vendor neutrality is maintained

## Common Tasks

### Adding a New Lesson

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

### Updating Existing Content

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Adding Images

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.en.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testing and Validation

### Content Validation

Since this is a documentation project, testing focuses on:

1. **Markdown Rendering:** Preview changes locally using Docsify
2. **Link Validation:** Manually test all links
3. **Image Loading:** Ensure all images display correctly
4. **Translation:** Confirm that files are processed by the translator workflow (automated)
5. **Accessibility:** Check heading hierarchy and alt text

### Local Preview

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Pre-commit Checklist

- [ ] Markdown files use correct syntax
- [ ] All links are valid and use HTTPS where possible
- [ ] Images have descriptive alt text
- [ ] Content is beginner-friendly and accurate
- [ ] Vendor-neutral language is maintained
- [ ] README.md updated if adding or removing modules
- [ ] File naming follows conventions

## Security Considerations

- **No secrets in content:** Never commit API keys, passwords, or sensitive data
- **Link validation:** Ensure all external links point to trusted sources
- **Image content:** Confirm images do not contain sensitive information
- **Translation workflow:** Uses Azure AI services with proper authentication
- **SECURITY.md:** Follow the vulnerability reporting process outlined in SECURITY.md

## Additional Resources

### Related Microsoft Courses

This curriculum is part of a broader collection of Microsoft educational resources:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### External Learning Paths

After completing Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Contributing

1. **Fork the repository** on GitHub
2. **Create a feature branch** for your changes
3. **Make your changes** following the guidelines above
4. **Test locally** to ensure everything renders correctly
5. **Submit a pull request** with a clear description of changes
6. **Respond to feedback** from maintainers

## Common Issues and Troubleshooting

### Translations Not Working

- Ensure changes are pushed to the `main` branch
- Check the GitHub Actions tab for workflow status
- Verify that translation workflow secrets are correctly configured
- Translation is automated; do not manually edit translation files

### Images Not Loading

- Ensure the image path uses forward slashes: `images/filename.png`
- Confirm the image file is committed to the repository
- Verify the image filename matches exactly (case-sensitive)
- Use relative paths, not absolute URLs

### Docsify Not Rendering

- Confirm that `index.html` is present in the root directory
- Verify that Docsify CDN links are accessible
- Ensure Markdown files follow standard syntax
- Check the browser console for JavaScript errors

### Links Not Working

- Use full GitHub URLs for cross-references between lessons
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Test links in the rendered view, not just in raw Markdown

## Project Maintenance

### Regular Tasks

- Review and merge community contributions
- Update content to reflect changes in the security landscape
- Monitor translation workflow for errors
- Respond to issues and discussions
- Keep external links current

### Version Control

- The `main` branch is protected and requires PR reviews
- All changes must go through the pull request process
- Translation files are auto-generated; do not edit them manually
- Use clear and meaningful commit messages

## Notes for AI Coding Agents

- **This is a documentation project** - prioritize content quality over code
- **Do not modify translation files** - they are automatically generated
- **Preserve file naming conventions** - use spaces in filenames as per the existing pattern
- **Update README.md** when adding or removing modules to keep the table consistent
- **Test locally** before submitting pull requests to ensure proper Markdown rendering
- **Follow the existing content style** - maintain a beginner-friendly, vendor-neutral tone
- **No build process required** - a simple HTTP server is sufficient for local development
- **Respect the module structure** - ensure consistent numbering and organization for each module

---

**Disclaimer**:  
This document has been translated using the AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator). While we aim for accuracy, please note that automated translations may contain errors or inaccuracies. The original document in its native language should be regarded as the authoritative source. For critical information, professional human translation is recommended. We are not responsible for any misunderstandings or misinterpretations resulting from the use of this translation.