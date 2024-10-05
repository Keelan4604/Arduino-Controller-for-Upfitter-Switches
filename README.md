# Arduino Controller for Upfitter Switches

## Overview
I've finally taken the time to properly wire up the **upfitter switches** in my truck to an **Arduino-based microcontroller setup** mounted in the toolbox. The goal was to build a robust and modular infrastructure that could control multiple accessories, such as a large **air compressor**, **lights**, **train horn**, and other electronic add-ons—all while being easily expandable through software updates and hardware add-ons.

## Power and Wiring Setup
The foundation of this setup relies on clean and reliable power distribution:
- **Power Supply**: A **2 AWG wire** runs directly from the **battery** to **jump posts** located in the back of the vehicle. This provides solid power delivery to a **2000W power inverter**, which will power a **large air compressor** in the back.
- **Upfitter Switch Wiring**: The **upfitter switches** are wired to the toolbox. They connect through the **10A** or **20A leads** and pass through a **Deutsch connector** onto a **breadboard**. From there, the voltage is regulated down to **12V**.
- **Arduino Integration**: The switches are further regulated using a **10,000-ohm resistor** to drop the voltage before sending it through a **2N2222 transistor**. This transistor then pulls **4 Arduino pins** to ground, which are programmed as **pull-up resistors**. The Arduino and breadboard share a common power source from a **5V voltage regulator** to avoid overvolting and damaging the Arduino's **ATMEGA328P** microcontroller.

## Functionality and Modular Design
This infrastructure is designed to be **modular and expandable**. Right now, the Arduino setup controls a **two-way DC motor controller** through pins **8** and **9**, which operates a **cutout exhaust** system. The robust wiring and power regulation allow for future expansion, including:
- **Control over Air Compressor**: Using the upfitter switches and Arduino to manage the compressor through relays and MOSFETs.
- **Lights, Train Horn, and Other Add-ons**: As the project grows, the Arduino can easily control additional accessories by modifying the software and adding hardware relays or transistors as needed.
- **Potential Bluetooth and Special Programming**: The modularity allows for easy implementation of **Bluetooth connectivity**, custom light flashing sequences, or other special functions through simple Arduino code updates.

## Current Status and Challenges
I’ve confirmed that the **entire system works** in theory, except for some resistor-related issues with the Arduino inputs. Right now, I'm waiting on a new **Arduino board** to arrive, which will allow me to finalize the programming and functionality.

### Challenges & Solutions
- **Cutout Exhaust Control Issue**: One issue I've encountered is that the **low voltage disconnect (LVD)** powering the Arduino remains on when the upfitter switch is on, and the truck is off. This makes the Arduino think the upfitter switch has been turned off, which triggers the exhaust cutout to close. While not a critical issue, it’s not ideal.
  - **Potential Solution**: A potential solution is to use an **unused button on the steering wheel** to control the cutout exhaust instead of the upfitter switch. A button would provide better control over this type of function than a switch, allowing for precise operation of the exhaust cutout.

- **Programming & Backup Bootloaders**: When the new Arduino arrives, I plan to **reburn the bootloader** on a few spare ATMEGA328P microcontrollers to have backups on hand in case I brick another one. This way, if an issue arises, I can swap in a new microcontroller and continue testing.

### Next Steps
After resolving the programming and wiring issues, the next major step will be to cut out a spot in the toolbox and **mount the relay switch box**. This process will involve a fair amount of wiring, which isn't the most exciting task, especially since there are no accessories currently needing those relays. However, once I install some lights or other accessories, it will be worth the effort to get everything wired up and functioning.

---

Overall, this project has been a great way to learn about **microcontroller integration**, **power regulation**, and **Arduino programming**. Once fully operational, it will provide a flexible and powerful control system for all the accessories I plan to add to my truck.
