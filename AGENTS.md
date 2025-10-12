# AGENTS.md

## Project Overview

**Security-101** is a beginner-friendly cybersecurity curriculum created by Microsoft. The project is a documentation-based learning resource that teaches fundamental cybersecurity concepts through structured modules. It is vendor-agnostic and designed to be completed in small lessons (30-60 minutes each).

**Key Technologies:**
- Markdown for content
- Docsify for static site generation
- GitHub Pages for hosting
- Co-op Translator for multi-language support (50+ languages)
- GitHub Actions for CI/CD

**Architecture:**
- Educational content organized in 8 main modules, each with sub-lessons
- Static HTML site with Docsify rendering Markdown content
- Automated translation workflow using Azure AI services
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

Modules are numbered sequentially:
- **Module 1:** Basic security concepts (1.1-1.7)
- **Module 2:** Identity & access management (2.1-2.4)
- **Module 3:** Network security (3.1-3.4)
- **Module 4:** Security operations (4.1-4.4)
- **Module 5:** Application security (5.1-5.3)
- **Module 6:** Infrastructure security (6.1-6.3)
- **Module 7:** Data security (7.1-7.3)
- **Module 8:** AI security (8.1-8.4)

Each module ends with a quiz file (e.g., "1.7 End of module quiz.md").

### Making Content Changes

1. Edit Markdown files directly in the root directory
2. Follow existing naming convention: `[module].[lesson] [Title].md`
3. Update README.md table if adding/removing modules
4. Add images to `/images/` directory
5. Reference images using relative paths: `![Description](images/filename.png)`

## Translation Workflow

**Automated Translation:**
- Translations are handled automatically by the Co-op Translator GitHub Action
- When you push changes to `main` branch, the workflow translates content to 50+ languages
- Translated files are stored in `/translations/[language_code]/`
- Translation metadata is preserved in YAML frontmatter

**Supported Languages:** Arabic, Bengali, Bulgarian, Burmese, Chinese (Simplified, Traditional), Croatian, Czech, Danish, Dutch, Estonian, Finnish, French, German, Greek, Hebrew, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean, Lithuanian, Malay, Marathi, Nepali, Norwegian, Persian, Polish, Portuguese, Punjabi, Romanian, Russian, Serbian, Slovak, Slovenian, Spanish, Swahili, Swedish, Tagalog, Tamil, Thai, Turkish, Ukrainian, Urdu, Vietnamese, and more.

**Do NOT manually edit translation files** - they will be overwritten by the automated workflow.

## Code Style Guidelines

### Markdown Conventions

- Use standard Markdown syntax
- Headings: Use `#` for main title, `##` for sections, `###` for subsections
- Lists: Use `-` or `*` for unordered lists, `1.` for ordered lists
- Links: Use descriptive text with full GitHub URLs for cross-references
- Images: Store in `/images/` directory, use descriptive alt text
- Code blocks: Use triple backticks with language identifier when applicable

### Content Guidelines

- Keep lessons focused and concise (30-60 minute read time)
- Use clear, beginner-friendly language
- Avoid vendor-specific tool instructions (curriculum is vendor-agnostic)
- Include learning objectives at the start of each module
- Link to external Microsoft Learn resources where appropriate
- Ensure content is educational, not promotional

### File Naming

- Use format: `[Module].[Lesson] [Title].md`
- Example: `1.1 The CIA triad and other key concepts.md`
- Quiz files: `[Module].[Last] End of module quiz.md`
- Use spaces in filenames (existing convention)

## GitHub Workflows

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push to `main` branch  
**Purpose:** Automatically translates new/modified Markdown files to 50+ languages

**Environment Variables Required:**
- Azure AI Service credentials (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI credentials (optional alternative)
- OpenAI credentials (optional alternative)

### Deploy (deploy.yaml)

**Trigger:** Push to `main` branch when README.md changes  
**Purpose:** Deploys static site to GitHub Pages  
**Output:** Updates GitHub Pages site

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push to configured branch  
**Purpose:** Builds and deploys site using Jekyll

## Pull Request Guidelines

### Before Submitting

1. **Content Review:** Ensure accuracy and clarity of cybersecurity concepts
2. **Formatting:** Verify Markdown formatting renders correctly
3. **Links:** Test all internal and external links
4. **Images:** Ensure all images load and have descriptive alt text
5. **Consistency:** Follow existing content structure and style

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

1. At least one maintainer review required
2. Focus on technical accuracy of security concepts
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
# ![Descriptive alt text](images/new-image.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testing and Validation

### Content Validation

Since this is a documentation project, testing focuses on:

1. **Markdown Rendering:** View changes locally using Docsify
2. **Link Validation:** Manually click through all links
3. **Image Loading:** Verify all images display correctly
4. **Translation:** Check that files are picked up by translator workflow (automated)
5. **Accessibility:** Ensure proper heading hierarchy and alt text

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
- [ ] README.md updated if adding/removing modules
- [ ] File naming follows conventions

## Security Considerations

- **No secrets in content:** Never commit API keys, passwords, or sensitive data
- **Link validation:** Ensure all external links are to trusted sources
- **Image content:** Verify images don't contain sensitive information
- **Translation workflow:** Uses Azure AI services with proper authentication
- **SECURITY.md:** Follow vulnerability reporting process in SECURITY.md

## Additional Resources

### Related Microsoft Courses

This curriculum is part of a larger collection of Microsoft educational resources:
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

- Ensure changes are pushed to `main` branch
- Check GitHub Actions tab for workflow status
- Verify translation workflow secrets are configured
- Translation happens automatically; do not manually edit translation files

### Images Not Loading

- Verify image path uses forward slashes: `images/filename.png`
- Check that image file is committed to repository
- Ensure image filename matches exactly (case-sensitive)
- Use relative paths, not absolute URLs

### Docsify Not Rendering

- Check that `index.html` is present in root
- Verify Docsify CDN links are accessible
- Ensure Markdown files use standard syntax
- Check browser console for JavaScript errors

### Links Not Working

- Use full GitHub URLs for cross-references between lessons
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Test links in rendered view, not just in raw Markdown

## Project Maintenance

### Regular Tasks

- Review and merge community contributions
- Update content for accuracy as security landscape evolves
- Monitor translation workflow for errors
- Respond to issues and discussions
- Keep external links up to date

### Version Control

- `main` branch is protected and requires PR reviews
- All changes go through pull request process
- Translation files are auto-generated, do not edit manually
- Use meaningful commit messages

## Notes for AI Coding Agents

- **This is a documentation project** - focus on content quality, not code
- **Do not modify translation files** - they are auto-generated
- **Preserve file naming conventions** - use spaces in filenames as per existing pattern
- **Update README.md** when adding/removing modules to keep table in sync
- **Test locally** before submitting PRs to ensure Markdown renders correctly
- **Follow existing content style** - maintain beginner-friendly, vendor-neutral tone
- **No build process required** - simple HTTP server is sufficient for local development
- **Respect the module structure** - each module has consistent numbering and organization
