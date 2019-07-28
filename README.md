# Biogotchi!
Biohacking Village 2019 - Biohacking Village Tamagotchi Badge, AKA "Biogotchi"

The Biogotchi is modeled after the original Bandai "Tamagotchi", but centered around raising the realistic organisms of everday microscopic life. 

[Wikipedia on the original Tamagotchi](https://en.wikipedia.org/wiki/Tamagotchi)

**BioDev**

The Biogotchi badge is flashed with the associated game firmware, but also comes with a USB to UART interface via the microUSB port that interfaces with the onboard Espressif ESP32 WROOM (the brains), making it a fully reprogrammable WiFi and Bluetooth dev board. 

**Rechargeable**

The Biogotchi schematic is modeled after the open source Adafruit ESP32 Feather (which is why we've sourced our batteries and other components from Adafruit, in appreciation!), and include the same LiPo charging capabilities, which means you can recharge your battery by plugging your Biogotchi into a standard USB port. 


**Color & Touch Display**

The onboard display is wired for using both the resistive touch panel and the 1.8" TFT breakout designed for the ILI9163 controller. 

Wiring for the display to the ESP32 is as follows:

| Display Pin | ESP32 Pin |
| ---------- | ---------- |
| 1 | **3.3V** |
| 2 | **GPIO4** |
| 3 | **GPIO21** |
| 4 | **GPIO15** |
| 5 | **GND** |
| 6 | **GPIO2** |
| 7 | **GPIO19** |
| 8 | **GPIO18** |
| 9 | **GPIO16** |
| 10 | GPIO17 |
| 11 | NC |
| 12 | GPIO14 |
