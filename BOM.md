# Bill of Materials (BOM) - OBD-II Diagnostic Device

This document lists all hardware components required to build the OBD-II diagnostic device.

## Core Components

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| Raspberry Pi | Single-board computer (Pi 3B+ or Pi 4 recommended) | 1 | Runs Raspbian OS; handles data processing and display |
| MicroSD Card | 16GB or larger, Class 10 | 1 | For Raspberry Pi OS and application storage |
| ELM327 Bluetooth Adapter | OBD-II to Bluetooth interface | 1 | Communicates with vehicle ECU at 38400 baud |
| Plugable USB Bluetooth 4.0 Adapter | Low Energy Micro Adapter | 1 | Connects Pi to ELM327 wirelessly (not needed if using Pi 3/4 with built-in Bluetooth) |

## Power Supply

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| Micro USB Car Charger | 5V 2A minimum (or USB-C for Pi 4) | 1 | Plugs into vehicle 12V accessory outlet |
| **OR** 2A Car Power Supply | With on/off switch | 1 | Alternative power option |

## Display & Audio

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| Aftermarket Head Unit | Car stereo with AUX input | 1 | Receives audio/video from Raspberry Pi |
| RCA Cable | Composite video/audio cable | 1 | Connects Pi to head unit |
| **OR** Small HDMI Display | 3.5" - 7" touchscreen | 1 | Alternative standalone display option |

## Cables & Connectors

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| SAE J1962 Extension Cable | OBD-II extension (optional) | 1 | For easier access to OBD-II port |
| ELM327 USB Cable | USB to OBD-II | 1 | Alternative to Bluetooth adapter; uses `/dev/ttyUSB*` |

## Optional Accessories

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| Raspberry Pi Case | Protective enclosure | 1 | Protects the Pi in vehicle environment |
| USB Keyboard | For initial setup/debugging | 1 | Can be removed after configuration |
| USB Mouse | For GUI navigation | 1 | Alternative to keyboard arrow keys |
| Heatsinks | Raspberry Pi heatsink kit | 1 | Recommended for Pi 4 in warm vehicle environments |

## Vehicle Requirements

| Requirement | Description |
|-------------|-------------|
| OBD-II Port | SAE J1962 16-pin diagnostic connector |
| Vehicle Year | 1996 or newer (US) - OBD-II compliant |
| Port Location | Within 2 feet of steering wheel |

## Minimum Configuration

For the simplest build, you need:

1. **Raspberry Pi** (with built-in Bluetooth) + MicroSD Card
2. **ELM327 Bluetooth Adapter**
3. **Micro USB Car Charger** (2A)
4. **Display** (HDMI screen or head unit with RCA)

## Wiring Diagram

```
┌─────────────────┐     Bluetooth      ┌──────────────────┐
│   Raspberry Pi  │ <----------------> │  ELM327 Adapter  │
│                 │                    │                  │
│  HDMI/RCA Out ──┼───> Display        │   OBD-II Plug ───┼───> Vehicle Port
│                 │                    │                  │
│  Micro USB ─────┼───> 12V Car Power  └──────────────────┘
└─────────────────┘
```

## Sensors Monitored (via OBD-II)

The device reads the following sensors from your vehicle's ECU:

- **Engine**: RPM, Load, Timing Advance
- **Speed**: Vehicle Speed (MPH/km/h)
- **Temperature**: Coolant Temp, Intake Air Temp
- **Fuel System**: Fuel Trim (Short/Long Term), Fuel Rail Pressure
- **Air System**: Mass Air Flow (MAF), Intake Manifold Pressure
- **Oxygen Sensors**: Bank 1 & 2, Sensors 1-4
- **Diagnostics**: Trouble Codes (DTCs), MIL Status

## Notes

- The ELM327 adapter must be paired with the Raspberry Pi's Bluetooth before use
- Serial communication runs at **38400 baud** (8N1)
- Device paths: `/dev/rfcomm0` (Bluetooth) or `/dev/ttyUSB0` (USB)
- Logs are saved to `~/pyobd-pi/log/` in CSV format
