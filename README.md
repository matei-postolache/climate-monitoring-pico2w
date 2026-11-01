# Climate Monitoring & Alert Station (Raspberry Pi Pico 2W)

An embedded environmental monitoring and alert system written in C using the Pico SDK, running on the Raspberry Pi Pico 2W (RP2350 microcontroller).

## Project Overview
The board reads ambient temperature and humidity, outputs real-time data across two screens, and triggers alarms if values cross safety boundaries:
- **Non-blocking main loop:** Removed all blocking sleep calls (`sleep_ms`); button polling runs every 10 ms and sensor sampling every 2 seconds asynchronously.
- **Dual screen setup:** A 4-bit parallel LCD 1602 shows live sensor data, while an I2C SSD1306 OLED displays the active threshold configuration.
- **Hardware-driven buzzer:** Critical temperature warnings trigger a 1 kHz tone generated directly by the hardware PWM peripheral, freeing the CPU from audio generation.
- **Resistor ladder keypad:** Reads 5 tactile push buttons through a single 12-bit ADC input (GP26) to save GPIO pins.
- **Bus resilience:** The custom 1-Wire communication handles sensor timeouts gracefully to prevent hangs if the DHT22 disconnects.

## Hardware Used
- Raspberry Pi Pico 2W (dual-core ARM Cortex-M33)
- DHT22 digital temperature & humidity sensor (1-Wire)
- LCD 1602 display (parallel 4-bit mode)
- SSD1306 OLED display (I2C)
- 5-button analog shield (ADC0)
- Passive buzzer (PWM driven) & 1-channel relay module

## Media & Setup
Photos of the physical circuit and wiring can be found in the `media/` directory.

## Author
- Matei Postolache
