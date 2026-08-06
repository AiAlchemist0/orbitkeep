# OrbitKeep

**Personal Relationship Keeper** — keep everyone who matters in your orbit.

OrbitKeep helps you track important people across platforms, set a contact cadence, and get nudged before connections fade. Built as a Bloome interactive widget for the Bloome AI Team Hackathon (2026).

## Features

- **Relationship orbit** — visual map of people by closeness / due status (on track · due soon · overdue · no contact yet)
- **Interactive person cards** — tap a bubble for status, last contact, next due, platforms, quick log
- **Cadence engine** — `next_due = last_contact + frequency_days` with local calendar math
- **Demo + Start Your Orbit** — sample data for demos; clean slate for personal use
- **Two-path start** — Manual tracking now; Friend Agent path as future extension
- **Science page** — Hall friendship-hours research + Dunbar layers, mapped to product metrics
- **Light / dark theme** — light by default, corner toggle

## Quick start

Open the widget HTML in a browser (or serve statically):

```bash
# from this directory
python3 -m http.server 8080
# open http://localhost:8080
```

> **Note:** Full Bloome features (`ResonWidget.state`, theme persistence across sessions, CDN assets) work best when running as a Bloome widget. Local open is fine for layout and logic review; state may not persist without the Bloome host.

## Project layout

```
.
├── index.html          # Full OrbitKeep widget (single-file app)
├── assets/             # Optional media (hero trailer, etc.)
├── docs/               # Product notes
└── README.md
```

## Product model (MVP)

| Entity | Fields |
|--------|--------|
| Person | name, memo, platforms[], topics[], last_contact, frequency_days, next_due, interactions[] |
| Interaction | date, notes |

**Status rules**

| Status | Rule |
|--------|------|
| Overdue | `next_due < today` |
| Due soon | within 7 days |
| On track | beyond 7 days |
| No contact yet | `last_contact` null → next due today (first-touch prompt) |

Logging an interaction uses **max-date** (never rewinds last contact).

## Stack

- Single-file HTML / CSS / JS
- [Bloome](https://bloome.im) widget runtime (`ResonWidget`)
- Bloome design system (`.bw` components)
- No backend required for MVP (local widget state)

## Credits

Built by the OrbitKeep hackathon team:

- Mira · Project Lead  
- Mike · Eng Lead  
- Iris · Designer  
- Nova · QA & Experience  
- Builder · Dev support  
- Axel · Advanced Builder  
- Leo · Marketing Video  
- Bloome Assistant · Coordination & deploy  

Product owner: **Dean Shev**

## License

MIT — see [LICENSE](./LICENSE)
