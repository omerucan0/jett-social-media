<p align="center">
  <img src=".github/assets/cover.svg" alt="Jett Social Media — twelve posts, one unmistakable brand" width="100%" />
</p>

<p align="center">
  <a href="https://github.com/omerucan0/jett-social-media/actions/workflows/ci.yml"><img src="https://github.com/omerucan0/jett-social-media/actions/workflows/ci.yml/badge.svg" alt="CI status" /></a>
  <img src="https://img.shields.io/badge/Codex-skill-111827?style=flat-square" alt="Codex skill" />
  <img src="https://img.shields.io/badge/output-12%20%C3%97%201080%20%C3%97%201350-98f5d1?style=flat-square&labelColor=111827" alt="12 posts at 1080 by 1350" />
</p>

# Jett Social Media

**A production-minded Codex skill for creating complete, brand-specific Instagram campaigns.**

Jett turns a real brand brief into twelve coordinated 4:5 posts: original background imagery, exact typography, a deliberate feed rhythm, a 3×4 review sheet, and upload-ready files. Image generation handles the scenes. A deterministic HTML renderer handles the words. Nothing guesses your logo, invents testimonials, or claims a campaign was published when it was not.

Each invocation derives its visual direction from the current subject and brand. For one editorial concept feed, Jett also supports a combined 12-tile preview with sparse, exact overlays; that preview is not twelve full-resolution production posts. See [topic-led art direction](references/topic-led-art-direction.md).

## What ships

| Output | Details |
| --- | --- |
| 12 finished posts | Individual PNG files, each **1080 × 1350** |
| One coherent feed | A 3×4 review sheet with balanced text placement for production posts |
| Combined concept preview | One text-free composite with deterministic overlays and its own visual review |
| Brand-specific art direction | Brand colors, type, offer, audience, language, and optional logo |
| Review evidence | Contact sheet, technical QA report, and recorded visual-review status |
| Clean handoff | Ready-to-upload assets plus a packaged ZIP |

## Requirements

| Runtime | Used for |
| --- | --- |
| **Python 3.12+** | Campaign setup, manifest validation, and delivery packaging |
| **Node.js 20+ with npm** | Typography rendering, image normalization, and QA |
| **Codex with image generation** | Creating the twelve text-free campaign backgrounds |

Check your machine first:

```bash
python --version
python3 --version
node --version
npm --version
```

Only one Python command needs to work: usually `python` on Windows and `python3` on macOS/Linux.

### Install Python when it is missing

**Windows 10/11**

```powershell
winget install --exact --id Python.Python.3.12
```

Close and reopen the terminal, then run `python --version`. If `python` is not recognized, try `py -3 --version`.

**macOS**

Install the current macOS package from [python.org/downloads](https://www.python.org/downloads/), or use Homebrew:

```bash
brew install python
```

Then run `python3 --version`.

**Ubuntu / Debian**

```bash
sudo apt update
sudo apt install -y python3
```

Then run `python3 --version`. For other systems, use the official [Python downloads page](https://www.python.org/downloads/).

If Node.js is missing, install a current LTS release from [nodejs.org/download](https://nodejs.org/en/download) and reopen the terminal. Full platform notes are in [references/runtime-setup.md](references/runtime-setup.md).

## Install the skill

This repository is **private**. Downloads and cloning require a GitHub account with repository access. Authenticate Git or GitHub CLI before installing.

Clone the current `main` branch into your Codex skills directory:

```bash
git clone https://github.com/omerucan0/jett-social-media.git ~/.codex/skills/jett-social-media
```

On Windows with PowerShell:

```powershell
git clone https://github.com/omerucan0/jett-social-media.git "$HOME\.codex\skills\jett-social-media"
```

Open a new Codex task, then ask for the skill by name:

```text
Use $jett-social-media to create a 12-post Instagram launch campaign
for my brand using the attached logo, brand guidelines, and reference images.
```

### Download or update

- [Latest packaged skill ZIP](https://github.com/omerucan0/jett-social-media/releases/latest/download/jett-social-media.zip) — stable URL for the newest published release.
- [Latest release and checksums](https://github.com/omerucan0/jett-social-media/releases/latest) — version notes and SHA-256 checksum.
- [Current main source ZIP](https://github.com/omerucan0/jett-social-media/archive/refs/heads/main.zip) — follows the newest code on `main`, including changes not yet released.

Sign in with repository access when using these links. Anonymous access to a private repository may return 404. With authenticated GitHub CLI, download the newest release into a fresh directory:

```bash
gh release download --repo omerucan0/jett-social-media --pattern jett-social-media.zip --pattern SHA256SUMS --dir jett-download
```

Extract the `jett-social-media/` folder from the release ZIP into your Codex skills directory. Preserve any customized existing installation before replacing it. A download is a snapshot; installed copies do not update automatically.

For a clean Git installation, inspect local changes and then update from `main`:

```bash
git -C ~/.codex/skills/jett-social-media status --short
git -C ~/.codex/skills/jett-social-media pull --ff-only origin main
```

On Windows, use `"$HOME\.codex\skills\jett-social-media"` for that path. If the working tree has local edits or has diverged, preserve and reconcile those changes before updating. Open a new Codex task to load the updated skill.

### What to provide

Share the brand name, sector, offer, audience, campaign goal, language, colors, and preferred typography. Logo files, approved evidence, reference images, brand voice, and a call to action are helpful when available.

Missing colors or type can be proposed, but they remain explicitly marked as proposals until approved. Unsupported claims, fabricated metrics, and invented testimonials are never substituted for real evidence.

## How it works

1. **Understand the brief.** Separate brand references, visual inspiration, logo assets, and proof.
2. **Choose the art direction and delivery mode.** Derive a topic-specific visual world. Plan a production campaign or a combined editorial preview according to the request.
3. **Generate clean scenes.** For production, create one text-free 4:5 background per post. For a combined preview, compose twelve related tiles together, then overlay copy using the actual quiet areas.
4. **Render the exact copy.** Production uses HTML, Playwright, and Sharp. A combined preview uses a task-local deterministic overlay source fitted to the generated image.
5. **Verify the campaign.** Check dimensions, filenames, unique image content, layout rules, and supported claims.
6. **Review and deliver.** Inspect the feed, record the visual-review result, and package the final files.

The visual-review status stays `UNVERIFIED` until a person or vision-capable agent actually checks the artwork.

## Manual production workflow

For a combined concept preview, follow [the preview workflow](references/topic-led-art-direction.md#combined-editorial-preview); the production renderer does not accept a composite as twelve backgrounds.

For separate production posts, create a campaign from the bundled template:

Windows:

```bash
python scripts/init_campaign.py \
  --dest /absolute/path/to/campaign \
  --brand-name "Your Brand" \
  --campaign-slug your-brand-launch \
  --language en
```

macOS/Linux uses the same arguments with `python3`:

```bash
python3 scripts/init_campaign.py \
  --dest /absolute/path/to/campaign \
  --brand-name "Your Brand" \
  --campaign-slug your-brand-launch \
  --language en
```

Complete `brand/brand.json` and `content/posts.json`, then add the twelve generated background files to `assets/backgrounds/`.

From the campaign directory:

```bash
npm install
npx playwright install chromium
npm run build
```

Inspect the generated contact sheet and representative full-size posts. Record the review before producing the final QA report:

```bash
node scripts/record-visual-review.mjs \
  --status pass \
  --notes "Reviewed the contact sheet and posts 01, 04, 08, and 12."

npm run verify
```

Package the deliverables:

```bash
python /absolute/path/to/jett-social-media/scripts/package_delivery.py \
  --campaign /absolute/path/to/campaign \
  --desktop-dir /absolute/path/to/delivery
```

```text
Your Brand - 12 Post Final/
├── 01-opening-hook.png
├── …
├── 12-final-cta.png
└── preview/
    ├── contact-sheet.png
    ├── qa-report.json
    └── your-brand-launch.zip
```

## Repository layout

```text
jett-social-media/
├── SKILL.md                         Skill entrypoint and operating rules
├── agents/openai.yaml              Codex display name and invocation metadata
├── assets/campaign-template/       Reusable HTML, Node.js, and rendering assets
├── references/                     Intake, content, image, and QA guidance
└── scripts/                        Campaign scaffolding, validation, and delivery
```

The `agents/` directory contains standard Codex skill metadata. It does not run an autonomous agent or connect to an external service.

## Development

Run the regression suite from the repository root:

```bash
python scripts/test_skill.py
```

GitHub Actions checks the Python workflow and JavaScript syntax on both Linux and Windows.

---

<p align="center"><strong>Twelve posts. One clear identity.</strong></p>
