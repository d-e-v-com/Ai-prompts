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

Goal: Automated generation of offline-ready deliverables that exactly match the interactive index.html:

- [x] `index.html` - Interactive dashboard (working)
- [x] `report.png` - Full-page screenshot (✅ FIXED: 4x scale, Chart.js wait logic)
- [x] `report.pdf` - Print-ready PDF (✅ FIXED: PNG-based, 4x scale)
- [x] `data.json` - Raw metrics data (working)

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
