# Fact Spreader

A privacy-first Chrome extension for AI-powered fact-checking. Highlight any text or image on the web and send it to your choice of LLM — cloud or local.

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Chrome Web Store](https://img.shields.io/badge/Chrome%20Web%20Store-available-green?logo=google-chrome)](https://chromewebstore.google.com/detail/fact-checker-gpt-connecto/jikiecjhdofccpaejidggiiiejogemni)
[![Manifest V3](https://img.shields.io/badge/Manifest-V3-orange)](https://developer.chrome.com/docs/extensions/mv3/)

![Fact Spreader screenshot](images/check_result.png)

## Why Fact Spreader?

Most "AI fact-checking" tools are black boxes. Fact Spreader is transparent by design:

- **Your choice of LLM** — ChatGPT, Claude, Gemini (cloud) or Ollama, LM Studio (local)
- **Privacy-first** — local models keep data on your device; no telemetry
- **Image fact-checking** — right-click any image to verify it
- **Knowledge graph support** — optional [lightRAG](https://github.com/HKUDS/lightRAG) integration for source-backed verification
- **Customizable personas** — Scientist, Acerbic Rationalist, or define your own

## Quick Start

### Install from Chrome Web Store

[Install Fact Spreader from the Chrome Web Store](https://chromewebstore.google.com/detail/fact-checker-gpt-connecto/jikiecjhdofccpaejidggiiiejogemni)

### Developer Setup

```bash
git clone https://github.com/factspreaders/fact-spreader.git
cd fact-spreader
npm install
npm run build        # outputs to dist-chrome/
```

Then in Chrome:
1. Open `chrome://extensions/`
2. Enable "Developer mode"
3. Click "Load unpacked" → select `dist-chrome/`

### Configure an LLM Provider

1. Right-click the extension icon → "Options"
2. Choose a provider and enter your API key (for cloud models)
3. Or configure Ollama/LM Studio endpoint for local models

## Architecture

```
src/
├── background/     # Service worker (Manifest V3)
├── content/        # Content scripts injected into pages
├── popup/         # Extension popup UI (Svelte)
├── options/        # Options/settings page
└── shared/         # Shared utilities, API clients
```

- **Manifest V3** service worker architecture
- **Svelte** frontend with Tailwind CSS
- **Multi-provider LLM layer** — adapters for OpenAI, Anthropic, Google, Ollama, LM Studio
- **Context menu integration** — right-click text/image selection
- **Optional lightRAG** — configurable endpoint for knowledge-graph verification

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Development Workflow

```bash
npm run dev            # watch mode (Chrome)
npm run build          # production build
npm run lint           # ESLint check
npm run test           # Playwright e2e tests
```

### Reporting Issues

- **Bug reports**: use the [bug report template](https://github.com/factspreaders/fact-spreader/issues/new?template=bug_report.md)
- **Feature requests**: use the [feature request template](https://github.com/factspreaders/fact-spreader/issues/new?template=feature_request.md)

## License

[MIT License](LICENSE) — © 2024 Fact Spreaders

## Privacy

- All configuration is stored locally in your browser
- No data is sent to Fact Spreaders servers
- Cloud LLM requests go directly to your chosen provider (OpenAI, Anthropic, Google)
- Local LLM requests never leave your device
