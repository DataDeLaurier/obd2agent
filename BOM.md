# Bill of Materials (BOM) - OBD-II Diagnostic Device

This document lists all hardware components required to build the OBD-II diagnostic device with advanced audio/visual diagnostics capabilities.

## Research Background

This design incorporates findings from peer-reviewed research on vehicle diagnostics:

- **Audio-based fault detection** using MFCC (Mel-Frequency Cepstral Coefficients) analysis can achieve 92%+ accuracy in identifying engine faults
- **Computer vision** enables automated dashboard warning light detection and gauge reading
- **Multi-source sensor fusion** combining OBD-II data with GPS, accelerometer, and audio/video significantly improves diagnostic accuracy

## Core Components

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| Raspberry Pi 4 Model B | 4GB or 8GB RAM recommended | 1 | Required for ML inference; handles audio/video processing |
| MicroSD Card | 64GB or larger, Class 10/U3 | 1 | Larger capacity for audio/video storage and ML models |
| ELM327 Bluetooth Adapter | OBD-II to Bluetooth interface (v1.5 or v2.1) | 1 | Communicates with vehicle ECU at 38400 baud |
| Plugable USB Bluetooth 4.0 Adapter | Low Energy Micro Adapter | 1 | Optional - Pi 4 has built-in Bluetooth |

## Power Supply

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| USB-C Car Charger | 5V 3A minimum for Pi 4 | 1 | Must provide stable power for compute-intensive tasks |
| **OR** 12V to 5V Buck Converter | 3A+ output with USB-C | 1 | More reliable than cheap car chargers |
| UPS HAT (optional) | Uninterruptible power supply | 1 | Prevents SD card corruption on power loss |

## Display & Audio Output

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| 7" HDMI Touchscreen | 1024x600 or higher resolution | 1 | Recommended for displaying diagnostic data |
| **OR** Aftermarket Head Unit | Car stereo with AUX input | 1 | Receives audio/video from Raspberry Pi |
| RCA Cable | Composite video/audio cable | 1 | For head unit connection |

## Audio Diagnostics (Research-Optimized)

Based on research showing MFCC-based sound analysis achieves 92%+ fault detection accuracy:

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| USB Condenser Microphone | 44.1kHz+ sample rate, <20dB noise floor | 1 | Required for MFCC feature extraction |
| **OR** USB Audio Interface | 24-bit/48kHz ADC (e.g., Focusrite Scarlett Solo) | 1 | Professional-grade for best results |
| Lavalier/Clip Microphone | 3.5mm with extension cable | 1 | For USB audio interface; position near engine |
| Windscreen/Pop Filter | Foam cover for microphone | 1 | Reduces wind noise at speed |
| Microphone Extension Cable | 3-5m shielded audio cable | 1 | Route mic to engine bay or wheel wells |

### Audio Specifications (Research-Based)
- **Sample Rate**: Minimum 44.1kHz (48kHz recommended) for accurate frequency analysis
- **Bit Depth**: 16-bit minimum, 24-bit preferred
- **Frequency Response**: 20Hz - 20kHz to capture full engine sound spectrum
- **SNR**: >60dB for clean recordings in noisy vehicle environment

### Detectable Faults via Sound Analysis
- Engine knocking/pinging (detonation)
- Valve train noise (lifter tick, rocker arm clatter)
- Belt squealing (serpentine, timing)
- Bearing wear (alternator, water pump, wheel bearings)
- Exhaust leaks and muffler issues
- Brake pad wear indicators
- CV joint clicking
- Suspension component wear

## Visual Diagnostics (Computer Vision)

Based on research in automated dashboard warning light detection:

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| Raspberry Pi Camera Module 3 | 12MP, HDR, low-light capable | 1 | Best for dashboard in varying light conditions |
| **OR** Pi HQ Camera | 12.3MP with C/CS mount | 1 | Higher quality; requires separate lens |
| **OR** USB Webcam | 1080p, low-light capable (e.g., Logitech C920) | 1 | Wider compatibility; good low-light performance |
| Wide-Angle Lens | 120°+ FOV (for HQ Camera) | 1 | Captures full dashboard in tight spaces |
| Camera Gooseneck Mount | Flexible 30-50cm arm | 1 | Adjustable positioning for dashboard view |
| IR LED Ring (optional) | 850nm infrared illuminator | 1 | For night driving dashboard visibility |
| CSI Ribbon Cable (extended) | 1m or 2m length | 1 | Flexible camera positioning |

### Camera Specifications (Research-Based)
- **Resolution**: Minimum 1080p for reading small warning light icons
- **Low-Light Performance**: Essential for nighttime dashboard monitoring
- **Frame Rate**: 30fps minimum for capturing intermittent warning lights
- **Dynamic Range**: HDR preferred to handle bright sunlight and dark cabin

### Detectable via Computer Vision
- Dashboard warning light states (on/off/flashing)
- Gauge readings (tachometer, speedometer, fuel, temperature)
- Check engine light patterns
- ABS, airbag, battery, oil pressure indicators
- Correlation of visual gauge data with OBD-II readings

## Sensor Fusion (Enhanced Diagnostics)

Research shows multi-source data fusion significantly improves diagnostic accuracy:

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| GPS Module | u-blox NEO-6M or NEO-M8N | 1 | Vehicle location, speed verification, route logging |
| IMU (Accelerometer/Gyroscope) | MPU-6050 or MPU-9250 | 1 | Detect vibrations, vehicle dynamics, road conditions |
| GPS + IMU HAT | Combines both sensors | 1 | Cleaner installation than separate modules |
| OBD-II Splitter Cable | Y-adapter for OBD port | 1 | Share port with other devices if needed |

### Sensor Fusion Benefits
- **GPS + OBD-II**: Verify speedometer accuracy, log routes with engine data
- **IMU + Audio**: Correlate vibrations with sounds for bearing/suspension diagnosis
- **All sensors**: Comprehensive vehicle health profile with location context

## Cables & Connectors

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| SAE J1962 Extension Cable | 1m OBD-II extension | 1 | For easier access to OBD-II port |
| USB Hub (powered) | 4+ port, 5V/3A powered | 1 | Required for multiple USB peripherals |
| USB Extension Cables | 1-2m lengths | 2-3 | Route microphone and other USB devices |
| Cable Management Kit | Velcro ties, cable clips | 1 | Clean installation in vehicle |

## Optional Accessories

| Component | Description | Qty | Notes |
|-----------|-------------|-----|-------|
| Raspberry Pi Case | With cooling fan | 1 | Essential for Pi 4 thermal management |
| Heatsinks | Copper heatsink kit | 1 | Additional cooling for ML workloads |
| USB Keyboard/Mouse | Wireless combo | 1 | For initial setup and debugging |
| Real-Time Clock (RTC) | DS3231 module | 1 | Accurate timestamps without network |
| External SSD | USB 3.0, 256GB+ | 1 | Faster storage for large recordings |

## Vehicle Requirements

| Requirement | Description |
|-------------|-------------|
| OBD-II Port | SAE J1962 16-pin diagnostic connector |
| Vehicle Year | 1996 or newer (US) - OBD-II compliant |
| Port Location | Within 2 feet of steering wheel |

## Configuration Tiers

### Tier 1: Basic OBD-II Diagnostics
Minimum build for reading vehicle codes and sensor data:
1. Raspberry Pi 4 (2GB) + 32GB MicroSD
2. ELM327 Bluetooth Adapter
3. USB-C Car Charger (3A)
4. Small HDMI Display

### Tier 2: Audio Diagnostics
Add sound-based fault detection:
1. All Tier 1 components
2. USB Condenser Microphone (44.1kHz+)
3. Microphone windscreen
4. 64GB MicroSD (for recordings)

### Tier 3: Visual Diagnostics
Add computer vision for dashboard monitoring:
1. All Tier 2 components
2. Pi Camera Module 3 or USB Webcam
3. Gooseneck camera mount
4. Extended CSI cable (if using Pi Camera)

### Tier 4: Full Sensor Fusion (Recommended)
Complete diagnostic system with research-backed accuracy:
1. All Tier 3 components
2. GPS Module (u-blox)
3. IMU Sensor (MPU-6050/9250)
4. USB Audio Interface (for professional audio)
5. 128GB+ MicroSD or External SSD
6. Powered USB Hub
7. UPS HAT (for data integrity)

## Wiring Diagram

```
                                              ┌──────────────────┐
                          Bluetooth           │  ELM327 Adapter  │
                      <-------------------->  │   OBD-II Plug ───┼───> Vehicle Port
                      │                       └──────────────────┘
┌─────────────────────┴─────┐
│       Raspberry Pi 4      │
│                           │                 ┌──────────────────┐
│  CSI Port ────────────────┼────────────────>│  Pi Camera       │───> Dashboard View
│                           │                 └──────────────────┘
│  GPIO (I2C) ──────────────┼────────────────> GPS + IMU Module
│                           │
│         ┌─────────────────┼────────────────> Powered USB Hub
│  USB ───┤                 │                       │
│         └─────────────────┤                       ├──> USB Microphone ───> Engine Bay
│                           │                       ├──> USB Webcam (alt)
│                           │                       └──> External SSD
│                           │
│  HDMI ────────────────────┼────────────────> 7" Touchscreen Display
│                           │
│  USB-C Power ─────────────┼────────────────> 12V Car Power (via buck converter)
│                           │
│  UPS HAT ─────────────────┼────────────────> Battery Backup
└───────────────────────────┘
```

## Software Requirements

For full functionality, the following software components are recommended:

| Software | Purpose |
|----------|---------|
| Python 3.9+ | Core application runtime |
| pyOBD / python-OBD | OBD-II communication |
| librosa / scipy | Audio analysis (MFCC extraction) |
| OpenCV | Computer vision for dashboard detection |
| TensorFlow Lite | ML inference for fault classification |
| gpsd | GPS data processing |

## Sensors Monitored (via OBD-II)

The device reads the following sensors from your vehicle's ECU:

- **Engine**: RPM, Load, Timing Advance
- **Speed**: Vehicle Speed (MPH/km/h)
- **Temperature**: Coolant Temp, Intake Air Temp
- **Fuel System**: Fuel Trim (Short/Long Term), Fuel Rail Pressure
- **Air System**: Mass Air Flow (MAF), Intake Manifold Pressure
- **Oxygen Sensors**: Bank 1 & 2, Sensors 1-4
- **Diagnostics**: Trouble Codes (DTCs), MIL Status

## Research References

This design is informed by the following peer-reviewed research:

1. **Engine Fault Detection by Sound Analysis and Machine Learning** (2024) - MDPI Applied Sciences
   - Demonstrates 92%+ accuracy using MFCC features with ELM classifier
   - https://www.mdpi.com/2076-3417/14/15/6532

2. **Intelligent Sound-Based Early Fault Detection System for Vehicles** (2023) - Tech Science Press
   - Validates smartphone/microphone-based engine fault detection
   - https://www.techscience.com/csse/v46n3/52169/html

3. **OBD-II-Based Machine Learning Applications Review** (2025) - MDPI Sensors
   - Comprehensive review of ML applications with OBD-II data
   - https://www.mdpi.com/1424-8220/25/13/4057

4. **Diagnostics Vehicle's Condition Using OBD-II and Raspberry Pi** - ResearchGate
   - Foundational study on Pi-based OBD-II diagnostics
   - https://www.researchgate.net/publication/323803679

5. **Computer Vision Application in Automobile Error Detection** - IEEE Xplore
   - Dashboard image analysis for fault detection
   - https://ieeexplore.ieee.org/document/9791543/

6. **TrackSide Pi** - Cornell ECE
   - Reference implementation combining OBD-II, camera, GPS, and accelerometer
   - https://courses.ece.cornell.edu/ece5990/ECE5725_Spring2020_Projects/

## Notes

- The ELM327 adapter must be paired with the Raspberry Pi's Bluetooth before use
- Serial communication runs at **38400 baud** (8N1)
- Device paths: `/dev/rfcomm0` (Bluetooth) or `/dev/ttyUSB0` (USB)
- Logs are saved to `~/pyobd-pi/log/` in CSV format
- For ML inference, Pi 4 with 4GB+ RAM is strongly recommended
- Audio recordings should be in WAV format (uncompressed) for MFCC analysis
