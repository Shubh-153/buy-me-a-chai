# Decisions Log

Record of decisions made for this project, in chronological order.

## 2026-08-17 — Repository setup

- **Initialize as a git repo and publish to GitHub.** Project started as a single untracked file (`upi-sponsor-widget.html`) with no `.git` directory.
- **Repo name:** `buy-me-a-chai`, created under the `Shubh-153` GitHub account.
- **Visibility: public.** Chosen over private when asked.
- **Default branch:** `main`.
- Initial commit contains only `upi-sponsor-widget.html`.

## 2026-08-17 — Code review follow-up

- Reviewed `upi-sponsor-widget.html` and identified a list of potential improvements (bugs, functionality gaps, robustness/security, accessibility, repo hygiene) — see conversation history for the full list.

## 2026-08-17 — Fixed init-state bug and generic placeholder

- **Fixed:** on page load, the ₹49 tier button rendered as `.active` while `amountMode` was `'open'`, making two conflicting selections appear active simultaneously. Removed the stray `classList.add('active')` call on init; tiers now only show a selection once the user switches to "Fixed amount" mode.
- **Fixed:** "Display name" placeholder was hardcoded to `"Shubh"` (the author's own name). Changed to the generic `"Your Name"` since the tool is meant to be reused by others.
- Remaining items from the review (custom fixed-amount input, SRI hash on the QRious CDN script, accessibility label wiring, README/LICENSE, etc.) are **not yet actioned**.

## 2026-08-17 — Sponsor badge added to README

- Added a `### ☕ Sponsor via UPI` section to a new `README.md`, embedding the repo owner's own generated badge (base64 SVG) + QR (base64 PNG) for UPI ID `shubhgupta194@oksbi`.

## 2026-08-17 — Full color customization, embedded preview, README preview image, footer CTA

- **Color customization:** added 6 `<input type="color">` controls (badge background/text, QR foreground/background, ticket background/text) so the *generated* badge/QR/ticket can be recolored to match any site's branding. Scoped deliberately to only the embeddable widget's colors — the generator page's own dark UI theme (`--bg-deep`, `--accent-marigold`, etc.) stays fixed, since those are two different concerns. A "Reset" control restores the original marigold/cream defaults. Known accepted limitation: the "SCAN TO PAY" label and the ticket's perforation punch-holes stay on fixed page colors, out of the requested scope.
- **Embedded preview:** added a second preview block beneath the existing stylized "ticket" mockup, showing the *actual* bare badge + bare QR images (what really gets pasted) against a Light/Dark backdrop toggle — the existing ticket mockup has decorative chrome (cream card, perforation) that isn't part of the real embedded output, so this closes that gap. Dark backdrop uses `#0d1117`, GitHub's actual dark-mode background color, so the toggle previews the real target surface.
- **README preview image:** added `assets/preview.svg`, a hand-authored static SVG mirroring the ticket's look (no live screenshot tooling was available in this environment — Chrome isn't installed, only Safari, and the browser-automation tool requires Chrome). Uses only system font fallbacks since GitHub's SVG sandbox won't fetch Google Fonts. Referenced from a new `## Preview` section in README.md.
- **Footer sponsor CTA:** added a "Enjoying this tool? Sponsor via UPI" block to the bottom of `index.html`, reusing the exact same base64 badge/QR already committed in README.md (same UPI ID, copy-pasted verbatim rather than regenerated, to avoid any risk of corrupting the base64).
