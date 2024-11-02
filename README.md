# Twinbus Doorbell PCB with ESPHome Integration

This project provides a PCB that communicates with **ESPHome** to send a notification when someone rings the doorbell. Additionally, it can be configured to either:
- Automatically unlock the door after a specified time period, or
- Allow manual control of the door via an **Entity** in your home automation system.

## Notes

**Do not work on the Twinbus PCB when it is connected, it is a very fragile system which might break when there is a short.**

This project works reliably even without a custom PCB. The most important thing is the seperate power supply for the ESP8266 and that the grounds of both PCBs are always connected.
Other than soldering to the original PCB there are no other changes made. It still works the same way.
The system will trigger on both the front doorbell as well as the apartment doorbell as there is no differentiation.
If you want to mount the PCB without damaging the original casing you can mount it with pressure sensitive tape.

![PCB Front](https://github.com/user-attachments/assets/bc4f5a12-e06e-4cfc-ab80-2fbcd491545e)


## Power Considerations

Due to the fragile nature of the **Twinbus** system, it's not possible to power the PCB directly from the Twinbus itself. Doing so would render your entire door panel inoperative as long as the PCB is connected. To avoid this, the PCB utilizes a **voltage divider** to reduce the 5V doorbell signal to 3.3V, making it compatible with the **ESP8266** input.

A voltage divider works effectively because it draws almost no power from its source. While we used **10kΩ resistors** for testing, other higher-value resistors may also work. For example, we tested **11kΩ resistors** with no noticeable difference.

**Both the PCB of the ESP8266 and the Twinbus PCB need to share a common ground in order to work. The newer version has two ground pads for this reason**

The following Voltages are present at the original "Wohntelefon 7360"
- 5V while ringing the doorbell
- 24V of the Twinbus system itself 

## Door Lock Activation

To minimize interference with the original PCB, an **NPN transistor** is used to trigger the door lock signal. While you may be able to use different NPN transistors, we have successfully tested this with the **2N2222**.



## Documents:
Ritto Twinbus user manual:
https://asset.conrad.com/media10/add/160267/c1/-/de/000469693ML01/04-Bedienung.pdf

