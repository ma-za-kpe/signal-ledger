# Signal Ledger experience

## Information architecture

### `/`

The custody workspace: the place a security or analytics team member records an evidence item and keeps the chain of custody intact, entirely on this device. Primary task: Record an evidence item and stamp it into the local custody ledger.

| Section | Purpose | Layout | Components | Moment |
| --- | --- | --- | --- | --- |
| Custody header | Orient the user to the device's local state and give immediate access to the core task (record an item) and to search. | split | Local-Storage Status Strip, New Entry Button, Search Field, Item ID Field | load |
| Evidence item hero | Present the single item being recorded or last stamped as the hero: a stamped item label with its ID, timestamp, and local/offline status. | hero | Evidence Tag (hero), Item ID Field, Timestamp Stamp, Local-Storage Status Strip | save |
| Custody ledger | Show every evidence item recorded on this device as numbered ledger rows, each with its item ID, timestamp, and custody state. | table | Custody Ledger Row, Ledger Action Menu, Item ID Field, Timestamp Stamp | custody add |
| Chain-of-custody line | Trace the custody of the selected item as a plain line of handoffs, each stamped with a timestamp and the local device. | band | Chain-of-Custody Line, Timestamp Stamp, Local-Storage Status Strip | custody add |
| Record &amp; export band | Close the loop: confirm the item is saved locally and offer to export the ledger, with the on-device-only caveat stated plainly. | steps | Export Action, Local-Storage Status Strip, New Entry Button | export |

### `/item/:id`

The full custody view for one evidence item: its stamped label, complete chain of custody, and local status. Primary task: Review and extend the chain of custody for a single item.

| Section | Purpose | Layout | Components | Moment |
| --- | --- | --- | --- | --- |
| Item header | Show the item's stamped label, ID, and current local/offline status at the top. | hero | Evidence Tag (hero), Item ID Field, Timestamp Stamp, Local-Storage Status Strip | load |
| Custody line | List every handoff for this item as a stamped line, newest first, all on this device. | band | Chain-of-Custody Line, Timestamp Stamp, Ledger Action Menu | custody add |
| Record a handoff | Add the next custody event for this item and stamp it locally. | split | Item ID Field, Timestamp Stamp, New Entry Button, Local-Storage Status Strip | save |
| Export this item | Export this item's custody record as a local file, with the on-device caveat. | band | Export Action, Local-Storage Status Strip | export |

### `/export`

Export the full custody ledger from this device as a local file, with the on-device-only caveat stated plainly. Primary task: Export the local custody ledger.

| Section | Purpose | Layout | Components | Moment |
| --- | --- | --- | --- | --- |
| Export summary | State how many items are on this device and that the export is local only. | hero | Local-Storage Status Strip, Export Action | load |
| Ledger preview | Show the rows that will be exported as numbered ledger rows. | table | Custody Ledger Row, Item ID Field, Timestamp Stamp | search |
| Export action | Trigger the local export and confirm it completed on this device. | band | Export Action, Local-Storage Status Strip | export |

## Flows

- **Record an evidence item**: Open the custody workspace at /. → Press the New Entry Button in the header. → Enter the item ID in the Item ID Field and the item details. → Press the stamp control to apply the Timestamp Stamp. → The entry is saved to local storage and the Local-Storage Status Strip updates. → A new Custody Ledger Row is added and the Chain-of-Custody Line updates.
- **Search existing items**: Type an item ID or keyword into the Search Field. → The custody ledger filters to matching Custody Ledger Rows. → Select a row to open its custody view at /item/:id.
- **Open a custody view**: Select a Custody Ledger Row in the ledger. → The Chain-of-Custody Line for that item is shown. → Open the full view at /item/:id to review every handoff.
- **Export the ledger**: Press the Export Action in the record &amp; export band. → The ledger is written to a local file on this device. → The Local-Storage Status Strip confirms the export completed locally.
- **Handle an offline change**: Make a change while the device is offline. → The change is written to local storage and the Local-Storage Status Strip updates. → No account or sync is involved; the data stays on this device.

## Screen states

| Screen | empty | loading | error | success |
| --- | --- | --- | --- | --- |
| Record an evidence item | No evidence recorded on this device. | Preparing local ledger… | Local save failed — your entry has not been stamped. | Entry stamped locally; custody line updated. |
| Custody ledger | No evidence recorded on this device. | Preparing local ledger… | Local save failed — your entry has not been stamped. | Entry stamped locally; custody line updated. |
| Chain-of-custody line | No custody events for this item yet. | Preparing local ledger… | Local save failed — your entry has not been stamped. | Custody event stamped locally; line updated. |
| Export the ledger | Nothing to export — no evidence recorded on this device. | Preparing local ledger… | Export failed — the file was not written to this device. | Ledger exported to this device. |

## Interactions

| Trigger | Response | Duration |
| --- | --- | --- |
| Page load at / | Staggered reveal: the custody header, then the evidence item hero, then the custody ledger rows, then the chain-of-custody line, then the record &amp; export band, | `load` |
| Press the stamp control after entering an item | The Timestamp Stamp presses in, then the entry settles into the ledger and the Local-Storage Status Strip updates. | `save` |
| A new custody event is added | A new Custody Ledger Row and Chain-of-Custody Line entry slide into place. | `custody add` |
| A change is made while offline | The Local-Storage Status Strip settles to reflect the on-device change; no sync is attempted. | `offline change` |
| Type in the Search Field | The custody ledger filters to matching rows as the user types. | `search` |
| Press the Export Action | The ledger hands off to a local file and the status strip confirms the export. | `export` |
| A local save fails | The error state is shown and the status strip settles to the failure message. | `error` |
