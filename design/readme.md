# GMS Field Monitor: design

A short technical overview, split into sections. For how to use the app, see the [main readme](../README.md).

GMS Field Monitor is a browser app that fills the OneGMS Field Site Monitoring (FSM) Excel template in the field and regenerates the file for upload. It runs entirely on the device: no server, works offline, and stores reports locally.

## Sections

- [Architecture](architecture.md): the parts of the app and how they fit together.
- [Data model](data-model.md): what is stored on the device, as an entity diagram.
- [Data flow](data-flow.md): how data moves for single and multiple locations, and how the Excel is filled.
- [Deployment](deployment.md): how the app is hosted and reaches devices.
