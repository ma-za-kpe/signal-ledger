# Signal Ledger brand

Theme: **Custody Ledger**. The evidence locker: numbered evidence tags, the chain-of-custody ledger, incident report forms, item IDs, timestamps, and the local-storage status strip. The product is a working prototype whose data stays on this device, so the vernacular

Boldness, spent in one place: The evidence item is the hero. Every screen is built around a custody ledger entry — a stamped item label, a chain-of-custody line, and a local/offline status — with one sharp accent reserved for the

## Essence (B1)

| Tagline | Promise | Personality |
| --- | --- | --- |
| Every item logged, every hand recorded, nothing leaves this device. | Signal Ledger gives a security or analytics team a local, offline-first record of each evidence item, with the chain of custody written down so the record holds up. | precise, sober, local, accountable, plain-spoken |

| It is | It is not |
| --- | --- |
| A local, offline-first record of evidence items | Not a national-security or policy tool |
| A chain-of-custody ledger with item IDs and timestamps | Not a cloud service or a shared dashboard |
| A working prototype whose data stays on this device | Not a command centre or a live threat map |
| A tool for security and analytics teams in Canada | Not a finished product; it is a prototype |
| A custody record you can read at a glance | Not a claim about Canada's national security strategy |

The decision, with the directions rejected, is in [DECISION.md](DECISION.md).

## Colour (B4)

22 primitives and 11 semantic roles in two themes; use the roles, never a primitive directly.

| Primitive | Value |
| --- | --- |
| `paper` | #f4f1ea |
| `surface` | #fbfaf6 |
| `ink` | #1b1a17 |
| `muted` | #5c584f |
| `line` | #d8d2c4 |
| `accent` | #a6430f |
| `accent-ink` | #ffffff |
| `focus` | #1f4e79 |
| `success` | #2e6b3a |
| `warning` | #8a5a00 |
| `danger` | #a3231b |
| `paper-dark` | #16150f |
| `surface-dark` | #211f18 |
| `ink-dark` | #ede9df |
| `muted-dark` | #a6a093 |
| `line-dark` | #3a372e |
| `accent-dark` | #e8793a |
| `accent-ink-dark` | #1b1a17 |
| `focus-dark` | #8fb6de |
| `success-dark` | #7cc08a |
| `warning-dark` | #e0a94e |
| `danger-dark` | #e57a70 |

| Role | Light | Dark |
| --- | --- | --- |
| `--color-ink` | #1b1a17 | #ede9df |
| `--color-paper` | #f4f1ea | #16150f |
| `--color-surface` | #fbfaf6 | #211f18 |
| `--color-muted` | #5c584f | #a6a093 |
| `--color-line` | #d8d2c4 | #3a372e |
| `--color-accent` | #a6430f | #e8793a |
| `--color-accentInk` | #ffffff | #1b1a17 |
| `--color-focus` | #1f4e79 | #8fb6de |
| `--color-success` | #2e6b3a | #7cc08a |
| `--color-warning` | #8a5a00 | #e0a94e |
| `--color-danger` | #a3231b | #e57a70 |

Every text role on every surface is measured in `contrast.json` (WCAG 2.x), and the crew repository's tests recompute it. These pairs are not for body text:

| Pair | Contrast | Use |
| --- | --- | --- |
| light: ink on accent | 2.84:1 | never |
| light: muted on accent | 1.16:1 | never |
| light: accentInk on paper | 1.13:1 | never |
| light: accentInk on surface | 1.04:1 | never |
| light: success on accent | 1.05:1 | never |
| light: warning on accent | 1.03:1 | never |
| light: danger on accent | 1.22:1 | never |
| light: focus on accent | 1.42:1 | never |
| dark: ink on accent | 2.40:1 | never |
| dark: muted on accent | 1.12:1 | never |
| dark: accentInk on paper | 1.05:1 | never |
| dark: accentInk on surface | 1.06:1 | never |
| dark: success on accent | 1.35:1 | never |
| dark: warning on accent | 1.38:1 | never |
| dark: danger on accent | 1.02:1 | never |
| dark: focus on accent | 1.37:1 | never |

Statuses never rely on colour alone: each has a word and an icon (docs/design/COMPONENTS.md), and success, warning and danger differ in lightness, so they read in greyscale.

## Type (B5)

| Role | Face | Package | Licence |
| --- | --- | --- | --- |
| display | Bricolage Grotesque Variable | @fontsource-variable/bricolage-grotesque | SIL Open Font License 1.1 (OFL-1.1), self-hosted from the pinned @fontsource package |
| body | IBM Plex Sans Variable | @fontsource-variable/ibm-plex-sans | SIL Open Font License 1.1 (OFL-1.1), self-hosted from the pinned @fontsource package |
| mono | IBM Plex Mono | @fontsource/ibm-plex-mono | SIL Open Font License 1.1 (OFL-1.1), self-hosted from the pinned @fontsource package |

| Token | Min | Max |
| --- | --- | --- |
| `--text-xs` | 12px | 12px |
| `--text-sm` | 14px | 14px |
| `--text-base` | 16px | 16px |
| `--text-lg` | 18px | 18px |
| `--text-xl` | 22px | 22px |
| `--text-2xl` | 28px | 28px |
| `--text-3xl` | 36px | 36px |
| `--text-4xl` | 48px | 48px |

- Display (Bricolage Grotesque) is reserved for the stamped item label, the chain-of-custody heading, and page titles; it is never used for running body copy.
- Body (IBM Plex Sans) carries all reading text at base 16px or larger, with a line height of at least 1.5.
- Mono (IBM Plex Mono) is used only for item IDs, timestamps, and the local/offline status strip, so machine-readable values are visually distinct from prose.
- The stamped item label uses the 3xl or 4xl step in a heavy display weight; supporting fields drop to base or sm.
- Contrast in weight and size is deliberate: a heavy display label sits against a light-weight body field, never two similar weights stacked.
- No face is used below the xs step, and no text role is set in a colour that fails its theme's contrast floor.

## Logo (B3)

A stamped evidence tag: a rounded rectangle tag body in ink, a small punch hole near the top, and a single bold custody stripe in the accent colour running across the lower third. The mark reads as a physical tag you would clip to an item,

The mark sits on a 64-unit grid. Keep clear space of a quarter of its width on every side; never show it under 16px (favicon) or the lockup under 120px wide.

| File | Use |
| --- | --- |
| `logo/mark.svg` | the mark on paper; the favicon |
| `logo/mark-on-dark.svg` | the mark on the ink background |
| `logo/mark-mono.svg` | one colour: stamps, embossing, small sizes |
| `logo/mark-state-success.svg` | the mark in the success state |
| `logo/wordmark.svg` | the name alone |
| `logo/lockup.svg`, `logo/lockup-on-dark.svg` | mark and name together |

Don't:

- Do not add a crest, shield, flag, or any national-security emblem to the mark.
- Do not set the mark on a purple-to-blue or any other gradient background.
- Do not recolor the custody stripe to anything other than the accent primitive.
- Do not add text, letters, or a monogram inside the tag.
- Do not scale the mark below 16px, where the punch hole and stripe stop reading.
- Do not place the mark on a busy or photographic background; it needs paper or surface.

## Iconography

Solid icons on a 24 grid, 2px strokes, rounded corners, in `icons/ui/`: `new-entry`, `custody-chain`, `local-data`, `timestamp`, `item-id`, `search`, `export`.

## Pattern (B8)

`patterns/ledger-rule.svg` tiles seamlessly. A faint horizontal ledger rule, one line per tile, in the line primitive. Use it only as a quiet background texture for margins, the local/offline status strip, and empty states. Keep it below body-,

## Voice (B6)

1. **Name the item and the action in one short sentence.** — Item 0042 recorded. Chain of custody updated.
2. **State the local status plainly; do not soften it.** — Stored on this device. Not synced.
3. **Use the item ID and timestamp in every record line.** — 0042 · 2025-06-11 14:02 · logged by you
4. **Say what the user can do next, not what the product is.** — Add the next hand to the chain.
5. **Keep numbers and claims to what the brief supports.** — This is a working prototype. Its data stays on this device.
6. **Describe the record, not the threat.** — Three items in this ledger. Two have a full chain.
7. **Use the past tense for what is done and the present for what is here.** — Item 0041 sealed. Item 0042 open.
8. **Do not promise what the prototype does not do.** — No cloud. No sync. The record is here.

| Use | Avoid |
| --- | --- |
| record | seamless |
| log | unlock |
| item | empower |
| chain of custody | elevate |
| local | next-gen |
| on this device | cutting-edge |
| sealed | game-changer |
| open | leverage |

Banned words: “seamless”, “revolutionize”, “revolutionise”, “unlock”, “empower”, “next-gen”, “cutting-edge”, “game-changer”, “game changing”, “elevate”, “synergy”, “supercharge”.

Copy for every product state:

| State | Copy |
| --- | --- |
| empty | No items in this ledger yet. Record the first one. |
| loading | Reading the ledger… |
| error | The item could not be recorded. Nothing was written. Try again. |
| success | Item 0042 recorded. Chain of custody updated. Stored on this device. |
| offline | Offline. The record is on this device and will not sync. |

## Not this product (D21)

- A dark navy dashboard with cyan 'SOC' styling and live threat maps
- Government or national-security emblems, crests, or flag motifs
- A centred hero with a purple-to-blue gradient
- Three identical feature cards with emoji icons
- Inter or Roboto with no type contrast
- Glassmorphism panels on a blurred blob background
- Stock 'Get started' and 'Learn more' buttons side by side
- Stock photos of servers, lock icons, or a person at a desk with a laptop
- a centred hero with a purple-to-blue gradient
- three identical feature cards with emoji icons
- Inter or Roboto with no type contrast
- glassmorphism panels on a blurred blob background
- stock 'Get started' and 'Learn more' buttons side by side

Never in copy: “seamless”, “revolutionize”, “revolutionise”, “unlock”, “empower”, “next-gen”, “cutting-edge”, “game-changer”, “game changing”, “elevate”, “synergy”, “supercharge”, “leverage”, “world-class”, “effortless”, “unleash”, “harness the power”, “in today's”, “look no further”, “one-stop”.
