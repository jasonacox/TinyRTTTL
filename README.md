# TinyRTTTL - Arduino RTTTL Song Player # 
[![arduino-library-badge](https://www.ardu-badge.com/badge/TinyRTTTL.svg?)](https://www.ardu-badge.com/TinyRTTTL)
[![Build Status](https://travis-ci.org/jasonacox/TinyRTTTL.svg?branch=master)](https://travis-ci.org/github/jasonacox/TinyRTTTL)

Arduino Library to play RTTTL Songs on Speaker

## Description
This is an Arduino library to decode and play RTTTL (RingTone Text Transfer Language) songs via the tone() function. Works well with small piezo speakers. 

Ring Tone Text Transfer Language (RTTTL) was developed by Nokia to be used to define ringtones to be used in their cellphones (see [Wikipedia](https://en.wikipedia.org/wiki/Ring_Tone_Transfer_Language))  The format made it easy for people to create their favorite songs as ringtones. There are many available online.

Library also runs well on tiny controllers including the ATtiny85.

## Hardware
This library is designed to use the Arduino built in tone() function to play the notes on an attached piezo speaker (see [here](https://create.arduino.cc/projecthub/SURYATEJA/use-a-buzzer-module-piezo-speaker-using-arduino-uno-89df45)).

[![Speaker](speaker.jpg)](speaker.jpg)

* PC Internal Speaker Buzzer - https://smile.amazon.com/gp/product/B01MR1A4NV/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1

## Installation
Install this manually by cloning this repo into your Arduino library folder (e.g. `~/Documents/Arduino/libraries`).  

## Usage
The library provides a single class named TM1637TinyDisplay with the following functions:

* `play` - Play song by passing RTTTL string to function
* `play_P` - PROGMEM function of the above to keep data in Flash instead of being loaded in to SRAM to save memory. 

## Example Code
```cpp
#include <Arduino.h>
#include <TinyRTTTL.h>

// Define Location of Speaker
#define SPK 1

// Define Octive Offset
#define OCTIVE 0

// Initialize TM1637TinyDisplay
TinyRTTTL rtttl(SPK, OCTIVE);

// Sample song to play in RTTTL format
char *song = "SMBtheme:d=4,o=5,b=100:16e6,16e6,32p,8e6,16c6,8e6,8g6,8p,8g,8p,8c6,16p,8g,16p,8e,16p,8a,8b,16a#,8a,16g.,16e6,16g6,8a6,16f6,8g6,8e6,16c6,16d6,8b,16p,8c6,16p,8g,16p,8e,16p,8a,8b,16a#,8a,16g.,16e6,16g6,8a6,16f6,8g6,8e6,16c6,16d6,8b,8p,16g6,16f#6,16f6,16d#6,16p,16e6,16p,16g#,16a,16c6,16p,16a,16c6,16d6,8p,16g6,16f#6,16f6,16d#6,16p,16e6,16p,16c7,16p,16c7,16c7,p,16g6,16f#6,16f6,16d#6,16p,16e6,16p,16g#,16a,16c6,16p,16a,16c6,16d6,8p,16d#6,8p,16d6,8p,16c6";

void setup() {
  rtttl.play(song)
}

void loop() {
  delay(1000);
}
```

## References and Credit
* RTTTL Format Specification - http://merwin.bespin.org/t4a/specs/nokia_rtttl.txt and https://www.mobilefish.com/tutorials/rtttl/rtttl_quickguide_specification.html
* Tone by Brett Hagman - @bhagman - https://github.com/bhagman/Tone and especially the example RTTTL script https://github.com/bhagman/Tone/blob/master/examples/RTTTL/RTTTL.pde
* Instructables - https://www.instructables.com/RTTL-Tunes-on-arduino/

