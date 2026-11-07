# Signal Ledger: product requirements

Signal Ledger is a working prototype (F1) that gives a Canadian security or analytics team one current, sourced, on-device record of its capabilities, incidents and controls, so the team can answer a customer, auditor or strategy review with evidence instead of a rebuilt slide deck. The features are

## Problem and evidence

Canadian security and analytics teams must repeatedly prove their capability to government and defence customers, but they have no single, current, sourced record of what they control, what incidents they have handled, and what dual-use capability they hold. Per StartupTribunal, Canada's national security approach has not placed technology at its core (E1), leaving Canadian tech companies underutilized in cybersecurity and dual-use tech and missing contracts, policy influence and growth while Canada imports foreign solutions (E2); the new strategy announcement only implicitly acknowledges this gap (E3). The practical consequence for the team is that every bid, audit or strategy review forces them to rebuild the same evidence from scratch.

- Canada's national security approach has not placed technology at its core. (StartupTribunal, E1)
- This has left Canadian tech companies and innovators underutilized in critical areas like cybersecurity and dual-use tech, causing them to miss out on major contracts, policy influence, and growth opportunities while Canada imports solutions from foreign players. (StartupTribunal, E2)
- The new strategy announcement implicitly acknowledges this long-standing gap. (StartupTribunal, E3)

Who is hurt: Security and analytics teams and customers in Canada (F2) who must assemble and defend a capability record for a contract, audit or strategy review.

## Personas and jobs to be done

### P1 Security capability lead at a Canadian cybersecurity firm bidding on a federal/省

Runs the team that answers a customer's or auditor's question 'what do you actually control and have done?' during a bid or security review.

- Job to be done: When a customer or auditor asks what we actually control and have done, I want a current, sourced record of our capabilities and incidents, so I can answer with evidence instead of a stale slide deck.
- Today's workaround: A folder of spreadsheets and a PowerPoint rebuilt for every bid, so the same facts are re-typed and the latest incident is never in the deck.

### P2 Dual-use technology program manager at a Canadian defence supplier

Tracks which of the company's capabilities map to national-security priorities and is ready for a contract.

- Job to be done: When the strategy review asks which of our capabilities map to national-security priorities, I want to see which capabilities are ready, which are in progress and which need work, so I can direct the team's effort.
- Today's workaround: A status email chain and a single shared document nobody keeps current.

### P3 Compliance analyst at a Canadian analytics firm preparing for a security review

Assembles the evidence packet behind each control for a reviewer.

- Job to be done: When a reviewer asks for the evidence behind each control, I want to pull the items tied to that control with their source and date, so I can hand over a complete packet without digging through email.
- Today's workaround: A search of the team's email and a set of screenshots.

## Alternatives today

- A1 — Capability marketplace: a directory where Canadian security firms list capabilities and customers browse them. Rejected for the first release: it needs many firms and many customers to be useful, and it needs a server and accounts, which the offline-first rule excludes.
- A2 — Live threat-intel feed: a dashboard that pulls in current threat data. Rejected for the first release: it needs a network and a third-party data feed, which the offline-first rule excludes, and it does not solve the team's own record-keeping problem.
- A3 — Local evidence ledger (chosen): a single, offline, on-device record of the team's capabilities, incidents, controls and dual-use items, each with a type, status, owner, date and source, filterable and exportable. Chosen because it directly serves P1's recurring job, works fully offline in the
- reasoningForWedge

## Value proposition

Signal Ledger is a working prototype (F1) that gives a Canadian security or analytics team one current, sourced, on-device record of its capabilities, incidents and controls, so the team can answer a customer, auditor or strategy review with evidence instead of a rebuilt slide deck. The features are

## Solution options and wedge

- O1: Local evidence ledger: record each capability, incident, control or dual-use item with type, status, owner, date and source; filter by status or type; export a summary packet for a customer or auditor. Works offline in the browser with data in IndexedDB.
- O2: Capability marketplace: a browsable directory of Canadian security firms' capabilities for customers to compare. Needs many firms, many customers, a server and accounts.
- O3: Live threat-intel dashboard: a feed of current threat data for the team to monitor. Needs a network and a third-party data feed.

Wedge: O1, Local evidence ledger: record each capability, incident, control or dual-use item with type, status, owner, date and source; filter by status or type; export a summary packet for a customer or auditor. Works offline in the browser with data in IndexedDB. Why: It is the only option that works fully offline with a local database (the owner's rule for this stage), and it directly serves P1's recurring job of assembling a defensible evidence record for a bid or audit. O2 needs many parties and a server; O3 needs a live feed. O1 ships a complete, usable tool,

## Core feature

M1 Record an evidence item, for Security capability lead at a Canadian cybersecurity firm bidding on a federal/省: P1 adds a capability, incident, control or dual-use item with its type, status, owner, date and source, and it is saved on the device and appears in the ledger.

- Primary action: Record an evidence item
- Offline, on the device (indexeddb): yes

## MVP scope

- M1 Record an evidence item (P1): P1 adds a capability, incident, control or dual-use item with its type, status, owner, date and source, and it is saved on the device and appears in the ledger.
- M2 Filter the ledger (P1): P1 filters the ledger by status (ready / in progress / needs work) or by type (capability / incident / control / dual-use) and sees only the matching items.
- M3 Export a summary packet (P1): P1 exports the filtered items as a single on-device summary (a downloadable file) to hand to a customer or auditor.
- M4 Update an item's status (P2): P2 changes an item's status as work progresses, so the ledger reflects the current state of each capability.
- M5 Pull items by control (P3): P3 selects a control and sees every evidence item tied to it with its source and date, ready to hand over as a complete packet.

## Non-goals

- No server, account, payment, live data feed or third-party API (offline-first, local database only).
- No multi-user collaboration or shared workspace (single device, single user).
- No marketplace or directory of other firms' capabilities.
- No live threat-intel ingestion.
- No email or push reminders (needs a server).

## Success metrics

- Evidence item recorded end to end: Under 60 seconds from opening the ledger to a saved item (measured by Time from opening the app to a saved item, measured in the browser.)
- Summary packet exported: Under 30 seconds from a filtered view to a downloaded file (measured by Time from applying a filter to a downloaded export file.)
- Ledger kept current: At least 80% of items updated within 7 days of a status change (measured by Share of items whose last-updated date is within 7 days of the current date.)

## Risks

- The team's real evidence is too varied to fit a fixed set of item types. Test: Pilot with one real bid or audit; check whether the four types (capability, incident, control, dual-use) cover the items the team actually records.
- A single on-device record goes stale or is lost if the device is replaced. Test: Check whether the export packet is used as the backup; measure how often P1 exports after a status change.
- The team does not adopt the ledger because the workaround (spreadsheets) is already familiar. Test: Measure whether P1 records at least one new item per week for four weeks.

## Assumptions

- A Canadian security or analytics team has a recurring, concrete need to assemble a sourced evidence record for a bid, audit or strategy review. Check: Interview P1 and P2 about their last bid or review and what they had to assemble.
- The four item types (capability, incident, control, dual-use) cover the team's real evidence. Check: Pilot with one real bid or audit and check coverage.
- An on-device export is an acceptable hand-off to a customer or auditor. Check: Ask P1 and P3 whether a downloaded file is what they actually hand over.
- The team will keep the ledger current if updating a status is a single action. Check: Measure the share of items updated within 7 days of a status change.

Research claims are the source's and are attributed; every feature is the team's own concept.
