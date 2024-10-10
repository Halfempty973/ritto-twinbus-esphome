# Twinbus Doorbell PCB with ESPHome Integration

This project provides a PCB that communicates with **ESPHome** to send a notification when someone rings the doorbell. Additionally, it can be configured to either:
- Automatically unlock the door after a specified time period, or
- Allow manual control of the door via an **Entity** in your home automation system.

## Power Considerations

Due to the fragile nature of the **Twinbus** system, it's not possible to power the PCB directly from the Twinbus itself. Doing so would render your entire door panel inoperative as long as the PCB is connected. To avoid this, the PCB utilizes a **voltage divider** to reduce the 5V doorbell signal to 3.3V, making it compatible with the **ESP8266** input.

A voltage divider works effectively because it draws almost no power from its source. While we used **10kΩ resistors** for testing, other higher-value resistors may also work. For example, we tested **11kΩ resistors** with no noticeable difference.

## Door Lock Activation

To minimize interference with the original PCB, an **NPN transistor** is used to trigger the door lock signal. While you may be able to use different NPN transistors, we have successfully tested this with the **2N2222**.


## Documents:
Ritto Twinbus user manual:
https://asset.conrad.com/media10/add/160267/c1/-/de/000469693ML01/04-Bedienung.pdf

