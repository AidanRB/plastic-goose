# plastic-goose
The goal of this repository is to create a Rubber Ducky-like device out of an RP2040 based device, primarily the [Waveshare RP2040-One](https://www.waveshare.com/rp2040-one.htm). It should also support the Raspberry Pi Pico and Pico W with about the same feature set.

## Setup
1. Flash your device with [CircuitPython](https://circuitpython.org/downloads).
    - Generally, this looks like:
        1. Download the CircuitPython file for your device.
        2. Hold the BOOT/BOOTSEL button on your device.
        3. Plug it into your computer; it should mount as `RPI-RP2`.
        4. Copy the CircuitPython `.uf2` file onto the device.
        5. The device will reboot and remount as `CIRCUITPY`.
    - There is currently not a CircuitPython version for the Waveshare RP2040-One; the [RP2040-Zero](https://circuitpython.org/board/waveshare_rp2040_zero/) file will work fine.
2. Copy required libraries onto your device.
    1. Download and extract the [latest CircuitPython 8.x bundle](https://github.com/adafruit/Adafruit_CircuitPython_Bundle/releases/latest).
        - The filename will look like `adafruit-circuitpython-bundle-8.x-mpy-YYYYMMDD.zip`.
    2. Copy these folders/files from the `lib` folder in the zip to the `lib` folder on your device:
        1. `adafruit_hid`
        2. `adafruit_wsgi`
        3. `asyncio`
        4. `adafruit_debouncer.mpy`
        5. `adafruit_pixelbuf.mpy`
        6. `adafruit_ticks.mpy`
        7. `neopixel.mpy`
    3. Copy files from this repository onto your device.
        - All you need is the `.py` files. `payload*.py` may be omitted in favor of your own payload/s.

## Usage
By default, the device will only present a keyboard to the host computer. To mount your device as a mass storage device to edit the files, connect pin `GP0` to `GND`. This will also enable the serial device to access the Python console.
- On a Waveshare RP2040-One, this is `0` and `GND`.
- On a Raspberry Pi Pico, look at the back of the device to see the labels. `GP0` is at the very corner of the device.

To select a payload other than `payload.py`, connect GND to one of `GP1`-`GP4`.

## Reference