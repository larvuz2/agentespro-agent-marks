# Agent Marks

A small, dependency-free SVG identity engine for agent profiles.

**One silhouette. One flat color. One, two, or three live eyes.**

Agent Marks is built for self-hosted agent products, enterprise deployments, and interfaces that need memorable identities without relying on external avatar services.

## What it does

- Generates a stable identity from any seed: `Larvuz` will always render as Larvuz.
- Uses 18 constrained SVG silhouettes and 11 flat color presets.
- Supports one, two, or three large responsive eyes.
- Adds subtle pointer gaze, spring physics, blinking, breathing, and hover presence.
- Lets users randomize, set a seed, pick a color, select a form, and control eye count.
- Produces a compact profile payload that can be saved in an agent profile.
- Runs entirely in the browser. No canvas, model, WebGL, generated image API, or tracking.

## Run locally

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## Use in an app

```html
<div id="larvuz-mark"></div>
<script type="module">
  import { AgentMark } from './agent-marks.js';

  new AgentMark(document.querySelector('#larvuz-mark'), {
    seed: 'larvuz',
    size: 72,
    interactive: true,
  });
</script>
```

## Data contract

Use a deterministic fallback until a person customizes an avatar:

```yaml
avatar:
  mode: generated
  version: 1
  seed: larvuz
  shape: auto
  color: auto
  eyes: auto
```

Once customized, persist only a small explicit payload:

```yaml
avatar:
  mode: generated
  version: 1
  seed: larvuz
  shape: jelly
  color: violet
  eyes: 3
```

For agentesPRO, this belongs in the existing profile metadata / `profile.yaml`. Render the exact same payload in Agent Chats, agent details, settings, and enterprise profile cards.

## Design rules

- No gradients.
- No texture.
- No limbs, mouths, clothing, or illustrated monster features.
- No random appearance on page reload.
- Custom choices always override the deterministic fallback.

## License

MIT
