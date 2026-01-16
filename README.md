# Ai-prompts

A collection of AI prompts and tools for code analysis and software engineering.

[![GitHub](https://img.shields.io/badge/GitHub-d--e--v--com%2FAi--prompts-blue?logo=github)](https://github.com/d-e-v-com/Ai-prompts)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Available Tools

### [CLAUDE_CODE_REVIEW.md](CLAUDE_CODE_REVIEW.md)

A comprehensive Claude Code prompt template for generating detailed codebase metrics reports with interactive HTML dashboards and PDF export.

**Features:**
- 14 Metric Categories (complexity, coupling, OO metrics, security, testing, and more)
- AWS Well-Architected Framework alignment scoring
- DocOps Assessment
- Interactive Chart.js dashboard with dark/light mode
- PDF Export

**Quick Start:**
1. Install [Claude Code](https://claude.ai/code)
2. Login to your terminal and start `claude`
3. Enter:
   ```
   load and execute the CLAUDE_CODE_REVIEW.md procedures on the following project code base: /path/to/your/code
   ```
4. Watch the magic happen!

See [CLAUDE_CODE_REVIEW.md](CLAUDE_CODE_REVIEW.md) for full documentation.

---

## Credits

**Code Review Tool & Logic Created by:** [Jacob Baloul](https://www.linkedin.com/in/jacovbaloul/)

**Inspired by:** [Professor Dries Buytaert's work](https://dri.es/measuring-drupal-core-code-complexity) on measuring Drupal core code complexity.

### Key References

- **[drupal-core-metrics](https://github.com/dbuytaert/drupal-core-metrics)** - Professor Dries Buytaert's original metrics analysis tool for Drupal core
- **[Measuring Drupal Code Complexity](https://dri.es/measuring-drupal-core-code-complexity)** - Blog post explaining the methodology

### Standards & Methodologies

- **Chidamber & Kemerer (CK) Metrics** - Original OO metrics suite (1994)
- **MOOD Metrics** - Metrics for Object-Oriented Design by Abreu & Carapuça
- **SonarQube Cognitive Complexity** - Industry standard complexity measurement
- **SQALE Method** - Software Quality Assessment based on Lifecycle Expectations
- **Divio Documentation System** - Four-part documentation framework
- **Google SRE Production Readiness Review** - Operational excellence standards
- **Twelve-Factor App** - Methodology for building SaaS applications
- **ISO/IEC 25010 (SQuaRE)** - Systems and software quality models
- **ITIL v4** - IT Service Management best practices
- **DORA Metrics** - DevOps Research and Assessment performance metrics
- **[AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)** - Six pillars for building secure, high-performing, resilient, and efficient infrastructure

### License

MIT License - See [LICENSE](LICENSE) for details.

This work is inspired by [drupal-core-metrics](https://github.com/dbuytaert/drupal-core-metrics) by Professor Dries Buytaert.
