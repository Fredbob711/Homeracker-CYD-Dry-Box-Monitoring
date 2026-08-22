# ESPHome Dry Box Controller

So my goal with this was to build an ESP32 device that could monitor the temp/humidity in 3D Printed Homeracker Dry Boxes. I had a CYD with the I2C port sitting around, so grabbed that. Some SHT45 temp/humidity sensors, TCA9548A multiplexer(s), and 4-pin connectors of your choice (I bastardized some RJ45 connectors for mine).

Obligatory Reddit post explaining what I did: 

## Features

* 🌡️ Temperature monitoring
* 💧 Humidity monitoring
* 🖥️ Local touchscreen interface
* 🏠 Home Assistant integration
* 📡 Wi-Fi connectivity
* ⚫ Screen blanking logic for a clean "off" state

## Hardware
The project is built around a Hosyond ESP32S3 2.8" Touchscreen, TCA9548A multiplexer, and SHT45 temp/humidity sensors installed in the drybox.

Links:

CYD: https://www.amazon.com/dp/B0FKG7WRWV?th=1

TCA9548A: https://www.amazon.com/dp/B0FDFQ94HB

SHT45: https://www.amazon.com/dp/B0H69PZ7RJ

## User Interface
The touchscreen is designed to make the drybox useful as a standalone device without requiring a Home Assistant dashboard for basic information.

The main interface provides at-a-glance information for up to 8 dry boxes at once, including:
* Current Temperature
* Current Humidity
* Filament Type/Color

If you have more than 8 boxes, just create more pages!

There is a secondary interface that allows you to change the Filament Type & Color for a given Box #, this is also editable in Home Assistant.

The display also includes screen/backlight handling so the LCD can be properly blanked when not in use rather than simply displaying an illuminated black UI page.

## Home Assistant
The drybox connects directly to Home Assistant through ESPHome's native API.

This allows sensor readings, controls, and device status to be exposed to Home Assistant while keeping the primary display and monitoring functionality on the ESP32 itself. So Home Assistant is useful, but you don't need a dashboard open just to check the drybox.

## Credit
I want to give credit to RyanEwen and his esphome-lvgl project. I've used it extensively to help me understand esphome and as a starting point for my own projects. Several files are straight out of his repo.

RyanEwen: https://github.com/RyanEwen
esphome-lvgl: https://github.com/RyanEwen/esphome-lvgl
