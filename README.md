# Garuda - Smart Ambulance Traffic Clearance System

> **Status: Concept / prototype firmware.** Tested on the bench logic level; not deployed on real roads.

## Overview
An IoT concept that detects an approaching ambulance and activates roadside sirens ahead of time so traffic can clear.

## How it works
1. **Ambulance node** (ESP32 + LoRa) broadcasts an emergency beacon.
2. **Roadside node** (ESP32 + LoRa + HC-12) receives it, turns on the siren, and relays the alert to the next node over HC-12.
3. The siren turns off 5 s after the last beacon.

## Hardware
ESP32 x2+, LoRa SX1278 (433 MHz) x2+, HC-12 per roadside node, buzzer/siren, slide switch.

## Pin Map (ESP32)
| Signal | Pin |
|---|---|
| LoRa SS / RST / DIO0 | 5 / 14 / 26 |
| LoRa SCK / MISO / MOSI | 18 / 19 / 23 (default SPI) |
| Siren | 25 |
| HC-12 RX / TX | 16 / 17 |
| Emergency switch | 4 |

## How to Run
1. Install the Arduino IDE with ESP32 board support and the `LoRa` library (Sandeep Mistry).
2. Flash `ambulance_node/ambulance_node.ino` to the ambulance ESP32.
3. Flash `roadside_node/roadside_node.ino` to each roadside ESP32.
4. Turn the switch ON on the ambulance node and watch the siren.

## Future Improvements
- GPS-based distance filtering, direction detection
- Signal-strength (RSSI) based proximity
- Traffic-light integration

## Author
Beeravelli Srivasthav
