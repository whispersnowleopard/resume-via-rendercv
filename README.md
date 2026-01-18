# Resume via RenderCV

Professional CV/resume managed as YAML and rendered to PDF using [RenderCV](https://github.com/sinaatalay/rendercv).

## What is this?

This repo uses RenderCV to generate my resume from structured YAML data. Benefits:

- **Version control** - Track changes to resume content over time
- **Consistency** - Automated formatting ensures professional appearance
- **Reusability** - Easy to maintain multiple versions (full CV vs. brief resume)
- **Portability** - YAML is human-readable and easy to edit

## Files

- `Dave_Gilbert_CV.yaml` - Current production resume
- `Dave_Gilbert_CV.pdf` - Latest rendered output
- `David_E_Gilbert_CV-stub.yaml` - Template/alternative version

## Usage

### Install RenderCV
```bash
pip install rendercv
```

### Generate PDF
```bash
rendercv render Dave_Gilbert_CV.yaml
```

Output appears in `rendercv_output/` (gitignored by default).

## Why YAML for Resumes?

- **Data-driven** - Separate content from presentation
- **Searchable** - Easy to grep for specific experiences or skills
- **Maintainable** - Update once, regenerate multiple formats
- **Diffable** - Git shows exactly what changed between versions

## Tech Stack

- [RenderCV](https://github.com/sinaatalay/rendercv) - YAML to PDF rendering engine
- [Typst](https://typst.app/) - Modern typesetting system (replaces LaTeX)
- Git - Version control

---

*Generated resumes are for professional use. Contact information is public in this repo.*
