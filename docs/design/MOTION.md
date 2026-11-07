# Signal Ledger motion (U3)

Motion explains change; it never decorates. One orchestrated moment greets the visitor, every other motion answers something they did.

| Token | Duration |
| --- | --- |
| `--motion-stamp` | 180ms |
| `--motion-settle` | 240ms |
| `--motion-ledger` | 360ms |
| `--motion-reveal` | 520ms |
| `--motion-handoff` | 720ms |

| Token | Curve |
| --- | --- |
| `--ease-press` | cubic-bezier(0.2, 0, 0.8, 1) |
| `--ease-slide` | cubic-bezier(0.25, 0.1, 0.25, 1) |
| `--ease-stamp-in` | cubic-bezier(0.16, 1, 0.3, 1) |

## Moments

| Moment | Motion | Duration | Easing |
| --- | --- | --- | --- |
| load | status strip, item label stamp, custody line, and local/offline confirmation arrive in the named load sequence | `reveal` | `slide` |
| save | the custody entry settles into its stamped row with a short confirmation tick | `settle` | `press` |
| custody add | a new chain-of-custody line stamps in beneath the item label | `stamp` | `stamp-in` |
| offline change | the local/offline status strip shifts its label and pulses once to mark the change | `ledger` | `slide` |
| search | matching ledger rows reveal in place while non-matching rows dim | `reveal` | `slide` |
| export | the export control hands off to a stamped file-ready state | `handoff` | `press` |
| error | the affected field stamps a danger note and the status strip flags the failed write | `stamp` | `stamp-in` |

## The load moment

In order, 90ms apart (`--reveal-step`, `components/kit/Reveal.tsx`): status strip → item label stamp → custody line → local/offline confirmation.

- Reduced motion: Under reduced motion, every load step and state change renders its final state instantly with no movement or hidden content.
- Without JavaScript: With JavaScript disabled, the page shows a static custody ledger with its stamped item label, chain-of-custody line, and local/offline status already in place.
- Bursts: When many changes arrive at once, they collapse into a single stamped revision of the custody entry rather than a cascade of separate animations.
- Focus: Focus is always a visible 2px accent outline on every interactive target, which is at least 44px in size.
