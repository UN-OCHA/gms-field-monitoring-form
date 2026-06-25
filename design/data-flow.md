# Data flow

## Single location

```mermaid
flowchart LR
  A["Load template"] --> B["Fill form in<br/>guided steps"]
  B -->|autosave| C[("Location in<br/>IndexedDB")]
  B --> D["Generate"]
  D --> E["Final .xlsx<br/>saved to the report"]
  E --> F["Review in Excel and<br/>upload to OneGMS"]
```

## Multiple locations

Different team members fill different locations, optionally on different devices, then one person consolidates.

```mermaid
flowchart LR
  subgraph Per location
    L1["Location A"]
    L2["Location B"]
    L3["Location C"]
  end
  L1 -->|export or import field pack| M["Merge by<br/>location id"]
  L2 --> M
  L3 --> M
  M --> R["Consolidate: add numbers,<br/>combine text, set scores"]
  R --> RV["Editable review"]
  RV --> G["One final .xlsx"]
  G --> U["Review in Excel<br/>and upload"]
```

Aggregation is computed on demand from the locations; the per-location data is never overwritten, and review edits are kept as an override on the project.

## Filling the Excel

The app changes only the cells you fill; everything else in the template is preserved.

```mermaid
sequenceDiagram
  participant U as User
  participant App
  participant Tpl as Template in memory
  U->>App: Generate
  App->>App: collect changed answers
  App->>Tpl: write answers into the GMS named cells
  App->>Tpl: set recalculate on open
  App->>U: download timestamped .xlsx and save to records
```

See also: [data model](data-model.md), [deployment](deployment.md).
