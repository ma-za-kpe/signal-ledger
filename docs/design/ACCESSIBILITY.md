# Signal Ledger accessibility (U6)

- Targets are at least 44px in both directions (`--target-min`).
- Focus: Always-visible focus ring in #1f4e79, 2px offset, on every interactive element including Custody Ledger Rows, the New Entry Button, Search Field, Item ID Field, Timestamp Stamp, Ledger Action Menu, Ch
- Live regions: Polite live region announces local-storage status changes, save success or failure, and item-count changes; the error state is announced via an assertive live region.
- All interactive targets are at least 44px, including ledger row actions and the stamp control.
- Focus is always visible using #1f4e79 and never removed; focus order follows the visual ledger order.
- The Local-Storage Status Strip is a polite live region so status changes are announced without interrupting.
- Save success and failure are announced; failure is assertive so it is not missed.
- Item-count changes in the custody ledger are announced politely.
- Under reduced motion, nothing moves and nothing is hidden; all states are fully visible.
- The evidence item hero and ledger rows use sufficient contrast against the paper and surface palette.
- No accounts, no sync, no network: all data and status are local, and the UI says so plainly.
- axe (WCAG 2.1 AA) is clean on every page, at phone and desktop widths, in both themes; the frozen browser check enforces it.
- 30 of 46 measured pairs are fit for body text; the rest are listed in brand/BRAND.md with their limits.
