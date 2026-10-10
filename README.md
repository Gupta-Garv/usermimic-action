# UserMimic Autonomous Vision QA — Official GitHub Action

[![GitHub Action](https://img.shields.io/badge/GitHub_Action-UserMimic_Vision_QA-yellow?logo=githubactions&logoColor=white)](https://github.com/Gupta-Garv/usermimic-action)
[![Release](https://img.shields.io/badge/Release-v1.2.4-blue.svg)](https://github.com/Gupta-Garv/usermimic-action/releases)
[![NVIDIA Inception](https://img.shields.io/badge/NVIDIA_Inception-Program_Member-76B900?logo=nvidia&logoColor=white)](https://usermimic.tech)
[![SOC 2 Type II](https://img.shields.io/badge/SOC_2_Type_II-In--Audit-success)](https://usermimic.tech/#legal-security)
[![License](https://img.shields.io/badge/License-Apache_2.0-orange.svg)](LICENSE)

> **Deploy autonomous multimodal vision swarm agents to stress-test web applications, catch visual layout regressions, and eliminate brittle DOM selector debt directly inside your CI/CD pipeline.**

Official Platform: [https://usermimic.tech](https://usermimic.tech)  
Console & Documentation: [https://usermimic.tech/#engine](https://usermimic.tech/#engine)

---

## ⚡ The Problem: Brittle DOM Selectors

Traditional end-to-end automation tools (Playwright, Cypress, Selenium) rely on rigid DOM selectors:
```javascript
// ❌ Traditional Brittle Test: Breaks whenever CSS classes or DOM structure changes
await page.click('div.checkout-v2 > div.flex-row > button.btn-primary-389');
```
When design systems refactor Tailwind classes, change button hierarchies, or introduce dynamic A/B test overlays, test suites fail with false positives—costing engineering teams **15–20 hours per sprint** in test maintenance debt.

## 🎯 The UserMimic Solution: Zero-Selector Optical Perception

UserMimic deploys frontier multimodal vision models that perceive web applications the same way human eyes do:
- **No brittle CSS, IDs, or XPath selectors.**
- Perceives raw rendered viewports and spatial layout hierarchies.
- Detects overlapping sticky banners, unclickable buttons, layout overflows, and checkout blockers.
- Adapts autonomously to UI redesigns while catching real UX regressions.
- Automatically exports **WebM session reproduction videos** and **executable Playwright repro scripts** for any flagged failure.

---

## 🚀 Quickstart

Add the UserMimic Action to your pull request or deployment workflow:

```yaml
name: Autonomous Visual QA

on:
  pull_request:
    branches: [main, develop]
  deployment_status:

jobs:
  usermimic-vision-audit:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Run UserMimic Vision Swarm
        uses: Gupta-Garv/usermimic-action@v1
        with:
          api-key: ${{ secrets.USERMIMIC_API_KEY }}
          project-id: 'proj_84920482'
          base-url: 'https://preview-${{ github.event.pull_request.number }}.yourdomain.com'
          personas: 'Elena,Marcus,Kai'
          chaos-level: 65
          fail-on-regression: true
          export-video: true
```

---

## ⚙️ Configuration Inputs

| Input | Required | Default | Description |
| :--- | :---: | :---: | :--- |
| `api-key` | **Yes** | — | Your UserMimic Enterprise workspace API token. |
| `project-id` | **Yes** | — | UserMimic project or application UUID. |
| `base-url` | **Yes** | — | Target staging URL or preview deployment to audit. |
| `personas` | No | `Elena,Marcus,Kai` | Comma-separated synthetic persona swarm to deploy. |
| `chaos-level` | No | `65` | Autonomous exploratory chaos coefficient (0 = strict deterministic, 100 = hyper-chaotic edge-case hunting). |
| `fail-on-regression` | No | `true` | Whether to fail the GitHub Actions job if high-severity visual blockers are detected. |
| `export-video` | No | `true` | Generate downloadable WebM session video recordings of every simulated run. |
| `export-playwright` | No | `true` | Generate reproducible Playwright test scripts from recorded failures. |

---

## 📤 Action Outputs

| Output | Description |
| :--- | :--- |
| `status` | Execution result: `passed`, `failed`, or `flagged`. |
| `runs-executed` | Total autonomous user journeys executed during the run. |
| `regressions-count` | Number of layout anomalies or interaction friction blockers caught. |
| `report-url` | Deep-link to the UserMimic interactive session trace & heatmaps. |

---

## 🤖 Built-in Autonomous Personas

| Persona | Archetype | Target Focus |
| :--- | :--- | :--- |
| **Elena** | Rapid Clicker | Double-clicks un-debounced buttons, rapid tab navigation, spam-clicks CTA spinners. |
| **Marcus** | Power User | Deep workflow navigation, 15+ filter toggles, complex multi-step data entry. |
| **Chloe** | Distracted Mobile | Rapid viewport resizing, interrupted payment checkouts, background tab switches. |
| **Kai** | Accessibility (A11y) | Keyboard focus-traps, tab sequencing, contrast thresholds, and foreign RTL overflows. |

---

## 🔒 Security & Data Governance

- **NVIDIA Inception Program Member:** Vision inference pipelines accelerated on dedicated TensorRT GPU clusters.
- **In-Memory Zero Data Retention (ZDR):** Frame buffers and session telemetry are processed in volatile memory and purged immediately post-execution.
- **SOC 2 Type II & ISO 27001 Controls:** Dedicated isolated Firecracker microVM sandboxes for all test executions.
- **RFC 9116 Compliant:** Security disclosures available at `/.well-known/security.txt`.

---

## 📄 License & Commercial Support

- **Action Source Code:** Licensed under the [Apache License 2.0](LICENSE).
- **Enterprise Platform:** UserMimic Technologies Inc.
- **Website:** [https://usermimic.tech](https://usermimic.tech)
- **Support & Security Office:** [garv@usermimic.tech](mailto:garv@usermimic.tech)
- **Crunchbase:** [crunchbase.com/organization/usermimic](https://www.crunchbase.com/organization/usermimic)
- **LinkedIn:** [linkedin.com/company/usermimic](https://www.linkedin.com/company/usermimic)
