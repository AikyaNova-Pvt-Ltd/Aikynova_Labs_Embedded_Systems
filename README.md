# AikyaNova Labs Embedded Systems - ESP32 QC Testing

This repository provides AikyaNova Lab’s standardized Quality Control (QC) test firmware for ESP32 development boards. These tests are used internally by AikyaNova Labs during hardware validation and incoming quality control (IQC), and are also shared with customers so they can independently verify the ESP32 hardware they receive.

The QC process is divided into Phase One (Physical) and Phase Two (Functional/Firmware).

## What's Included

- `Blink_LED`: LED and basic GPIO checks.
- `ESP32_QC_WIFI_AP`: Wi-Fi Access Point mode test.
- `ESP32_QC_WIFI_STA`: Wi-Fi Station mode test.
- `ESP32_QC_Bluetooth_Android`: Bluetooth validation by Android pairing.
- `ESP32_QC_Bluetooth_IOS`: Bluetooth validation by iOS pairing.

## QC Phases Overview
  ### Phase 1: Physical and Power Checks
  - Board condition and enclosure inspection
  - USB port connectivity
  - Power-on LED behavior
  - GPIO pins validation
  - Button click test

  ### Phase 2: Functional & Connectivity Checks
  -Wi-Fi (Access Point & Station mode)
  -Bluetooth (Classic / BLE) testing using mobile devices

  To run the firmware tests (Phase Two), you must set up your software environment. We recommend the Arduino IDE due to its ease of use.

## Setting up the Arduino IDE

1. Install Arduino IDE
   - Download and install the latest Arduino IDE for your OS (Windows, macOS or Linux) from:
   https://www.arduino.cc/en/software
2. Add ESP32 Board Support
   - Open Arduino IDE and go to File > Preferences.
   - In the "Additional Boards Manager URLs" field, paste the following link:
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
3. Install ESP32 Board Support
   - Go to Tools > Board > Boards Manager.
   - Search for "esp32".
   - Install the "esp32 by Espressif Systems" package
4. Select Board & Port
   - Board: Go to Tools > Board > ESP Arduino > ESP32 Dev Module
   - Port: Go to Tools > Port and select the COM/USB port where ESP32 is connected
   - Upload Speed: 921600 (recommended) or 115200
   
## USB Driver Installation
If your computer does not recognize the board (no COM port appears), you likely need to install the USB-to-UART bridge driver.
CP210x Driver: Download from Silicon Labs - https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers (Common for DevKit V1/DOIT boards).
Tip: If you are unsure which chip your board uses, look at the small square black chip near the USB port. The text on it will usually say CP2102 or CP2104.
   

## Prerequisites

- Arduino IDE installed and configured.
- USB drivers for your ESP32 board.
- A supported ESP32 development board connected via USB.

## Quick Start

1. Choose the QC test folder you want to run.
2. Build and flash using ESP-IDF:

```bash
idf.py set-target esp32
idf.py build
idf.py flash monitor
```

3. Follow any on-screen prompts in the serial monitor.

## QC Workflow (Suggested)

1. Power-on and verify serial output.
2. Run `Blink_LED` to validate GPIO and basic firmware loading.
3. Run Wi-Fi AP/STA tests to verify radio and antenna performance.
4. Run Bluetooth tests on both Android and iOS if applicable.
5. Record pass/fail results per board.

## Notes

- These tests are designed for manufacturing QC, not production firmware.
- Adjust GPIO pins and credentials as required for your specific hardware.

## Brand and License

All materials are under the AikyaNova™ brand and are licensed for
non-commercial use only. See `LICENSE` for details.
