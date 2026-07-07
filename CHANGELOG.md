# Changelog

## v1.0.0

Initial release of the M-Bus plugin.

- Five abilities mapped to ATT&CK for ICS: ping address, scan bus, read meter,
  application reset, and broadcast reset (DoS).
- Generic `mbus_cli` payload (hand-built M-Bus framing + pyMeterBus decoding) with
  PyInstaller build + cross-platform CI, and unit tests against a local M-Bus server.
- `M-Bus Sample Facts` source and a payload registry.
- A GUI panel and a read output parser that produces `mbus.record.*` facts.
- Fieldmanual documentation in `docs/mbus.md`.
