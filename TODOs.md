# TODOs - Code Review Tool Enhancements

Tracking enhancements and fixes for the Claude Code Review prompt template.

---

## PDF Generation

- [ ] **Fix PDF output quality** - Current Puppeteer PDF export doesn't match the visual quality of index.html in browser
- [ ] **Make PDF generation headless and reliable** - Backend process should not pop up browser export/save prompts
- [ ] **Preserve styling accuracy** - Charts, colors, dark theme, and layout must match browser rendering exactly
- [ ] **Auto-open PDF when complete** - After headless generation, open the resulting PDF for review

---

## PNG Screenshot Generation

- [ ] **Full-page screenshot automation** - Generate pixel-perfect PNG that matches browser experience
- [ ] **High-resolution output** - Minimum 2x device scale factor for crisp rendering
- [ ] **Wait for Chart.js rendering** - Ensure all charts are fully rendered before capture
- [ ] **Current workaround** - Use browser plugin (e.g., GoFullPage) for accurate full-page screenshots until automated solution is reliable

---

## Deliverables

Goal: Automated generation of offline-ready deliverables that exactly match the interactive index.html:

- [ ] `index.html` - Interactive dashboard (current - working)
- [ ] `report.png` - Full-page screenshot (needs automation improvement)
- [ ] `report.pdf` - Print-ready PDF (needs quality fix)
- [ ] `data.json` - Raw metrics data (current - working)

---

## Future Enhancements

- [ ] Add report comparison (diff two analyses)
- [ ] Support multiple output themes
- [ ] Add executive summary one-pager PDF option
- [ ] Integrate with CI/CD pipelines for automated reporting
- [ ] Add trend tracking across multiple analysis runs

---

## Notes

Current PDF/PNG generation uses Puppeteer 13.7.0 (compatible with Node 15.x). Consider:
- Upgrading Node.js to support latest Puppeteer
- Alternative tools: Playwright, wkhtmltopdf, or browser-native print-to-PDF with better settings
- Server-side rendering approach for consistent output
