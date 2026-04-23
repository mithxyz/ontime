# MITH custom views

Self-contained HTML views that run on top of Ontime's
[custom views](https://docs.getontime.no/features/custom-views/) feature.

Each view is a single `index.html` (inline CSS + JS, no external resources)
that subscribes to Ontime's runtime data over `wss://<host>/ws` and falls
back to `GET /api/poll` on boot.

## Views

| slug       | target                                  | notes                                                         |
| ---------- | --------------------------------------- | ------------------------------------------------------------- |
| `pi-timer` | Raspberry Pi Zero @ 1424 × 280 ultrawide | Strip layout — clock ∙ big timer ∙ now/next ∙ progress bar.   |

### URL params (shared)

- `?name=<str>` — optional venue label under the clock
- `?clock=false` — hide the clock panel
- `?progress=false` — hide the progress bar
- `?next=false` — hide the Next card

## Deploying to an Ontime server

Drop a view's directory into the Ontime data volume:

```
<ontime-data>/external/<slug>/index.html
```

…then open `https://<ontime-host>/external/<slug>/`.

On the MITH VPS that's `/root/ontime/data/external/<slug>/`, served at
`https://ontime.mith.studio/external/<slug>/`.
