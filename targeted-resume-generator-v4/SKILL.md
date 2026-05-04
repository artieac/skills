---
name: targeted-resume-generator-v4
version: v4
description: >
  Generates a tailored, two-page resume PDF for Arthur J. Correa targeting a specific job description.
  Use this skill whenever Artie asks to create a resume, generate a resume for a role, tailor a resume
  to a job posting, or produce a resume for any job application. Also triggers when given a job
  description or job posting URL and asked to produce a resume or application document.
  Always use this skill — do not attempt resume generation without it. Never use any other resume
  skill or resume context found elsewhere. This skill is the only source of truth for resume generation.
---

# TargetedResumeGenerator v4 — Arthur J. Correa

Generates a tailored two-page resume PDF for a specific job description.
All content comes exclusively from the bundled source file.
The visual layout matches the bundled layout reference exactly.

---

## IMPORTANT: Source and Layout Files

- **All personal content** (experience, skills, education, contact info) comes ONLY from:
  `/path-to-skill/assets/SourceDataForResume.docx`
  Read this file at the start of every resume generation using: `extract-text <path>`

- **All formatting, fonts, colors, sizes, and layout** come ONLY from:
  `/path-to-skill/assets/LayoutExampleForResume.pdf`
  This PDF is the visual ground truth. Match it exactly.

Never use content from memory, prior conversations, or any other resume files.
If you want to include something not found in SourceDataForResume.docx, **stop and ask Artie first**.

---

## Step 1: Read the Source Data

Before writing any content or code, run:

```bash
extract-text /path-to-skill/assets/SourceDataForResume.docx
```

Extract and hold in context:
- Full name and contact info
- All work experience entries (company, title, dates, bullets)
- All skills (organized by category as listed)
- Education entries

---

## Step 2: Analyze the Job Description

Before writing content, read the job description carefully and identify:
- Role level (CTO / VP Engineering / Director / etc.)
- Company domain and mission
- Top 3-5 priorities the role emphasizes (e.g., reliability, AI, team scaling, security, cloud)
- Specific technologies or methodologies called out
- Any compliance, regulatory, or industry-specific requirements

This analysis drives all tailoring decisions across every section.

---

## Step 3: Build Each Section

### HEADER
- Full name: **ARTHUR J. CORREA** — large, bold, centered, dark navy color `1F3864`
- Contact line: `978 204-1241  |  artieac@gmail.com` — centered, smaller font, no location

---

### SUMMARY
- Write fresh for this specific role — do not copy source summary verbatim
- Max **5 lines** at body font size. This is a hard limit — cut without mercy if needed.
- Structure: Open with a strong executive-level framing (years of experience, leadership scope),
  then weave in 2-3 metrics or outcomes most relevant to this role's priorities,
  then close with a brief signal of the specific strength this role cares most about.
- The summary's job is: overall picture of experience + a hint of the #1 thing this role needs.

---

### SELECT IMPACT

This section contains **exactly 4 subsections**, displayed **vertically** (stacked, one after another — NOT a table, NOT side by side).

Each subsection:
- **Bold label** (3-6 words, dark navy color `1F3864`) — choose a label that speaks directly to what this role needs and how Artie fits it
- Followed by **2 to 4 bullet points** (minimum 2, maximum 4) — each bullet drawn from specific facts, roles, or outcomes in SourceDataForResume.docx
- Bullets should collectively demonstrate Artie's fit for the role, not just list generic achievements

The 4 subsections should together cover different dimensions of fit (e.g., org leadership, technical depth, delivery/reliability, domain-specific). Choose the 4 dimensions that best match the specific role.

**Do not use a table for this section.** Stack the 4 subsections vertically with the label bold on its own line above the bullets.

---

### EXPERIENCE

- Order: most recent role first, oldest last
- For each major role include:
  - **Company name** — bold, dark navy color `1F3864`, same shade as section headers
  - **Role title** — bold, dark navy color `1F3864`, same shade as section headers
  - **Location and dates** — dates right-aligned or tab-separated, regular weight
  - 1-2 sentence role description (what the org did, team size)
  - Bullet points — filtered and ordered by relevance to the JD. Include bullets that are most likely to resonate with the hiring manager for this specific role.

- **Earlier Experience** (roles before ~2012): Condense into a compact single-paragraph block using one `Paragraph` with mixed `TextRun` elements — bold navy for company/title, regular black for dates and separators. No bullets for these older roles.

- Never include a bullet Artie could not defend in an interview.
- Never invent facts, metrics, or accomplishments not in SourceDataForResume.docx.

---

### TECHNOLOGY FLUENCY

- Populate from the SKILLS section of SourceDataForResume.docx — use exactly what is there, do not add or remove items
- Format as labeled lines:
  - **Line opener** (e.g., "Operating Systems:", "Programming Languages:") — bold, dark navy color `1F3864`
  - Followed by the values from the source file on the same line, regular weight, black
- Categories to include (as found in the source):
  - Operating Systems
  - Programming Languages
  - AI & Developer Tools
  - Databases
  - Technologies
  - Other

---

### EDUCATION

- Populate from the EDUCATION section of SourceDataForResume.docx
- Each entry is a single line with two parts:
  - **Degree and major** (e.g., "M.S. in Computer Science") — bold, dark navy `1F3864`
  - **School name and location** (e.g., ", Boston University, Boston, MA") — regular weight, black body font
- Format each line as two TextRun elements in the same Paragraph: bold navy for degree/major, then regular black for school and location
- Example: `M.S. in Computer Science` [bold, navy] + `, Boston University, Boston, MA` [regular, black]

---

## Step 4: Visual Formatting Rules

All formatting must match the LayoutExampleForResume.pdf exactly, **with the following three exceptions which are fixed values that override anything seen in the PDF**:
- **Name**: always 31 half-points (15.5pt)
- **Section headers**: always 30 half-points (15pt)
- **Select Impact subsection labels**: always 19 half-points (9.5pt)

Never derive or infer these three sizes from the PDF. Always use the fixed values above.

### Page Setup
- Paper: US Letter — 12240 x 15840 DXA
- Margins: top 720, bottom 720, left 900, right 900 (approx 0.5" top/bottom, 0.625" sides)

### Font: Arial throughout — never any other font

### Sizes (in half-points — divide by 2 to get pt size)
| Element | Size (half-pts) | Source |
|---|---|---|
| Name | 31 | FIXED — do not use PDF value |
| Contact line | 18 | From PDF |
| Section headers (SUMMARY, SELECT IMPACT, etc.) | 30 | FIXED — do not use PDF value |
| Select Impact subsection labels | 19 | FIXED — do not use PDF value |
| Company name (Experience) | 22 | From PDF |
| Role title (Experience) | 18 | From PDF |
| Dates / location | 18 | From PDF |
| Body text and bullets | 18 | From PDF |
| Technology Fluency line openers | 18 | From PDF |
| Education degree/major (bold, navy) | 18 | From PDF |
| Education school/location (regular, black) | 18 | From PDF |

### Colors
- Dark navy (name, section headers, company, role titles, Select Impact labels, tech fluency openers, education lines): `1F3864`
- Body text, bullets, dates: `000000` (black)
- Section header bottom border line: `2E75B6`, size 6

### Section Headers
Every section header (SUMMARY, SELECT IMPACT, EXPERIENCE, TECHNOLOGY FLUENCY, EDUCATION) must have:
- Text: bold, dark navy `1F3864`, size 30 half-points
- A bottom border line: `BorderStyle.SINGLE`, size 6, color `2E75B6`
- No top, left, or right borders

### Spacing
- After name paragraph: spacing after 40
- Section headers: spacing before 120, after 60
- Company name: spacing before 80, after 0
- Role title line: spacing before 0, after 0
- Role description paragraph: spacing before 40, after 40
- Bullet items: spacing before 0, after 40
- Last bullet in a role: spacing after 60
- Select Impact label: spacing before 80, after 20
- Select Impact bullet: spacing before 0, after 40
- Technology Fluency lines: spacing before 0, after 40
- Education lines: spacing before 0, after 40

### Bullets
- Use `LevelFormat.BULLET` with docx numbering config — never unicode bullet characters
- Indent: left 360, hanging 180

---

## Step 5: Code Generation

Use Node.js with the `docx` npm package to generate the `.docx`.

### Setup
```javascript
const { Document, Packer, Paragraph, TextRun,
        AlignmentType, LevelFormat, BorderStyle,
        WidthType, TabStopType, TabStopPosition } = require('docx');
const fs = require('fs');
```

Install if needed:
```bash
npm install docx --save
```

### Key patterns to use

**Section header with blue bottom border:**
```javascript
new Paragraph({
  children: [new TextRun({ text: "SUMMARY", bold: true, font: "Arial", size: 30, color: "1F3864" })],
  border: { bottom: { style: BorderStyle.SINGLE, size: 6, color: "2E75B6", space: 1 } },
  spacing: { before: 120, after: 60 }
})
```

**Company name (bold, dark navy):**
```javascript
new Paragraph({
  children: [new TextRun({ text: "Grand Circle Corporation - Boston, MA", bold: true, font: "Arial", size: 22, color: "1F3864" })],
  spacing: { before: 80, after: 0 }
})
```

**Role title with right-tab date:**
```javascript
new Paragraph({
  tabStops: [{ type: TabStopType.RIGHT, position: 9360 }],
  children: [
    new TextRun({ text: "Vice President, Software Engineering", bold: true, font: "Arial", size: 18, color: "1F3864" }),
    new TextRun({ text: "\tMarch 2024 - Present", font: "Arial", size: 18, color: "000000" })
  ],
  spacing: { before: 0, after: 0 }
})
```

**Bullet item:**
```javascript
new Paragraph({
  numbering: { reference: "bullets", level: 0 },
  children: [new TextRun({ text: "Bullet text here", font: "Arial", size: 18 })],
  spacing: { before: 0, after: 40 }
})
```

**Select Impact label (bold, dark navy):**
```javascript
new Paragraph({
  children: [new TextRun({ text: "Org & Team Leadership", bold: true, font: "Arial", size: 19, color: "1F3864" })],
  spacing: { before: 80, after: 20 }
})
```

**Technology Fluency line (bold opener + regular values):**
```javascript
new Paragraph({
  children: [
    new TextRun({ text: "Operating Systems: ", bold: true, font: "Arial", size: 18, color: "1F3864" }),
    new TextRun({ text: "Windows, Linux, Android, CoreOS", font: "Arial", size: 18, color: "000000" })
  ],
  spacing: { before: 0, after: 40 }
})
```

**Education line (bold degree/major + regular school/location):**
```javascript
new Paragraph({
  children: [
    new TextRun({ text: "M.S. in Computer Science", bold: true, font: "Arial", size: 18, color: "1F3864" }),
    new TextRun({ text: ", Boston University, Boston, MA", font: "Arial", size: 18, color: "000000" })
  ],
  spacing: { before: 0, after: 40 }
})
```

**Earlier Experience compact block (no bullets — mixed TextRuns in one Paragraph):**
```javascript
new Paragraph({
  children: [
    new TextRun({ text: "Drift", bold: true, font: "Arial", size: 18, color: "1F3864" }),
    new TextRun({ text: " (Architect, 2019-2020) - Virtual Architect team, feature flag/billing/security redesign.  ", font: "Arial", size: 18, color: "000000" }),
    new TextRun({ text: "Intuit", bold: true, font: "Arial", size: 18, color: "1F3864" }),
    new TextRun({ text: " (Sr. Engineer, 2007-2012) - Partner Platform, Payment Services, Innovation Lab.  ", font: "Arial", size: 18, color: "000000" }),
    // ... continue for each earlier role
  ],
  spacing: { before: 60, after: 60 }
})
```

**Numbering config (include in Document constructor):**
```javascript
numbering: {
  config: [{
    reference: "bullets",
    levels: [{
      level: 0,
      format: LevelFormat.BULLET,
      text: "\u2022",
      alignment: AlignmentType.LEFT,
      style: { paragraph: { indent: { left: 360, hanging: 180 } } }
    }]
  }]
}
```

**Page setup (include in section properties):**
```javascript
properties: {
  page: {
    size: { width: 12240, height: 15840 },
    margin: { top: 720, right: 900, bottom: 720, left: 900 }
  }
}
```

---

## Step 6: Zero Non-ASCII Validation (REQUIRED)

After generating the `.docx`, run both checks:

```bash
# 1. Structural validation
cd /mnt/skills/public/docx && python scripts/office/validate.py /path/to/output.docx

# 2. Non-ASCII character scan
python3 -c "
import zipfile, re
with zipfile.ZipFile('/path/to/output.docx') as z:
    xml = z.read('word/document.xml').decode('utf-8')
matches = re.findall(r'<w:t[^>]*>([^<]*[^\x00-\x7F][^<]*)</w:t>', xml)
print(f'Non-ASCII hits: {len(matches)}')
for m in matches: print(repr(m))
"
```

If any non-ASCII characters are found, fix them before proceeding:
- En dash `\u2013` / Em dash `\u2014` → replace with `-` or `--`
- Curly apostrophe `\u2018` / `\u2019` → replace with `'`
- Curly quotes `\u201C` / `\u201D` → replace with `"`
- Any other non-ASCII → find a plain ASCII equivalent

All fixes must result in zero non-ASCII hits before moving to PDF conversion.

---

## Step 7: Convert to PDF

After passing validation, convert the `.docx` to PDF using LibreOffice:

```bash
python /mnt/skills/public/docx/scripts/office/soffice.py --headless --convert-to pdf /path/to/output.docx --outdir /mnt/user-data/outputs/
```

Verify the PDF was created:
```bash
ls -lh /mnt/user-data/outputs/*.pdf
```

---

## Step 8: Two-Page Hard Limit

The final PDF **must not exceed two pages**. To enforce this, apply these limits:

| Section | Max content |
|---|---|
| Summary | 5 lines — hard cap, cut without asking |
| Select Impact | 4 subsections, 2-4 bullets each |
| GCC bullets | Max 5 (choose highest relevance to JD) |
| Veracode bullets | Max 4 |
| Wayfair bullets | Max 4 |
| Drift | 2-3 bullets |
| Aetna Digital | 2-3 bullets |
| athenaHealth | 2-3 bullets |
| Vistaprint | 2-3 bullets across all sub-roles |
| Intuit | 2-3 bullets |
| Earlier roles (pre-Intuit) | One condensed paragraph, no bullets |

If still overflowing after applying all limits:
1. First, trim body text (shorten sentences)
2. Then reduce bullet count
3. Never drop to fewer than 2 bullets per Select Impact subsection
4. Never go to 3 pages

---

## Step 9: Output

- Save the final PDF to: `/mnt/user-data/outputs/Correa_Resume_[CompanyName].pdf`
- Present the PDF to Artie using `present_files`
- Do NOT produce a `.docx` as the deliverable — the PDF is the final output
  (the `.docx` is an intermediate file only)

---

## Guardrails

| Rule | Detail |
|---|---|
| Source of truth | SourceDataForResume.docx only — no other source, no memory, no prior context |
| Layout reference | LayoutExampleForResume.pdf only — match it exactly |
| No invented content | Every fact must be in SourceDataForResume.docx. Ask before adding anything new. |
| No non-ASCII | Zero tolerance — validated before PDF conversion |
| Max 2 pages | Hard limit — trim content, never expand pages |
| Summary max 5 lines | Hard limit |
| Select Impact | Exactly 4 vertical subsections, 2-4 bullets each, NOT a table |
| Colors | Dark navy `1F3864` for name/headers/companies/titles/labels; `2E75B6` for border lines; `000000` for body |
| Font | Arial throughout — never any other font |
| Earlier Experience | Single compact Paragraph with mixed TextRuns — bold navy for names, regular black for details. No bullets. |
| Final output | PDF only — not .docx |