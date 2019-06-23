## Prototype Hardware ##

The dev board for prototyping consists of two major components:

* Adafruit ESP32 Feather Dev Board (https://www.amazon.com/Adafruit-HUZZAH32-ESP32-Feather-Board/dp/B01NCRYHDL/)
* 1.8" TT w/resistive touch panel (https://www.buydisplay.com/default/display-1-8-inch-spi-128x160-tft-touch-screen-lcd-module-datasheet)

[TFT Display Breakout Datasheet](https://github.com/biohacking-village/tamagotchi/edit/master/prototype/ER-TFTM018-2_Datasheet.pdf)

## Prototype Software ##

Software will be flashed on the ESP32 using the Arduino IDE. Support libraries for the TFT display and touch panel are listed below.

### Setup Toolchain ###

1. Download the Arduino IDE: (https://www.arduino.cc/en/Main/Software)
2. Install extensions for ESP32 in Arduino: (https://github.com/espressif/arduino-esp32/blob/master/docs/arduino-ide/boards_manager.md)
3. If needed, install drivers for CP2104: (https://learn.adafruit.com/adafruit-huzzah32-esp32-feather/using-with-arduino-ide)

To verify the installation was successful, connect the ESP32 board via USB, open the Arduino IDE, and under the _Tools_ > _Board:_ menu, select the ESP32 Adafruit Feather (or other ESP32 board if you are using a different dev board). After selecting, review the options listed in the _Tools_ > _Port_ side menu. If the drivers were installed and the board is connected, a port should be automatically selected or available for selection. You can finish validation by flashing a basic Example sketch such as Blink to the board.

### Display & Touch Libraries ###

To support the TFT display and resistive touch panel breakout, you will need to download the TFT_eSPI libraries and install in Arduino:

* Download **TFT_eSPI**: (https://github.com/Bodmer/TFT_eSPI)
* Installing Libraries in Arduino: (https://www.arduino.cc/en/Guide/Libraries)

Additionally, you will need to open the TFT_eSPI User_Setup.h file and make sure the pins in the header match the wiring you will be using to connect the display to the dev board. For the tamagotchi, the wiring is as follows:

Display Pin | ESP32 Pin
------------ | -------------
1 | 3v3
2 | GPIO4
3 | GPIO18
4 | GPIO15
5 | GND
6 | GPIO2
7 | GPIO19
8 | GPIO23

![Front of TFT Breakout](https://github.com/biohacking-village/tamagotchi/blob/master/prototype/tft-pin-ex.JPG)

Final User_Setup.h should reflect something like the below:
```C++
// ###### EDIT THE PIN NUMBERS IN THE LINES FOLLOWING TO SUIT YOUR ESP32 SETUP   ######

// For ESP32 Dev board (only tested with ILI9341 display)
// The hardware SPI can be mapped to any pins

#define TFT_MISO 19
#define TFT_MOSI 18 // 23
#define TFT_SCLK 21 // 18
#define TFT_CS   15  // Chip select control pin
#define TFT_DC    2  // Data Command control pin
#define TFT_RST   4  // Reset pin (could connect to RST pin)
//#define TFT_RST  -1  // Set TFT_RST to -1 if display RESET is connected to ESP32 board RST
```

Once you have modified the User_Setup.h (or replaced the default with the already modified version uploaded here), you can verify your display is working by flashing and testing the display and touch panel:

* Open Arduino and select _File_ > _Examples_ > _TFT_eSPI_ > _Generic_ > _Touch_calibrate_
* Flash to the ESP32 board
* Connect the display using the above wiring
* Reset the dev board and follow the on-screen instructions using a touchscreen friendly stylus


