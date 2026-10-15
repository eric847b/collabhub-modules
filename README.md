# collabhub-modules

Standalone CollabHub "Nexus" userscripts and a tag-driven release pack, part of the Third Door fleet's browser layer.

**Version:** see `VERSION` (pack `1.0.0`; `package.json` tracks the Nexus line `25.0`) · **License:** MIT

## Contents

| File | Version | Status |
|---|---|---|
| `99-OmniNexus-Final.module.user.js` | 99.0 | **Current** — use this one |
| `archive/25-FinalNexus.module.user.js` | 25.0 | Superseded by 99 |
| `archive/23-UltimateNexus.module.user.js` | 23.0 | Superseded by 99 |
| `archive/22-CompleteNexus.module.user.js` | 22.0 | Superseded by 99 |
| `evolve.js` | — | Placeholder evolve cycle (`npm run evolve`); logs status only |
| `.github/workflows/release.yml` | — | Packs the repo into a zip on `v*` tags or manual dispatch |

Each Nexus script is a Tampermonkey userscript that matches `*://*/*`, stores provider API keys with `GM_setValue`/`GM_getValue` (never hardcoded), and calls OpenAI, Anthropic, and Groq via `GM_xmlhttpRequest`. Features named in the script headers: segmented math, infinite echo, vision, voice, consensus, AutoForge, and self-tuning.

## Install

1. Install [Tampermonkey](https://www.tampermonkey.net/).
2. Open `99-OmniNexus-Final.module.user.js` (Raw) and accept the install prompt.
3. Use the Tampermonkey menu command to enter your own provider keys.

Install only one Nexus version at a time; they overlap. Superseded versions live in `archive/`.

## Release

```bash
git tag v1.0.1
git push origin v1.0.1
```

## Relationship to the fleet

- **Canonical userscript suite:** `ai-chat-websites` (hub + modules). These Nexus scripts are standalone and do not require the hub.
- **Nested mirror:** `AI-Collaboration-Hub/collabhub-modules/` also contains the FreeAI rotator (`src/rotator.js`, `run-ai.js`, `FreeAIRotator.module.user.js`). That mirror is synced `missing-only`; this standalone repo is the source of truth for the files above.
- **Contracts:** module shape, key handling, and model routing follow the Third Door fleet contracts (`third-door-os/docs/CONTRACTS.md`, §6.2 and §8).

## Roadmap

- Bring the FreeAI rotator into this repository so standalone and mirror match.
- Route provider calls through the free-first ladder (local → keyless → free tiers → paid opt-in).
- Replace the placeholder `test`/`build`/`evolve` scripts with a real header lint and syntax check.
