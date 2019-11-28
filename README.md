# esp32DHT

[![Build Status](https://travis-ci.com/bertmelis/esp32DHT.svg?branch=master)](https://travis-ci.com/bertmelis/esp32DHT)

This is a DHT11/22 library for ESP32 using the RMT peripheral, for use in the ESP-IDF framework.

The library is non blocking, doesn't use delay and is usable in async frameworks. The library is kept simple on purpose. You are responsible yourself to follow the sensor's constraints (like polling frequency) and logical programming errors. Supplementary functions like dew point calculation are not included.

## Installation

In your ESP-IDF project, use `git submodule add git@github.com:john-yan/esp32DHT.git components/esp32DHT`

## Usage

```C++
```

> Note: `setup(uint8_t, rmt_channel_t channel = RMT_CHANNEL_0);` taks 2 arguments: the pin connected to the DHT sensor and the RMT channel[0-7]. The library uses 2 channels and defaults to (starting) channel 0. This means that by default channel 0 and channel 1 are occupied by the DHT and you should not use channel 7. If you're also using other RMT channels (for IR devices, extra DHT sensors, Neopixels...) you have to keep this in mind.
>
> Read more about RMT in the docs: [ESP-IDF documentation](https://esp-idf.readthedocs.io/en/latest/api-reference/peripherals/rmt.html)

## History

Whatever can be done using hardware should not be done by software. ESP32 has a RMT peripheral device which is remarkably versatile. As the DHT sensors rely on tight timing, the RMT device is perfect to accomplish reliable communication. I didn't find any other Arduino library that uses the RMT and/or doesn't block during communication. So I created my own one.

> This library won't exist without the examples for RMT. Credits go to the team and contributors of ESP-IDF and @nkolban!
