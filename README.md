# Wasserzähler ESPHome

## Funktion

ESPHome-Firmware für einen ESP32-C3 SuperMini, die mit einem induktiven Sensor die Impulse eines Diehl Corona MCI 108 Wasserzählers (1 L/Puls) zählt und an Home Assistant meldet. Das OLED zeigt den HA-Zählerstand und den aktuellen Durchfluss; ein TTP223-Touchbutton erlaubt manuelle +1-L-Korrekturen per Doppeltipp.

## Hardware

- ESP32-C3 SuperMini (externe 2.4 GHz SMA-Antenne)
- Induktivsensor LJ18A3-8-Z/BX-5V (M18, NPN, NO, 5 V, 8 mm)
- OLED 0.96" SSD1306 128×64 I²C
- TTP223 kapazitives Touch-Modul
- USB-C Einbaubuchse (5 V), IP67 Transparentgehäuse 100×68×40 mm
- Externer 10 kΩ Pull-Up Sensor → 3.3 V

## GPIO Pinout

| Pin    | Funktion                                  |
|--------|-------------------------------------------|
| 5 V    | USB-C, Sensor VCC                         |
| 3.3 V  | OLED VCC, TTP223 VCC, Pull-Up GPIO21      |
| GND    | gemeinsam                                 |
| GPIO0  | OLED SDA                                  |
| GPIO1  | OLED SCL                                  |
| GPIO3  | TTP223 (Doppeltipp = +1 L)                |
| GPIO21 | Sensor Signal (NPN, 10 kΩ Pull-Up 3V3)    |

GPIO2/8/9 bleiben frei (Strapping-Pins).
