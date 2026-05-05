# Wasserzähler ESPHome


<img width="800" alt="image" src="https://github.com/user-attachments/assets/b6a7d2c6-db03-42c1-bac7-4da6eab7282a" />

<img width="800" alt="image" src="https://github.com/user-attachments/assets/de795593-85bb-4de0-8c0e-540b7bfe3cc5" />


## Funktion

ESPHome-Firmware für einen ESP32-C3 SuperMini, die mit einem induktiven Sensor die Impulse eines Diehl Corona MCI 108 Wasserzählers (1 L/Puls) zählt und an Home Assistant meldet. Home Assistant führt den eigentlichen Zählerstand; das OLED zeigt den HA-Zählerstand, den aktuellen Durchfluss und das WLAN-Signal. Ein TTP223-Touchbutton erlaubt manuelle +1-L-Korrekturen per kurzem Tipp.

## Home Assistant

Der ESP sendet `Impulse gesamt` als Gesamtzähler. Jeder echte Impuls erhöht diesen Zähler um 1 L; ein kurzer Tipp auf den TTP223 erhöht denselben Gesamtzähler manuell um 1 L. Der Utility Meter in Home Assistant kann diesen Gesamtzähler als Quelle nutzen; `Delta values` ist dafür nicht nötig.

Die Entity `Touch Tastensperre` deaktiviert manuelle Korrekturen per TTP223. Nach einem Neustart ist die Tastensperre wieder aus.

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
| GPIO3  | TTP223 (kurz = +1 L)                      |
| GPIO21 | Sensor Signal (NPN, 10 kΩ Pull-Up 3V3)    |

GPIO2/8/9 bleiben frei (Strapping-Pins).

## Credits

- Sensorhalterung (3D-Druck): [Inductive sensor holder for Diehl Corona MCI](https://www.printables.com/model/465845-inductive-sensor-holder-for-diehl-corona-mci) von *timn*
- Referenz-ESPHome-Konfiguration: [timn/esphome-meters — water](https://github.com/timn/esphome-meters/tree/main/water)
