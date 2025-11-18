<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-11-18T18:03:10+00:00",
  "source_file": "AGENTS.md",
  "language_code": "pcm"
}
-->
# AGENTS.md

## Project Overview

**Security-101** na beginner-friendly cybersecurity curriculum wey Microsoft create. Dis project na documentation-based learning resource wey dey teach basic cybersecurity concepts through structured modules. E no dey tied to any vendor and e dey designed make person fit complete am for small-small lessons (30-60 minutes each).

**Key Technologies:**
- Markdown for content
- Docsify for static site generation
- GitHub Pages for hosting
- Co-op Translator for multi-language support (50+ languages)
- GitHub Actions for CI/CD

**Architecture:**
- Educational content dey arranged inside 8 main modules, each one get sub-lessons
- Static HTML site wey Docsify dey render Markdown content
- Automated translation workflow wey dey use Azure AI services
- No need for build tools or package managers for core content

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

Dis na documentation project wey no need any dependencies to install. To work with the content:

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

Dis project dey use Docsify for rendering. To preview changes:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Content Structure

Modules dey numbered one after the other:
- **Module 1:** Basic security concepts (1.1-1.7)
- **Module 2:** Identity & access management (2.1-2.4)
- **Module 3:** Network security (3.1-3.4)
- **Module 4:** Security operations (4.1-4.4)
- **Module 5:** Application security (5.1-5.3)
- **Module 6:** Infrastructure security (6.1-6.3)
- **Module 7:** Data security (7.1-7.3)
- **Module 8:** AI security (8.1-8.4)

Each module dey end with quiz file (e.g., "1.7 End of module quiz.md").

### Making Content Changes

1. Edit Markdown files directly for root directory
2. Follow the naming style wey dey already: `[module].[lesson] [Title].md`
3. Update README.md table if you dey add/remove modules
4. Add images to `/images/` directory
5. Reference images using relative paths: `![Description](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.pcm.png)`

## Translation Workflow

**Automated Translation:**
- Translations dey handled automatically by the Co-op Translator GitHub Action
- When you push changes go `main` branch, the workflow dey translate content to 50+ languages
- Translated files dey stored inside `/translations/[language_code]/`
- Translation metadata dey preserved inside YAML frontmatter

**Supported Languages:** Arabic, Bengali, Bulgarian, Burmese, Chinese (Simplified, Traditional), Croatian, Czech, Danish, Dutch, Estonian, Finnish, French, German, Greek, Hebrew, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean, Lithuanian, Malay, Marathi, Nepali, Norwegian, Persian, Polish, Portuguese, Punjabi, Romanian, Russian, Serbian, Slovak, Slovenian, Spanish, Swahili, Swedish, Tagalog, Tamil, Thai, Turkish, Ukrainian, Urdu, Vietnamese, and more.

**No dey manually edit translation files** - dem go overwrite am with the automated workflow.

## Code Style Guidelines

### Markdown Conventions

- Use standard Markdown syntax
- Headings: Use `#` for main title, `##` for sections, `###` for subsections
- Lists: Use `-` or `*` for unordered lists, `1.` for ordered lists
- Links: Use descriptive text with full GitHub URLs for cross-references
- Images: Store for `/images/` directory, use descriptive alt text
- Code blocks: Use triple backticks with language identifier when e dey necessary

### Content Guidelines

- Make lessons short and straight to the point (30-60 minute read time)
- Use clear, beginner-friendly language
- No dey use vendor-specific tool instructions (curriculum no dey tied to any vendor)
- Add learning objectives for the start of each module
- Link to external Microsoft Learn resources where e dey necessary
- Make sure say content dey educational, no be promotional

### File Naming

- Use format: `[Module].[Lesson] [Title].md`
- Example: `1.1 The CIA triad and other key concepts.md`
- Quiz files: `[Module].[Last] End of module quiz.md`
- Use spaces for filenames (existing style)

## GitHub Workflows

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push to `main` branch  
**Purpose:** Automatically dey translate new/modified Markdown files to 50+ languages

**Environment Variables Required:**
- Azure AI Service credentials (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Azure OpenAI credentials (optional alternative)
- OpenAI credentials (optional alternative)

### Deploy (deploy.yaml)

**Trigger:** Push to `main` branch when README.md change  
**Purpose:** Deploy static site go GitHub Pages  
**Output:** Updates GitHub Pages site

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push to configured branch  
**Purpose:** Builds and deploy site using Jekyll

## Pull Request Guidelines

### Before Submitting

1. **Content Review:** Make sure say cybersecurity concepts dey accurate and clear
2. **Formatting:** Check say Markdown formatting dey render well
3. **Links:** Test all internal and external links
4. **Images:** Make sure say all images dey load and get descriptive alt text
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

1. At least one maintainer review dey required
2. Focus on technical accuracy of security concepts
3. Check accessibility and beginner-friendliness
4. Make sure say vendor neutrality dey intact

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
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.pcm.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testing and Validation

### Content Validation

Since dis na documentation project, testing dey focus on:

1. **Markdown Rendering:** View changes locally using Docsify
2. **Link Validation:** Manually click through all links
3. **Image Loading:** Make sure say all images dey display well
4. **Translation:** Check say files dey picked up by translator workflow (automated)
5. **Accessibility:** Make sure say heading hierarchy and alt text dey correct

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

- [ ] Markdown files dey use correct syntax
- [ ] All links dey valid and dey use HTTPS where e dey possible
- [ ] Images get descriptive alt text
- [ ] Content dey beginner-friendly and accurate
- [ ] Vendor-neutral language dey intact
- [ ] README.md dey updated if you dey add/remove modules
- [ ] File naming dey follow conventions

## Security Considerations

- **No secrets for content:** No dey commit API keys, passwords, or sensitive data
- **Link validation:** Make sure say all external links dey go trusted sources
- **Image content:** Check say images no dey carry sensitive information
- **Translation workflow:** E dey use Azure AI services with proper authentication
- **SECURITY.md:** Follow vulnerability reporting process for SECURITY.md

## Additional Resources

### Related Microsoft Courses

Dis curriculum na part of bigger collection of Microsoft educational resources:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### External Learning Paths

After you complete Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Contributing

1. **Fork the repository** for GitHub
2. **Create a feature branch** for your changes
3. **Make your changes** follow the guidelines wey dey above
4. **Test locally** to make sure say everything dey render well
5. **Submit a pull request** with clear description of changes
6. **Respond to feedback** from maintainers

## Common Issues and Troubleshooting

### Translations Not Working

- Make sure say changes dey pushed to `main` branch
- Check GitHub Actions tab for workflow status
- Verify translation workflow secrets dey configured
- Translation dey happen automatically; no dey manually edit translation files

### Images Not Loading

- Check say image path dey use forward slashes: `images/filename.png`
- Make sure say image file dey committed to repository
- Confirm say image filename match exactly (case-sensitive)
- Use relative paths, no be absolute URLs

### Docsify Not Rendering

- Check say `index.html` dey present for root
- Verify Docsify CDN links dey accessible
- Make sure say Markdown files dey use standard syntax
- Check browser console for JavaScript errors

### Links Not Working

- Use full GitHub URLs for cross-references between lessons
- Format: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Test links for rendered view, no be just raw Markdown

## Project Maintenance

### Regular Tasks

- Review and merge community contributions
- Update content to make sure say e dey accurate as security landscape dey change
- Monitor translation workflow for errors
- Respond to issues and discussions
- Keep external links up to date

### Version Control

- `main` branch dey protected and e need PR reviews
- All changes dey go through pull request process
- Translation files dey auto-generated, no dey edit am manually
- Use meaningful commit messages

## Notes for AI Coding Agents

- **Dis na documentation project** - focus on content quality, no be code
- **No dey modify translation files** - dem dey auto-generated
- **Preserve file naming conventions** - use spaces for filenames as per existing style
- **Update README.md** when you dey add/remove modules to keep table in sync
- **Test locally** before you submit PRs to make sure say Markdown dey render well
- **Follow existing content style** - maintain beginner-friendly, vendor-neutral tone
- **No build process dey required** - simple HTTP server dey enough for local development
- **Respect the module structure** - each module get consistent numbering and arrangement

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Dis document don use AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator) take translate am. Even though we dey try make e accurate, abeg sabi say automated translations fit get mistake or no correct well. Di original document for di native language na di main correct source. For important information, e good make una use professional human translation. We no go dey responsible for any misunderstanding or wrong interpretation wey fit happen because of dis translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->