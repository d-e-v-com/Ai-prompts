# TODOs - Code Review Tool Enhancements

Tracking enhancements and fixes for the Claude Code Review prompt template.

---

## PDF Generation

- [x] **Derive PDF from PNG** - ✅ FIXED: PDF now uses PNG format internally with html2canvas (scale 4x)
- [x] **Fix PDF output quality** - ✅ FIXED: Increased scale to 4x, switched to PNG format, quality 1.0
- [ ] **Make PDF generation headless and reliable** - Backend process should not pop up browser export/save prompts (requires Node.js/Puppeteer script)
- [x] **Preserve styling accuracy** - ✅ FIXED: Added `allowTaint: true`, `backgroundColor: null` for better rendering
- [ ] **Auto-open PDF when complete** - After headless generation, open the resulting PDF for review (requires backend script)

---

## PNG Screenshot Generation

- [x] **Enhance PNG resolution** - ✅ FIXED: Increased from 2x to 4x scale for crisp high-DPI rendering
- [x] **Full-page screenshot automation** - ✅ FIXED: Added dedicated `exportPNG()` function with 4x scale
- [x] **Wait for Chart.js rendering** - ✅ FIXED: Added `waitForCharts()` using `Chart.getChart()` API instead of fixed timeout

---

## Deliverables

Goal: Automated generation of offline-ready deliverables for sharing and action.

### Expected Output Files

```
output-reports/YYYY-MM-DD_CodeBaseName_code_review_report/
├── data.json                                    # Raw metrics data (JSON)
├── index.html                                   # Interactive dashboard
├── YYYY-MM-DD_CodeBaseName_report.png           # Dashboard screenshot (4x scale)
├── YYYY-MM-DD_CodeBaseName_report.pdf           # Dashboard PDF export
├── YYYY-MM-DD_CodeBaseName_ACTION_ITEMS.md      # Remediation plan (Markdown)
├── YYYY-MM-DD_CodeBaseName_ACTION_ITEMS.html    # Remediation plan (styled HTML)
└── YYYY-MM-DD_CodeBaseName_ACTION_ITEMS.pdf     # Remediation plan (PDF for executives)
```

### Status

| File | Status | Notes |
|------|--------|-------|
| `data.json` | ✅ Working | Raw metrics data |
| `index.html` | ✅ Working | Interactive dashboard with charts |
| `*_report.png` | ✅ Implemented | 4x scale, Chart.js wait logic |
| `*_report.pdf` | ✅ Implemented | PNG-based, 4x scale |
| `*_ACTION_ITEMS.md` | ✅ Implemented | Epics/Stories/Subtasks format |
| `*_ACTION_ITEMS.html` | ✅ Implemented | Styled HTML, print-optimized |
| `*_ACTION_ITEMS.pdf` | ✅ Implemented | Executive-friendly PDF |

---

## Markdown Action Items Output (✅ IMPLEMENTED)

Generate `YYYY-MM-DD_CodeBaseName_ACTION_ITEMS.md` in the same output-reports folder containing:

### Structure

1. **Executive Summary**
   - High-level findings overview
   - Critical issues count by severity
   - Overall health grade and key metrics

2. **Findings Summary**
   - Categorized list of all detected issues
   - Anti-patterns, security vulnerabilities, code smells
   - Technical debt hotspots

3. **Remediation Plan** (Epics → Stories → Subtasks)

   **Format:**
   ```markdown
   ## Epic: [Category - e.g., "Security Hardening"]
   Priority: Critical/High/Medium/Low

   ### Story: [Specific Issue - e.g., "Fix SQL Injection Vulnerabilities"]
   **Priority:** Critical
   **Estimated Effort:** X hours
   **Description:** Detailed explanation of the issue and why it matters

   **Affected Files:**
   - `/full/path/to/file1.js:45` - Description of issue
   - `/full/path/to/file2.js:123` - Description of issue

   **Acceptance Criteria:**
   - [ ] All parameterized queries implemented
   - [ ] No raw SQL concatenation remains
   - [ ] Unit tests added for input validation

   #### Subtask 1: [Specific action]
   **File:** `/full/path/to/file.js`
   **Lines:** 45-67
   **Action:** Replace string concatenation with parameterized query
   **Details:** [Code snippet or specific instructions AI/developer can immediately act on]
   ```

### Requirements

- [x] **Prioritization** - ✅ Order by severity: Critical → High → Medium → Low
- [x] **Full File Paths** - ✅ Include absolute paths to all files needing modification
- [x] **Line Numbers** - ✅ Reference specific line numbers where issues occur
- [x] **Actionable Details** - ✅ Enough context for AI or developer to immediately start fixing
- [x] **Acceptance Criteria** - ✅ Clear, testable criteria for each story
- [x] **Effort Estimates** - ✅ Based on technical debt hours from analysis
- [x] **Code Snippets** - ✅ Include relevant code excerpts where helpful
- [x] **Cross-References** - ✅ Link related issues that should be fixed together

---

## Future Enhancements

- [ ] Add report comparison (diff two analyses)
- [ ] Support multiple output themes
- [ ] Add executive summary one-pager PDF option
- [ ] Integrate with CI/CD pipelines for automated reporting
- [ ] Add trend tracking across multiple analysis runs

---

## Notes

**Current Implementation (Updated 2026-01-20):**
- PDF/PNG generation now uses html2pdf.js + html2canvas with 4x scale factor
- PNG format used internally for better quality (vs previous JPEG)
- Proper Chart.js wait logic using `Chart.getChart()` API
- Added dedicated PNG export button alongside PDF export

**Remaining work for true headless generation:**
- Consider Node.js script with Puppeteer/Playwright for server-side rendering
- Alternative tools: wkhtmltopdf, or browser-native print-to-PDF
- Upgrade Node.js to support latest Puppeteer if needed
