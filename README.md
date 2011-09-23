AR1010lib
=========

The AR1010 FM Receiver Breakout Board is a miniature FM radio receiver whose parameters can be controlled over an I2C (two-wire) or an SPI (three-wire) serial interface, thus making it ideal for connection to an Arduino.

This library uses the I2C serial protocol, accessed through the Arduino's analog in pins 4 & 5. It allows for custom initialisation, and the setting of tuning frequency, volume, hardmute and softmute values. Although the library probably isn't feature complete it shouldn't be difficult to add in higher-level functions using the available programming guide* and some of the lower-level functions available in the library.

*The programming guide for the Airoha AR1000 (version 0.81, RevF) is also suitable for the AR1010, and contains accurate register maps of the module's functionality.


INSTALLATION
------------

* Install the AR1010lib library, following the instructions in the Contributed Libraries section on the [Arduino Libraries](http://www.arduino.cc/en/Reference/Libraries) page
* Make sure to add `#include <ar1010lib.h>` to the beginning of any necessary Sketchbook file
* Add the Arduino's Wire library here too


USAGE
--------------

### Hardware

* Connect AR1010 Data To to Arduino Analog in 4
* Connect AR1010 Clock to Arduino Analog in 5 

### Global

* Define an AR1010 instance: `AR1010 radio = AR1010();`
* Optionally define an array to set the AR1010's registers. This should be of type `word` and 18 elements large. Refer to the programming guide for the configurations of the registers

### Setup() function

* Begin I2C comms with the Wire library: `Wire.begin();`
* Initialise the AR1010 instance: `radio.initialise();` - optionally pass register array as argument here
* Add a second delay: `delay(1000);`

### The rest

Access library functions through the AR1010 instance; for example, to set the radio frequency use `radio.setFrequency(910);` to set it to 91.0MHz.
