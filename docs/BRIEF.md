# Signal Ledger: Record an evidence item (first release)

The approved brief, as its issue states it.

## Product

**Signal Ledger is a working prototype (F1) that gives a Canadian security or analytics team one current, sourced, on-device record of its capabilities, incidents and controls, so the team can answer a customer, auditor or strategy review with evidence instead of a rebuilt slide deck. The features are**

- For P1 Security capability lead at a Canadian cybersecurity firm bidding on a federal/省: When a customer or auditor asks what we actually control and have done, I want a current, sourced record of our capabilities and incidents, so I can answer with evidence instead of a stale slide deck.
- For P2 Dual-use technology program manager at a Canadian defence supplier: When the strategy review asks which of our capabilities map to national-security priorities, I want to see which capabilities are ready, which are in progress and which need work, so I can direct the team's effort.
- For P3 Compliance analyst at a Canadian analytics firm preparing for a security review: When a reviewer asks for the evidence behind each control, I want to pull the items tied to that control with their source and date, so I can hand over a complete packet without digging through email.
- Wedge: Local evidence ledger: record each capability, incident, control or dual-use item with type, status, owner, date and source; filter by status or type; export a summary packet for a customer or auditor. Works offline in the browser with data in IndexedDB. Why: It is the only option that works fully offline with a local database (the owner's rule for this stage), and it directly serves P1's recurring job of assembling a defensible evidence record for a bid or audit. O2 needs many parties and a server; O3 needs a live feed. O1 ships a complete, usable tool,
- Core feature: M1 Record an evidence item, for Security capability lead at a Canadian cybersecurity firm bidding on a federal/省; works offline (indexeddb).
- The full PRD is `docs/PRD.md`.

## User stories

### R1 Record an evidence item
- [ ] With the browser offline, entering a type (capability), a status (ready), an owner, a date and a source, and saving, the item appears in the ledger with all five fields shown.
- [ ] After saving, reloading the page with the network off still shows the item in the ledger.
- [ ] The time from opening the ledger to a saved item is under 60 seconds.
Covers: M1 Record an evidence item (for Security capability lead at a Canadian cybersecurity firm bidding on a federal/省)

### R2 Filter the ledger by status or type
- [ ] With 5 items (2 ready, 1 in progress, 2 needs work) and 3 types present, applying the status filter 'in progress' shows only the 1 matching item.
- [ ] Applying the type filter 'dual-use' shows only items of that type; no item of another type is listed.
- [ ] Clearing the filter returns all 5 items to the ledger view.
Covers: M2 Filter the ledger (for Security capability lead at a Canadian cybersecurity firm bidding on a federal/省)

### R3 Export a summary packet
- [ ] With a status filter applied so the ledger shows 3 of 8 items, choosing export downloads a single file containing only those 3 items, each with its type, status, owner, date and source.
- [ ] The time from applying the filter to the downloaded file is under 30 seconds.
- [ ] The downloaded file opens and is readable as a hand-off document.
Covers: M3 Export a summary packet (for Security capability lead at a Canadian cybersecurity firm bidding on a federal/省)

### R4 Update an item's status
- [ ] Selecting an item whose status is 'in progress' and changing it to 'ready' updates the ledger to show 'ready' in a single action.
- [ ] After the change, reloading the page still shows the item with status 'ready'.
- [ ] The item's last-updated date reflects the change, supporting the 80%-within-7-days metric.
Covers: M4 Update an item's status (for Dual-use technology program manager at a Canadian defence supplier)

### R5 Pull items by control
- [ ] With 4 items tied to control 'C-01' (each with a source and date) and 2 items tied to 'C-02', selecting 'C-01' shows exactly those 4 items and no others.
- [ ] Each item in the list shows its source and date.
Covers: M5 Pull items by control (for Compliance analyst at a Canadian analytics firm preparing for a security review)

## Out of scope

- No server, account, payment, live data feed or third-party API (offline-first, local database only).
- No multi-user collaboration or shared workspace (single device, single user).
- No marketplace or directory of other firms' capabilities.
- No live threat-intel ingestion.
- No email or push reminders (needs a server).

## Journeys

- **J1** (visitor) Know what Signal Ledger is, who it is for, and that its research is caveated. Observed: The prototype status, the Canadian audience, the attributed research claim, and the 'rejected/published with caveats' note are all visible on a phone without sideways scrolling.
- **J2** (visitor) Record a first evidence item and see it saved on the device. Observed: The new item appears in the ledger after a reload, showing its type, status, owner, date, and source, with no server required.
- **J3** (owner) Filter the ledger to see only items that need work. Observed: Only items with status 'needs work' are shown, and clearing the filter restores the full list.
- **J4** (owner) Update an item's status as work progresses. Observed: The item now shows status 'ready' in the ledger and the change persists after a reload.
- **J5** (owner) Pull all evidence items tied to a specific control. Observed: Every item tied to that control is shown with its source and date, ready to hand over.
- **J6** (owner) Export a filtered set of items as a summary packet. Observed: The downloaded file contains only the filtered items with their type, status, owner, date, and source.

## Facts the site shows

- `F1`: Status: a working prototype; its features are the team's own concept, and its data stays on this device
- `F2`: Who it is for: Security and analytics teams and customers in Canada
- `F3`: StartupTribunal research reports: Until now, Canada's national security approach has not placed technology at its core. This has left Canadian tech companies and innovators underutilized in critical areas like cybersecurity and dual-use tech, causing them to miss out on major contracts, policy influence, and growth opportunities while Canada imports solutions from foreign players. The new strategy announcement implicitly acknowledges this long-standing gap.
- `F4`: Research status: rejected by the StartupTribunal AI Tribunal, published with caveats.
- `F5`: Research by StartupTribunal: https://startuptribunal.com/catalog/canadian-tech-sidelined-from-national-security-strategy

## Assumptions

- A public repository and a public site on GitHub Pages; no server or database.
- The frozen tests under `tests/` are the acceptance contract; changing them needs the owner's approval.
- Facts appear exactly as the brief gives them.
