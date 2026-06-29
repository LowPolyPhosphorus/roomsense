# roomsense

ESP32 + ESPHome sensor node for Home Assistant, mmWave presence detection, temperature/humidity, and sound level sensing.

> **Status: wip** most of the stuff isnt done yet


## What this is

**roomsense** is a small sensor node that sits in a room and reports into Home Assistant:

- **Presence**, via a 24ghz mmWave radar module (LD2420), unlike a basic PIR motion sensor, mmWave can detect that someone is still in the room even when they're sitting still (e.g. at a desk), because it senses micro-motion/breathing rather than just movement.
- **Sound level**, via a KY-037 sound sensor, which is useful for things like "is someone talking in this room" or basic noise logging.

It runs on plain [ESPHome](https://esphome.io) no seperate web dashboard or maintaining. ESPHome handles WiFi, OTA updates, and exposes everything as native Home Assistant entities automatically.

## Why I built this

> *wip idrk yet*


## Hardware

Full bill of materials with links and cost: [`docs/BOM.csv`](https://github.com/LowPolyPhosphorus/roomsense/blob/main/docs/BOM.csv)

**Parts:**
- 1x ESP32 dev board
- 1x DHT11 temperature/humidity sensor (not the best just what i have on hand :/)
- HLK-LD2420 24GHz mmWave presence sensor
- 1x KY-037 sound sensor
- USB-C cable (power + programming)

## Wiring

Full pin reference: [`docs/pinout.csv`](https://github.com/LowPolyPhosphorus/roomsense/blob/main/docs/pinout.csv)

Wiring diagram: 

![roomsense wiring diagram](https://raw.githubusercontent.com/LowPolyPhosphorus/roomsense/main/docs/roomsense-pinout.svg)

### Pin map (board labels, not generic GPIO numbers)
| Component | Signal | Board Pin | Notes |
|---|---|---|---|
| DHT11 | Data | D4 | |
| DHT11 | VCC | 3V3 | |
| DHT11 | GND | GND | |
| LD2420 mmWave | OT1 (presence output 1) | D13 | digital input |
| LD2420 mmWave | OT2 (presence output 2) | D18 | digital input |
| LD2420 mmWave | RX (config/commands) | D19 | optional, see note below |
| LD2420 mmWave | VCC | 3V3 | see power note below |
| LD2420 mmWave | GND | GND | |
| KY-037 | AO (analog out) | D34 | ADC1-capable pin |
| KY-037 | DO (digital out) | D35 | optional, threshold trigger |
| KY-037 | VCC | 3V3 | some KY-037 variants want 5V instead — check yours |
| KY-037 | GND | GND | |

### some notes 

- The LD2420's RX pin is optional and is only needed if sending config/sensitivity commands to the sensor. Wired to D19 instead of the boards labeled UART pins (RX2/TX2), since their actual GPIO number isn't printed on this board. Skip wiring it if you only need the basic presence via OT1/OT2

### power note (unresolved, needs testing)

All sensors currently run off the ESP32's 3V3 pin. 
todo: confirm that works and holds up under wifi load with all sensors

## Firmware (ESPHome)

> **PLACEHOLDER** not done yet

### Flashing instructions

> **PLACEHOLDER** not done yet



## Calibration

### mmWave (LD2420) sensitivity/range tuning

> **PLACEHOLDER** not done yet

### KY-037 sound threshold tuning

> **PLACEHOLDER** not done yet



## Home Assistant integration

> **PLACEHOLDER** not done yet



##  Enclosure

> **PLACEHOLDER** not done yet



## Troubleshooting

> **PLACEHOLDER** not done yet
