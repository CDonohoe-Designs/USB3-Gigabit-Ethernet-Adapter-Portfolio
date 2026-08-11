# USB 3.1 Gen 1 to Gigabit Ethernet Adapter

LAN7800-based USB 3.1 Gen 1 to Gigabit Ethernet adapter designed in **Altium Designer** as a high-speed hardware and PCB design portfolio project.

<p align="center">
  <img src="Images/PCB_3D.PNG" alt="LAN7800 USB 3.1 to Gigabit Ethernet adapter 3D view" width="850">
</p>

## Project Overview

I designed this board to convert a **USB 3.1 Gen 1 (5 Gbit/s)** host connection to **10/100/1000BASE-T Ethernet** using the Microchip **LAN7800** USB-to-Ethernet controller.

I developed the project to demonstrate the complete hardware design process rather than schematic capture alone, including component selection, power architecture, controlled-impedance routing, high-speed PCB constraints, grounding and return-path control, manufacturability rules, DRC, and fabrication documentation.

### Key design features

- I used the Microchip **LAN7800** USB 3.1 Gen 1 to Gigabit Ethernet controller
- I implemented USB 2.0 and USB 3.x interfaces
- I routed the Gigabit Ethernet MDI interface to an RJ45 MagJack
- I used a **4-layer PCB** with dedicated internal ground reference planes
- I targeted **90 Ω differential impedance** for USB
- I targeted **100 Ω differential impedance** for Gigabit Ethernet
- I created dedicated Altium **net classes, differential-pair classes and routing rules**
- I applied length matching and controlled pair spacing to the high-speed interfaces
- I used separate power routing and pours for the LAN7800 supply rails
- I positioned ESD/protection components close to the external interfaces
- I prepared the fabrication drawing and manufacturing outputs
- I checked the final PCB using Altium DRC

## High-Speed Design Approach

I treated the PCB as a **high-speed design**, with the layout driven by signal-integrity and return-path requirements rather than by simple point-to-point connectivity.

The main design methods I used were:

- **Controlled impedance:** I created dedicated Altium impedance profiles for 90 Ω USB and 100 Ω Ethernet differential routing.
- **Differential-pair classes:** I separated the USB 2.0, USB 3.x and Ethernet MDI signals into dedicated classes so I could apply interface-specific constraints consistently.
- **Length matching:** I used matched-length rules to control skew within the high-speed differential pairs, with separate Ethernet pair-to-pair matching constraints.
- **Continuous reference planes:** I routed the high-speed signals primarily on the outer signal layer over an adjacent solid ground reference plane.
- **Layer restrictions:** I constrained the high-speed classes to the intended routing layers to avoid unnecessary layer changes and reference-plane discontinuities.
- **Controlled spacing and clearance:** I used dedicated rules for pair geometry, pair-to-pair spacing and clearance from unrelated copper.
- **Via control:** I defined separate via styles for general and higher-current power routing.
- **Power integrity:** I used local power pours, short decoupling paths and large ground regions around the LAN7800 and its regulators.
- **Manufacturing constraints:** I included minimum annular ring, drilled-hole, solder-mask and silkscreen rules in the PCB rule set.
- **Rule-driven verification:** I used Altium's PCB Rules and Constraints system and DRC to check that the physical implementation remained consistent with the design intent.

> **Design status:** This repository presents my Rev A schematic, PCB layout and fabrication design intent. It does not claim production or laboratory signal-integrity validation.

## PCB Layout

### Top side

I used the top layer for the principal signal routing, including the USB and Ethernet differential interfaces and the LAN7800 support circuitry.

<p align="center">
  <img src="Images/PCB_Layout_Top.PNG" alt="Top PCB layout" width="850">
</p>

### Bottom side — power and ground distribution

I used the bottom side for local power distribution together with a broad GND copper pour. The internal ground planes provide the primary high-speed reference structure.

<p align="center">
  <img src="Images/PCB_Layout_Bottom.PNG" alt="Bottom PCB layout showing power and ground pours" width="850">
</p>

## Schematic

I split the design into two functional sheets: **USB/power** and **LAN7800/Ethernet**.

<p align="center">
  <img src="Images/Schematic_Overview.png" alt="LAN7800 and Ethernet schematic overview" width="780">
</p>

<details>
<summary><b>View USB and power schematic overview</b></summary>

<p align="center">
  <img src="Images/Schematic_Overview_Power_USB.png" alt="USB and power schematic overview" width="780">
</p>

</details>

**[View the complete schematic PDF](Docs/LAN7800_USB_Ethernet_RevA_Schematic.pdf)**

**[View the Rev A fabrication drawing](Docs/LAN7800_USB_Ethernet_RevA_Fabrication.PDF)**

**[Download the Rev A fabrication package](Manufacturing/LAN7800_USB_Ethernet_RevA_Fabrication.zip)**  
Gerber X2, NC Drill and fabrication documentation.

## Design Verification

I ran a final Altium **Design Rule Check** against the configured PCB rule set after completing the layout and copper pours. The final report shows **0 warnings and 0 rule violations**.

<p align="center">
  <img src="Images/DRC.PNG" alt="Altium final DRC report showing zero warnings and zero rule violations" width="850">
</p>

## Altium Design Rules

I used a rule-driven approach rather than manually routing each interface with ad-hoc settings. Representative rule configuration is shown below.

<details>
<summary><b>View high-speed stack-up, impedance and rule configuration</b></summary>

### Layer stack

<p align="center">
  <img src="Images/Design_Rules/01_Layer_Stack.PNG" alt="4-layer PCB stack-up" width="850">
</p>

### Controlled-impedance profiles

<p align="center">
  <img src="Images/Design_Rules/02_Impedance_Profiles.png" alt="USB and Ethernet impedance profiles" width="850">
</p>

### Net classes

<p align="center">
  <img src="Images/Design_Rules/03_Net_Classes.png" alt="Altium net classes" width="850">
</p>

### Differential-pair routing rules

<p align="center">
  <img src="Images/Design_Rules/05_Differential_Pair_Routing_Rules.png" alt="Differential pair routing rules" width="850">
</p>

### Matched-length rules

<p align="center">
  <img src="Images/Design_Rules/10_Matched_Length_Rules.png" alt="Matched length rules" width="850">
</p>

</details>

## Repository Contents

```text
Hardware/Altium/   Editable Altium schematic and PCB source
Docs/              Schematic and fabrication PDFs
Images/            PCB, schematic and selected design-rule images
Manufacturing/     Rev A Gerber X2 and NC Drill fabrication package
```

I have intentionally kept the public repository concise so the design can be reviewed quickly, while the editable Altium sources remain available for deeper technical inspection.

---

**Designed by Caoilte Donohoe**
