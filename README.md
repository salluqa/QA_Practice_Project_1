# Playwright TypeScript E2E Framework with MCP & CI Integration utilizing Cline AI

A TypeScript-based Playwright automation framework testing [playwright.dev](https://playwright.dev) using Page Object Model architecture, GitHub Actions CI pipeline, and MCP-powered AI browser interactions via Cline.

---

## Architecture

```
project/
├── src/
│   └── PlaywrightHomePage.ts   # Page Object Model
├── tests/
│   └── example.spec.ts         # E2E test specs
├── .github/
│   └── workflows/
│       └── playwright.yml      # CI pipeline
├── playwright.config.ts        # Multi-browser config
├── tsconfig.json               # Strict TypeScript config
└── package.json                # Scripts & dependencies
```

---

## Tech Stack

- **Playwright** — E2E browser automation
- **TypeScript** — strict type safety
- **Page Object Model** — maintainable test abstraction
- **GitHub Actions** — CI pipeline
- **Cline AI + MCP** — AI-driven browser interactions

---

## Setup

```bash
# Install dependencies
npm ci

# Install Playwright browsers
npx playwright install --with-deps
```

---

## Running Tests

```bash
npm test                  # all tests
npm run test:e2e          # E2E project only
npm run test:headed       # visible browser
npm run typecheck         # TypeScript check only
npm run report            # open HTML report
```

---

## CI Pipeline

Triggers on every push to `main`:

```
Checkout → Setup Node → npm ci → Type Check → Install Browsers → Run Tests → Upload Report
```

- Retries: 2 on CI, 0 locally
- Workers: 1 on CI (serial), parallel locally
- Trace collected on first retry
- HTML report retained for 30 days as GitHub Actions artifact

> **Note:** This is CI only — no deployment (CD) step is configured.

---

## Cross-Browser Coverage

| Browser | Engine |
|---|---|
| Chromium | Chrome/Edge |
| Firefox | Gecko |
| WebKit | Safari |

---

## MCP Integration (Cline AI)

The Playwright MCP server was configured via Cline's settings file:

**Config location:**
```
C:\Users\<user>\AppData\Roaming\Code\User\globalStorage\
saoudrizwan.claude-dev\settings\cline_mcp_settings.json
```

**Config:**
```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"],
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

**Exposed tools:** `browser_navigate`, `browser_snapshot`, `browser_click`, `browser_take_screenshot`

Used for AI-driven exploratory testing and rapid page inspection via natural language commands in Cline.

---

## Viewing CI Report

1. Go to repo → **Actions** tab
2. Click a workflow run
3. Scroll to **Artifacts** → download `playwright-report.zip`
4. Extract → open `index.html` in browser

---

## Author

**Muhammad Salman Ali** — Software Quality Assurance Engineer  
[linkedin.com/in/salmanali97](https://www.linkedin.com/in/salmanali97/)
