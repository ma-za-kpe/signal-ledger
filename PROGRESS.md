# Progress: Signal Ledger

As of this commit. Trusted code writes this file from the job's journal; every role reads it first (`AGENTS.md`, Start here).

0 of 5 features pass.

## Features

| Feature | Title | Page | Status | Passes |
| --- | --- | --- | --- | --- |
| M1 | Record an evidence item | `index` | in-progress | no |
| M2 | Filter the ledger | `index` | in-progress | no |
| M3 | Export a summary packet | `index` | in-progress | no |
| M4 | Update an item's status | `index` | in-progress | no |
| M5 | Pull items by control | `index` | in-progress | no |

## Current sprint

Sprint contract: Design direction: home page and shared style

Done means, for each feature:

- [ ] M1 Record an evidence item: P1 adds a capability, incident, control or dual-use item with its type, status, owner, date and source, and it is saved on the device and appears in the ledger. (on `index`, working offline)
- [ ] M2 Filter the ledger: P1 filters the ledger by status (ready / in progress / needs work) or by type (capability / incident / control / dual-use) and sees only the matching items. (on `index`, working offline)
- [ ] M3 Export a summary packet: P1 exports the filtered items as a single on-device summary (a downloadable file) to hand to a customer or auditor. (on `index`, working offline)
- [ ] M4 Update an item's status: P2 changes an item's status as work progresses, so the ledger reflects the current state of each capability. (on `index`, working offline)
- [ ] M5 Pull items by control: P3 selects a control and sees every evidence item tied to it with its source and date, ready to hand over as a complete packet. (on `index`, working offline)

Checked by the implementer, on the exact head:

- `npm run build`
- `python tests/site_view.py && python -m unittest discover -s tests`
- `node tests/browser/qa.mjs`

Judged by the evaluator, on the rendered product: every criterion (design, originality, depth, craft, functionality) scores at least 7 of 10, and so do its 6 hidden rubric categories. Below that the task holds; it never merges.

## Recent commits

- `15532587cc03` on `feature/issue-2-home`: docs: product requirements, architecture and design system
- `dc70530bdde7` on `feature/issue-2-home`: docs: brief, plan, decisions, handoff and run record
