# Boss DS-1 Distortion Clone V2 (Custom Build)

![Hardware](https://img.shields.io/badge/Hardware-PCB_Design-blue)
![Software](https://img.shields.io/badge/EDA-KiCad-green)

## About The Project

This repository contains the schematic, PCB design files, and build documentation for a custom-built clone of the legendary Boss DS-1 Distortion pedal. Designed from the ground up using **KiCad**, this project aims to faithfully recreate the iconic hard-clipping distortion tone while implementing modern hardware practices such as True Bypass switching and optimized component routing.

## Key Features & Modifications

While the core audio path remains true to the original DS-1 architecture, several mechanical and component-level modifications were made based on the local availability of certain original components and hardware.

* **Custom Transistor Selection:** The original BC549C transistors were substituted with **JC2N3904S49 (NPN)** transistors for the input buffer (Q1), gain boost (Q2), and output buffer (Q3) stages. The PCB footprints were carefully matched to accommodate the E-B-C pinout of the 2N3904.
* **True Bypass Switching:** Unlike the original Boss buffered bypass, this build utilizes a **3PDT 9-Pin Latching Footswitch**. This ensures zero tone coloration when the pedal is disengaged and includes an independent pole for the status LED.
* **Smart Power Management:** Integrated a Stereo Input Jack to act as a ground-shunt switch. The 9V battery is completely disconnected from the circuit when the input cable is unplugged, preserving battery life.
* **Capacitor Accuracy:** High-quality film and ceramic capacitors are used throughout the tone stack and filtering stages (e.g., precise 100pF and 220pF ceramics for RF filtering in the op-amp feedback loop).
* **Modular Design:** All parts that require a cable connection are routed using JST connectors to ensure a clean, solder-free assembly process. This allows the main PCB to be easily installed, serviced, or modified without the need to desolder off-board components like the footswitch, potentiometers, and audio jacks.
* **Grounded Mounting Holes:** The PCB mounting holes include GND pads, so the board can be grounded to a metal enclosure through its mounting screws for shielding.

## Tools & Technologies Used

* **EDA Software:** KiCad (Schematic Capture & PCB Layout)
* **CAD Software:** Fusion 360 (PCB measurements & enclosure fitting)
* **Testing & Measurement:** UNI-T UT33D+ Digital Multimeter
* **Audio Components:** 1/4" Mono/Stereo Jacks, Custom PCB.

## Hardware Wiring Guide

Proper off-board wiring is critical for a noise-free pedal. All off-board connections are managed via JST connectors to ensure a clean, solder-free assembly process. This allows the main PCB to be easily installed, serviced, or modified without the need to desolder components like the footswitch, potentiometers, and audio jacks.

Here is the standard True Bypass implementation used in this build:

* **Input Jack (Stereo):**
   * *Tip:* Routed to 3PDT Switch (Lug 2).
   * *Ring:* Connected to the 9V Battery Negative.
   * *Sleeve:* Connected to System Ground (Star Grounding).
* **Output Jack (Mono):**
    * *Tip:* Routed from 3PDT Switch (Lug 5).
    * *Sleeve:* Connected to System Ground.

* **3PDT Footswitch (True Bypass):**
   When wiring the 9-pin switch, orient the flat metal lugs horizontally (so you see 3 rows and 3 columns).

   ```text
   [1] PCB Input         [4] PCB Output         [7] LED Negative (-)
   [2] Input Jack (Tip)  [5] Output Jack (Tip)  [8] Ground (GND)
   [3] Jumper to Lug 6   [6] Jumper to Lug 3    [9] Empty
   ```

## Enclosure & 3D Model

![Enclosure Assembly](<Boss DS-1 Clone - Pictures/Boss DS-1 Clone (Enclosure Assembly) - Izometric.png>)

The full pedal was assembled in **Fusion 360** to check how the PCB, potentiometers, jacks, footswitch and 9V battery fit inside the enclosure before manufacturing.

* **Enclosure:** Black plastic handheld enclosure, **76 × 136 × 50 mm**, bought from Robotistan as *"76 x 136 x 50 mm El Tipi Kutu (Siyah)"*. Its dimensions match the Altınkaya HH-070 handheld enclosure.
* **Model files** (in [`Boss DS-1 Clone - 3D Model`](<Boss DS-1 Clone - 3D Model>)):
    * `Boss DS-1 Clone (Assembly).f3z` — Fusion 360 archive of the full assembly.
    * `Boss DS-1 Clone (Assembly).step` — STEP export for FreeCAD, KiCad and other CAD tools.

> [!NOTE]
> The enclosure in this model was created for fit-checking only. It is modeled to the exact outer dimensions of the box above, but it has no screw holes to join the body and lid and has not been tested for 3D printing. It is not intended to be printed as-is; use the off-the-shelf enclosure instead.

> [!NOTE]
> The PCB mounting holes have GND pads, so the board can be grounded through its mounting screws. This only provides shielding when the pedal is built into a **metal** enclosure. The plastic enclosure used in this build does not act as a shield.

## Previous Version

The first version of this pedal is kept at [Boss-DS-1-Clone](https://github.com/emrebuyukonder/Boss-DS-1-Clone) for project history. It has several known design issues that are fixed in this version and should not be used for a build.

## Author

Designed and built by **Erdoğan Emre Büyükönder** (Music Producer). 

As an Electrical-Electronics Engineering student and a music producer, this project bridges the gap between theoretical circuit analysis and practical, stage-ready audio equipment.

---
*Note: The "Boss" and "DS-1" names are trademarks of Roland Corporation. This project is strictly for educational purposes and personal use.*
