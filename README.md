# IN-9 Spectrum Analyzer

> 🚧 **Early WIP — currently on hold.** The hardware design, BOM and project scaffold are
> here; the firmware is **not implemented yet** (`firmware/src/main.cpp` is a stub). Sharing
> the concept now — active development is paused.

An 8-channel audio **spectrum analyzer built on IN-9 neon bargraph tubes**, driven by an
ESP32-S3 — vintage glow meters dancing to live audio.

## Concept

- 7-band spectrum analysis (MSGEQ7) shown across **8 × IN-9** bargraph tubes
- Live, audio-reactive bar levels
- Environmental readout: CO₂ / temperature / humidity (SCD41)
- Real-time clock (DS3231) with NTP sync over WiFi
- Browser-based configuration / web UI

## Hardware

| Part | Role |
|---|---|
| ESP32-S3-DevKitC-1 (WROOM-1-N16R8) | MCU + WiFi |
| IN-9 × 8 | neon bargraph display tubes |
| MSGEQ7 | 7-band audio spectrum IC |
| MCP4728 × 2 | I²C DACs (tube drive levels) |
| MGE340 × 8 | high-voltage drive transistors |
| SCD41 | CO₂ / temperature / humidity sensor |
| DS3231 | real-time clock |
| HV PSU 12 V → ~150 V | MC34063 + IRF840 boost for the IN-9 tubes |

Assembly notes: [docs/assembly-guide.md](docs/assembly-guide.md).

## Status & roadmap

- [x] Project structure, hardware BOM, assembly notes
- [x] Web-flasher scaffold (ESP Web Tools) in `web/`
- [ ] Firmware: MSGEQ7 sampling → tube levels via MCP4728
- [ ] SCD41 / DS3231 / NTP integration
- [ ] Web UI + **WiFi provisioning** (credentials via captive portal — never hard-coded)
- [ ] Publish the browser web-flasher on GitHub Pages once the firmware is functional

## Build (firmware)

```bash
cd firmware
pio run
```

The built binaries are copied into `web/` for the [ESP Web Tools](https://esphome.github.io/esp-web-tools/)
browser flasher. The live "flash from your browser" page will go online (GitHub Pages) once
the firmware actually does something — until then it is intentionally not linked.

## License

[MIT](LICENSE) © 2026 Nikolay Mir
