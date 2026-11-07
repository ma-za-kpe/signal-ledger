# Signal Ledger: architecture

## Information architecture

| Page | Purpose | Primary task | Features |
| --- | --- | --- | --- |
| `index` Signal Ledger | Tell a Canadian security or analytics team what Signal Ledger is, who it is for, and that the research behind it is caveated, so they can decide to open the ledger. | J1 | none |
| `ledger` Ledger | Let the team record, filter, update, pull-by-control and export its evidence items, all on the device. | J2 | M1 Record an evidence item, M2 Filter the ledger, M3 Export a summary packet, M4 Update an item's status, M5 Pull items by control |

## Content per page

### Signal Ledger (`index`)

1. hero: State in one line that Signal Ledger is a working prototype that keeps a current, sourced, on-device record of a team's capabilities, incidents and controls.
2. problem: Explain the practical pain: every bid, audit or strategy review forces the team to rebuild the same evidence from scratch.
3. evidence: Show the StartupTribunal research claims (E1-E3) attributed to StartupTribunal, with the 'rejected by the AI Tribunal, published with caveats' note, so the research is never read as established fact.
4. feature: Describe the four item types (capability, incident, control, dual-use) and the three statuses (ready, in progress, needs work) the ledger records, labelled as the team's own concept.
5. caveats: State the prototype status (F1), the Canadian audience (F2), that data stays on this device, and the research caveat (F4), all visible on a phone without sideways scrolling.

### Ledger (`ledger`)

1. hero: One line: the current, sourced, on-device record of the team's evidence, with the count of items saved on this device.
2. form: Record an evidence item (M1): type, status, owner, date, source, and an optional control reference; the new item is saved to IndexedDB and appears in the list.
3. results: The ledger list (M2, M4, M5): every saved item showing type, status, owner, date and source, with a status control to update in place (M4) and a control selector to pull all items tied to one control (M5).
4. explainer: Explain what a 'summary packet' is and that the export is a single on-device file containing only the currently filtered items.
5. caveats: Remind the user the data lives only on this device and that the export file is the backup if the device is replaced.

## Content model

- **EvidenceItem** (indexeddb): id, type, status, owner, date, source, control, createdAt, updatedAt. The one thing the product keeps: each capability, incident, control or dual-use item the team records. type and status are fixed enums from the PRD; control is an optional free-text reference so P3 can pull all items tied to a named control; createdAt and updatedAt support the 'kept current' success
- **ItemTypes** (static-json): capability, incident, control, dual-use. The four fixed item types from the PRD, bundled as reference data so the form and filters stay in sync with the product's own vocabulary
- **ItemStatuses** (static-json): ready, in-progress, needs-work. The three fixed statuses from the PRD, bundled as reference data for the form, the filter and the in-place status update

## Decisions

### ADR-1 Store evidence items in IndexedDB

- Context: The product must work fully offline on a single device with no server, account or third-party API (the owner's rule for this stage), and P1 must be able to record, filter, update and export items across browser reloads.
- Decision: Use IndexedDB through the kit's useCollection hook, with one collection kind ('evidence-items') for all evidence items.
- Rejected: A hosted database: rejected because it needs a server and accounts, which the offline-first rule excludes.
- Rejected: localStorage: rejected because it has no queries and a ~5 MB cap, which is too small for a growing ledger of sourced items with dates and references.
- Consequences: Data is tied to the browser and device; the export file is the only backup, so the caveats block must say so. A device replacement or a cleared browser store loses the ledger unless the user has exported.

### ADR-2 One island for the whole ledger

- Context: M1 (record), M2 (filter), M4 (update status) and M5 (pull by control) all read and write the same on-device collection and must stay in sync with the list the user is looking at.
- Decision: Put the form, the filter, the list with in-place status update, and the control selector in a single client island (EvidenceLedger) on the Ledger page, so all features share one useCollection subscription and one source of truth.
- Rejected: Separate islands per feature: rejected because each would open its own view of the collection and could show stale data after another feature changed an item, and the user would have to scroll between disconnected blocks.
- Consequences: The island is larger, but it is the only way to keep the list, the filter, the status update and the control pull consistent without a server. The export (M3) reads the same filtered set the island already holds.

### ADR-3 Export as a client-side file download

- Context: M3 requires P1 to export the filtered items as a single on-device summary to hand to a customer or auditor, with no server and no network call.
- Decision: Generate the summary packet in the browser (a text or CSV file built from the currently filtered items) and trigger a download, so the file contains only the filtered items with their type, status, owner, date and source.
- Rejected: A server-side export endpoint: rejected because it needs a server, which the offline-first rule excludes.
- Rejected: A print-to-PDF prompt: rejected because it is not a single, predictable file the user can hand over, and it depends on the browser's print dialog.
- Consequences: The export format is fixed by what the island can build offline; if the team later needs a richer format, the island must be extended. The file is the backup, so the caveats block ties the export to device-replacement risk.

## Non-functional requirements

- The ledger list updates within 100 ms of a status change, a filter change or a new item being saved, with no full page reload.
- The page is usable on a 360 px-wide phone without sideways scrolling (J1 success criterion).
- All content is reachable with a keyboard and announced to screen readers: the form labels its inputs, the list announces a saved or updated item via a live region, and the filter and status controls are focusable buttons or selects.
- The product works with no network connection: no fetch, no third-party API, no external font or script; every feature (record, filter, update, pull-by-control, export) completes offline.
- When IndexedDB is unavailable or the quota is exceeded, the island shows a visible message and never loses a record silently; the user's input stays on screen so they can retry.
- Motion is limited to a small reveal on page blocks and a saved-row highlight, and is disabled entirely when prefers-reduced-motion is set.
- Research claims (E1-E3) are always shown attributed to StartupTribunal with the 'rejected by the AI Tribunal, published with caveats' note; the product's own features are labelled as the team's concept (F1).
