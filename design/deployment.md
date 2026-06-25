# Deployment

```mermaid
flowchart LR
  Maint["Maintainer"] -->|git push main| Repo["GitHub repo:<br/>UN-OCHA /<br/>gms-field-monitoring-form"]
  Repo -->|Pages build| Pages["GitHub Pages<br/>over HTTPS"]
  Pages -->|first visit| Device["Field device:<br/>browser or installed app"]
  Device -->|user uploads Excel| GMS[("OneGMS")]
  Offline["Works offline after<br/>the first visit"] -.-> Device
```

- Hosted on GitHub Pages; pushing to `main` redeploys.
- The first visit must be online; after that the app runs offline and can be installed to the home screen.
- All data stays on the device. The only things that cross the network are loading the app and the user's own upload to OneGMS.

See also: [architecture](architecture.md).
