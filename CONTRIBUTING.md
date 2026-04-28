# Contributing to Fact Spreader

Thank you for your interest in contributing! This guide will help you get set up.

## Development Setup

```bash
git clone https://github.com/factspreaders/fact-spreader.git
cd fact-spreader
npm install
npm run dev        # watch mode — rebuilds on changes
```

Load the extension in Chrome:

1. Open `chrome://extensions/`
2. Enable "Developer mode"
3. Click "Load unpacked" → select `dist-chrome/`

## Code Style

- **Linting**: `npm run lint` — we use ESLint with the project config
- **Formatting**: follow existing code style; use meaningful variable names
- **Commits**: use conventional commit messages (`feat:`, `fix:`, `refactor:`, etc.)

## Project Structure

```
src/
├── background/     # Service worker (Manifest V3 background script)
├── content/        # Content scripts injected into web pages
├── popup/          # Extension popup UI (Svelte + Tailwind)
├── options/        # Settings/options page
└── shared/         # Shared utilities, LLM adapters, types
```

## Adding a New LLM Provider

1. Create a new adapter in `src/shared/providers/`
2. Implement the standard interface (`sendMessage`, `validateConfig`)
3. Register it in `src/shared/providerRegistry.ts`
4. Add options UI in `src/options/`
5. Add tests

## Testing

```bash
npm run test        # Playwright end-to-end tests
npm run build       # verify production build succeeds
```

## Pull Request Guidelines

- Keep PRs focused — one feature or fix per PR
- Update tests if you change behavior
- Run `npm run lint` before submitting
- Link related issues in the PR description

## Local LLM Testing

To test with local models:

1. Install [Ollama](https://ollama.com) or [LM Studio](https://lmstudio.ai)
2. Start the local server (Ollama: `ollama serve`, LM Studio: enable API server)
3. Configure the endpoint in extension options

## Questions?

Open a [discussion](https://github.com/factspreaders/fact-spreader/discussions) or reach out via an issue.
