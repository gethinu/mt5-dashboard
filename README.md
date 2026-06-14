# mt5-dashboard

Public, mobile-friendly mirror of the **MT5 Edge Factory** live dashboard.

The source of truth is the private repo
[`gethinu/mt5_Bundle-of-edges`](https://github.com/gethinu/mt5_Bundle-of-edges)
which builds `docs/factory_dashboard.html` daily (and on demand). A
sync script (`scripts/sync_dashboard_to_public.ps1` in the private repo)
copies that single HTML file here as `index.html` and pushes.

## Live dashboard

https://gethinu.github.io/mt5-dashboard/

(Open on your phone. Add to home screen for a one-tap app-like
experience. Auto-refreshes every 60 seconds.)

## Auto-update mechanism

1. Private repo runs `scripts/build_factory_dashboard.py` (Cloud Routine
   at 08:00 JST + Cowork Scheduled task at 30-min ticks).
2. Build script calls the optional post-hook
   `scripts/sync_dashboard_to_public.ps1` if present.
3. The hook copies `docs/factory_dashboard.html` -> `index.html` here,
   commits, and pushes.
4. GitHub Pages serves the new `index.html` within ~30s.

## Why a separate repo?

The main strategy repo is **private** — it contains discovery scans, R2
results, and kill memos that shouldn't be public. This mirror exposes
**only** the rendered dashboard.

## License

Mirror of dashboard renderings. Source data and code remain private.
