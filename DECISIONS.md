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
