# Architecture

Everything runs in the browser on the device.

```mermaid
flowchart TB
  Template["GMS template .xlsx"]
  subgraph Browser on the device
    UI["UI: records, form,<br/>locations, review"]
    Engine["Engine: read template,<br/>fill cells, build .xlsx"]
    Store[("IndexedDB:<br/>reports stored locally")]
    SW["Service worker:<br/>offline cache, auto-update"]
    UI --> Engine
    UI --> Store
    Store --> UI
  end
  Template -->|load| Engine
  Engine -->|generate| Excel["Final .xlsx"]
  Excel --> Check["User checks and<br/>verifies in Excel"]
  Check -->|upload| GMS[("OneGMS")]
```

- **UI**: the records home, the step-by-step form, the project (locations) view, and the consolidation review.
- **Engine**: reads field values, dropdowns and tables from the loaded template, and writes answers back into the original file, unchanged except for the filled cells.
- **IndexedDB**: keeps every report on the device so it can be reopened without the original file.
- **Service worker**: makes the app work offline and applies updates automatically.
- Before upload, the user opens the generated file in Excel to check and verify it.

See also: [data model](data-model.md), [data flow](data-flow.md).
