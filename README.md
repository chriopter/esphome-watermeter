# Wasserzähler ESPHome

Impulszähler für einen MOM/Diehl Corona MCI 108 Wasserzähler auf Basis eines
ESP32-C3 SuperMini mit induktivem Sensor (LJ18A3-8-Z/BX-5V), OLED-Display
und zwei TTP223 Touch-Buttons zur manuellen Kalibrierung.

Der Zählerstand selbst wird nicht auf dem ESP gespeichert (Flash-Schonung),
sondern über Home Assistant `utility_meter` getrackt und zur Anzeige
zurückgeholt.

## Hardware

- ESP32-C3 SuperMini (externe 2.4 GHz SMA-Antenne)
- Induktivsensor LJ18A3-8-Z/BX-5V (M18, NPN, Normally Open, 5 V, 8 mm)
- OLED 0.96" SSD1306 128×64 I²C
- 2× TTP223 kapazitive Touch-Module
- USB-C Einbaubuchse (5 V), IP67 Transparentgehäuse 100×68×40 mm

## Pinout

| Pin    | Funktion                                      |
|--------|-----------------------------------------------|
| 5 V    | USB-C, Sensor VCC                             |
| 3.3 V  | OLED VCC, TTP223 VCC, Pull-Up für GPIO4       |
| GND    | gemeinsam                                     |
| GPIO0  | OLED SCL                                      |
| GPIO1  | OLED SDA                                      |
| GPIO3  | TTP223 "−" (Kalibrierung runter, links)       |
| GPIO4  | TTP223 "+" (Kalibrierung hoch, rechts)        |
| GPIO5  | Sensor Signal (NPN, 10 kΩ Pull-Up nach 3.3 V) |

GPIO2/8/9 bleiben frei (Strapping-Pins).

## Credits

- Sensorhalterung (3D-Druck): [Inductive sensor holder for Diehl Corona MCI](https://www.printables.com/model/465845-inductive-sensor-holder-for-diehl-corona-mci) von *timn*
- Referenz-ESPHome-Konfiguration: [timn/esphome-meters — water](https://github.com/timn/esphome-meters/tree/main/water)
