# Plan

## Pages

| Page | Title | Purpose | Facts |
|---|---|---|---|
| `/` | Signal Ledger | Tell a Canadian security or analytics team what Signal Ledger is, who it is for, and that the research behind it is caveated, so they can decide to open the ledger. | F1, F2, F3, F4, F5 |

## Tasks

Status as of this commit.

| Issue | Task | Status |
|---|---|---|
| [#2](https://github.com/ma-za-kpe/signal-ledger/issues/2) | Design direction: home page and shared style | In progress |

## How the work is planned

Build one feature at a time, in this order, each to its sprint contract: M1 Record an evidence item on index; M2 Filter the ledger on index; M3 Export a summary packet on index; M4 Update an item's status on index; M5 Pull items by control on index

## Experience

Signal Ledger (index): Tell a Canadian security or analytics team what Signal Ledger is, who it is for, and that the research behind it is caveated, so they can decide to open the ledger.
  1. hero: State in one line that Signal Ledger is a working prototype that keeps a current, sourced, on-device record of a team's capabilities, incidents and controls.
  2. problem: Explain the practical pain: every bid, audit or strategy review forces the team to rebuild the same evidence from scratch.
  3. evidence: Show the StartupTribunal research claims (E1-E3) attributed to StartupTribunal, with the 'rejected by the AI Tribunal, published with caveats' note, so the research is never read as established fact.
  4. feature: Describe the four item types (capability, incident, control, dual-use) and the three statuses (ready, in progress, needs work) the ledger records, labelled as the team's own concept.
  5. caveats: State the prototype status (F1), the Canadian audience (F2), that data stays on this device, and the research caveat (F4), all visible on a phone without sideways scrolling.
Ledger (ledger): Let the team record, filter, update, pull-by-control and export its evidence items, all on the device.
  1. hero: One line: the current, sourced, on-device record of the team's evidence, with the count of items saved on this device.
  2. form: Record an evidence item (M1): type, status, owner, date, source, and an optional control reference; the new item is saved to IndexedDB and appears in the list.
  3. results: The ledger list (M2, M4, M5): every saved item showing type, status, owner, date and source, with a status control to update in place (M4) and a control selector to pull all items tied to one control (M5).
  4. explainer: Explain what a 'summary packet' is and that the export is a single on-device file containing only the currently filtered items.
  5. caveats: Remind the user the data lives only on this device and that the export file is the backup if the device is replaced.
The design system: docs/design/ and brand/; the tokens: app/tokens.css.
