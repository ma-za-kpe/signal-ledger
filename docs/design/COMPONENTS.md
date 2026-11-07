# Signal Ledger components (U4, U5)

## Evidence Tag (hero)

The stamped evidence item, the hero of every screen. It carries the item ID, description, and the custody line, and it is the thing the user is recording.

Anatomy: stamped item label (item-id icon + ID), description field, custody-chain line, timestamp stamp, local/offline status chip.

| State | Treatment |
| --- | --- |
| default | Surface card on paper, ink text, item label in mono, single accent rule under the ID. |
| hover | Line darkens one step; no lift, no shadow, the tag does not float. |
| focus | 2px focus ring (#1f4e79) around the focused inner field; the tag outline stays quiet. |
| active | Pressed field shows a 1px inset; the stamp re-inks at stamp 180ms. |
| disabled | Muted text, line border, accent rule removed; fields not editable. |
| loading | Skeleton tag: label and custody line as muted bars, no accent, settle 240ms. |
| empty | Dashed outline, item-id icon, plain-spoken line: No item logged yet. Stamp the first one below. |
| error | Danger border on the failing field, danger message in the ledger's voice: Item ID is missing, the tag cannot be stamped. |
| success | Success tick beside the timestamp, Logged to this device. Accent reserved for the ID only. |
| selected | Left accent bar + surface fill; used when the tag is the open entry in the ledger. |
| offline | Local-data chip reads On this device; no sync language, no red, offline is the normal state. |

## Custody Ledger Row

One line in the chain-of-custody ledger: who handled the item, when, and the action. Rows stack into the ledger the user is accountable for.

Anatomy: handler name, action word, timestamp (mono), item-id reference, row status dot.

| State | Treatment |
| --- | --- |
| default | Ledger row on surface, hairline line divider, mono timestamp, ink text. |
| hover | Surface darkens one step; the status dot gains a 1px ring. |
| focus | Full-row focus ring (#1f4e79) for keyboard users; row is a 44px target. |
| active | Pressed fill; the row's custody add animates in at ledger 360ms. |
| disabled | Muted text, no dot; used for a row locked after a break. |
| loading | Two muted bars in place of name and timestamp, settle 240ms. |
| empty | Not applicable to a single row; the ledger container owns the empty state. |
| error | Danger dot + danger text: Custody break, the chain is not continuous. |
| success | Success dot; Handed off and recorded. |
| selected | Accent left bar + surface fill; the row the tag is currently bound to. |
| offline | Local-data dot in muted; Recorded on this device. |

## Item ID Field

Captures or generates the numbered evidence tag ID. It is the identity of the item and the first thing stamped.

Anatomy: mono input, item-id icon, prefix label, generate button.

| State | Treatment |
| --- | --- |
| default | Mono input on surface, line border, item-id icon at left, ink text. |
| hover | Border darkens one step. |
| focus | 2px focus ring (#1f4e79); caret in mono. |
| active | Pressed generate button re-inks the ID at stamp 180ms. |
| disabled | Muted, non-editable; used once the tag is stamped. |
| loading | Muted bar in the input while an ID is generated, settle 240ms. |
| empty | Placeholder e.g. EV-0001; no error until submit. |
| error | Danger border + ID must be unique on this device. |
| success | Success tick; the ID is stamped and locked. |
| selected | Not applicable to a field; the parent tag owns selection. |
| offline | Local-data note: Stored on this device. |

## Timestamp Stamp

The stamped time an action happened, in mono, with the device's local clock. It is the accountability mark on every entry.

Anatomy: mono time value, timestamp icon, device clock label, stamp mark.

| State | Treatment |
| --- | --- |
| default | Mono value in ink, timestamp icon, quiet line rule. |
| hover | Rule darkens one step. |
| focus | Focus ring (#1f4e79) when the stamp is editable or adjustable. |
| active | Stamp re-inks at stamp 180ms with a settle 240ms. |
| disabled | Muted; a stamped time cannot be changed. |
| loading | Muted bar while the clock is read, settle 240ms. |
| empty | Not applicable; a stamp always has a time. |
| error | Danger text: Clock could not be read on this device. |
| success | Success tick; Time recorded. |
| selected | Not applicable to a stamp. |
| offline | Local-data note: Local device time. |

## Local-Storage Status Strip

The always-present strip that says where the data lives: on this device. It is the offline-first truth of the product and never promises sync.

Anatomy: local-data icon, status word, item count, last-saved time (mono).

| State | Treatment |
| --- | --- |
| default | Thin strip on paper, local-data icon, muted text, mono count. |
| hover | Surface darkens one step. |
| focus | Focus ring (#1f4e79) when the strip is a button to open storage details. |
| active | Pressed fill; opens the storage detail at reveal 520ms. |
| disabled | Muted; used while storage is being read. |
| loading | Muted bar over the count, settle 240ms. |
| empty | No items on this device yet. |
| error | Danger text: Could not read local storage on this device. |
| success | Success tick; Saved on this device. |
| selected | Not applicable to the strip. |
| offline | The strip's normal state: On this device, no connection needed. Muted, not red. |

## Search Field

Finds an item by ID or handler across the local ledger. It searches only what is on this device.

Anatomy: search icon, input, clear button, result count (mono).

| State | Treatment |
| --- | --- |
| default | Input on surface, search icon at left, line border, ink text. |
| hover | Border darkens one step. |
| focus | 2px focus ring (#1f4e79); the search moment runs at reveal 520ms. |
| active | Pressed clear button; results re-flow at ledger 360ms. |
| disabled | Muted, non-editable. |
| loading | Muted bar over the result count, settle 240ms. |
| empty | Placeholder Search item ID or handler; no results yet. |
| error | Danger text: Search could not run on this device. |
| success | Success count: N items found on this device. |
| selected | Not applicable to the field; a result row owns selection. |
| offline | Local-data note: Searching this device only. |

## Export Action

Writes the ledger out as a file from the device. It is a handoff, not a sync, the data leaves only when the user chooses.

Anatomy: export icon, label, format note (mono), handoff progress mark.

| State | Treatment |
| --- | --- |
| default | Button on surface, export icon, ink label, line border, 44px target. |
| hover | Surface darkens one step; border darkens. |
| focus | 2px focus ring (#1f4e79). |
| active | Pressed fill; the export moment runs at handoff 720ms. |
| disabled | Muted, non-clickable; used when the ledger is empty. |
| loading | Handoff progress mark animates at handoff 720ms; label Writing file. |
| empty | Disabled with note: Nothing to export yet. |
| error | Danger text: Export failed on this device. |
| success | Success tick; File written from this device. |
| selected | Not applicable to an action. |
| offline | Local-data note: Export works offline. |

## New Entry Button

Opens a fresh evidence tag to record the next item. It is the primary action that starts the core job.

Anatomy: new-entry icon, label, accent rule.

| State | Treatment |
| --- | --- |
| default | Accent fill (#a6430f) with accentInk text, new-entry icon, 44px target, the one sharp accent. |
| hover | Accent darkens one step; no shadow. |
| focus | 2px focus ring (#1f4e79) offset from the accent fill. |
| active | Pressed fill; the new tag reveals at reveal 520ms. |
| disabled | Muted fill, muted text; used while a save is in flight. |
| loading | Muted bar over the label, settle 240ms. |
| empty | Not applicable to a button. |
| error | Danger text beside it: Could not open a new entry. |
| success | Success tick; New entry ready. |
| selected | Not applicable to a button. |
| offline | Local-data note: Works on this device. |

## Ledger Action Menu

The per-item actions on a custody row: add a handoff, mark a break, or export that item. It keeps the ledger's verbs close to the row.

Anatomy: menu trigger (custody-chain icon), action list, action icons, menu label.

| State | Treatment |
| --- | --- |
| default | Quiet trigger on the row, custody-chain icon, line border, 44px target. |
| hover | Surface darkens one step. |
| focus | 2px focus ring (#1f4e79) on trigger and on the focused action. |
| active | Pressed trigger; the menu opens at reveal 520ms. |
| disabled | Muted, non-clickable; used on a locked row. |
| loading | Muted bar over an action while it runs, settle 240ms. |
| empty | Not applicable; the menu always has at least one action. |
| error | Danger text: That action could not be recorded. |
| success | Success tick; Recorded on this device. |
| selected | Selected action shows an accent tick + surface fill. |
| offline | Local-data note: Actions recorded on this device. |

## Chain-of-Custody Line

The visual chain connecting a tag to its custody rows, the line that shows the item's path and where it is continuous or broken.

Anatomy: line spine, node markers, break marker, item-id reference.

| State | Treatment |
| --- | --- |
| default | Quiet line spine on paper, node markers in line colour, mono item-id at the head. |
| hover | Spine darkens one step; the hovered node gains a ring. |
| focus | Focus ring (#1f4e79) on the focused node for keyboard users. |
| active | Pressed node; a custody add draws in at ledger 360ms. |
| disabled | Muted spine; used for a chain that is closed. |
| loading | Muted spine with two muted nodes, settle 240ms. |
| empty | Single node, no spine: No handoffs yet. |
| error | Danger break marker: Custody break, the chain is not continuous. |
| success | Success node; Chain is continuous. |
| selected | Accent node + accent spine segment for the open item. |
| offline | Local-data note: Chain stored on this device. |

## Status

Every status is a word, an icon and a colour, never colour alone.

| Status | Word | Icon | Colour role |
| --- | --- | --- | --- |
| Logged | Logged | `timestamp` | `--color-success` |
| Custody break | Custody break | `custody-chain` | `--color-danger` |
| On this device | On this device | `local-data` | `--color-muted` |
| New entry | New entry | `new-entry` | `--color-accent` |
| Saved | Saved | `local-data` | `--color-success` |
| Needs review | Needs review | `item-id` | `--color-warning` |
