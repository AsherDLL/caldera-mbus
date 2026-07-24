# M-Bus Plugin for Caldera

The M-Bus plugin provides [Caldera](https://github.com/mitre/caldera) with
adversary-emulation abilities for **Meter-Bus (M-Bus, EN 13757)**, the protocol used
to read utility meters, typically reached over a **TCP/M-Bus gateway** (port 5000).

Abilities are mapped to [ATT&CK for ICS](https://attack.mitre.org/matrices/ics/) and
driven by a generic command-line client (`mbus_cli`), so they work against any M-Bus
meter or gateway, the address and port are supplied as facts.

## Abilities

| Ability | Tactic | Technique |
|---|---|---|
| M-Bus - Ping Address | Discovery | T0846 Remote System Discovery |
| M-Bus - Scan Bus | Discovery | T0846 Remote System Discovery |
| M-Bus - Read Meter | Collection | T0801 Monitor Process State |
| M-Bus - Application Reset | Inhibit Response Function | T0816 Device Restart/Shutdown |
| M-Bus - Broadcast Reset (DoS) | Inhibit Response Function | T0814 Denial of Service |

See [`docs/mbus.md`](docs/mbus.md) for commands and the fact reference.

## Installation

1. Clone into Caldera's `plugins/` directory as `mbus`:

   ```
   git clone https://github.com/AsherDLL/caldera-mbus plugins/mbus
   ```

   The payload binaries ship in `payloads/` (`mbus_cli`, and `mbus_cli.exe` /
   `mbus_cli_darwin` from the release CI).

2. Enable the plugin in `conf/local.yml`:

   ```yaml
   plugins:
     - mbus
   ```

3. Restart Caldera. Abilities appear under the tactics above, with an
   **M-Bus Sample Facts** source to seed a fact source.

## Payload

`mbus_cli` builds M-Bus frames directly and decodes reads with
[pyMeterBus](https://github.com/ganehag/pyMeterBus) (BSD-3-Clause). Source and build
tooling are in [`src/`](src/README.md); the plugin is Apache-2.0.

## Tests

```
pip install -r src/requirements.txt pytest
PYTHONPATH=src python -m pytest tests -q
```

## License

Apache-2.0. See [`LICENSE`](LICENSE) and [`NOTICE.md`](NOTICE.md).

## Authors

- Asher Davila ([AsherDLL](https://github.com/AsherDLL))
- Malav Vyas ([MalavVyas](https://github.com/MalavVyas))
