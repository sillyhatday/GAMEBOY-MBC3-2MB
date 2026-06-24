# GAMEBOY-FLASHCART-MBC3-2MB

## Introduction

This is a Gameboy flash cartridge. This uses FRAM to preserve game saves. The battery is only needed to keep the real time clock running.

Requires original donor cartridge.

>[!TIP]
>Compatible with GBxCart and FlashGBX

## Photos:

<img width="400" height="412" alt="mbc3render" src="https://github.com/user-attachments/assets/5e55a523-1d50-40e4-b8dc-c30ccc9459b9" />
<img width="400" height="267" alt="mbc3build" src="https://github.com/user-attachments/assets/0d381152-27e1-4f6c-a4af-707228583e96" />
<img width="400" height="267" alt="mbc3build2" src="https://github.com/user-attachments/assets/4c76036c-c65d-44a1-a3bb-95c3b32a08e7" />

>[!IMPORTANT]
>Be sure to order PCB in 0.8mm thickness with gold plating.

| Parts List | Quantity | Donor Salvage |
| --- | --- | --- |
| 15pF Cap 0603 | 2 | Yes |
| 100nF Cap 0603 | 4 | Yes |
| 1K Res 0603 | 1 | Yes |
| 330K Res 0603 | 1 | Yes |
| 10K Res 0603 | 1 | No |
| BA6129A or MM134A | 1 | Yes |
| MBC3 | 1 | Yes |
| 74LVC1G332W | 1 | No |
| 29F016 | 1 | No |
| FM1808 or FM10W08 or FM18L08 | 1 | No |
| 32.768 kHz Quartz Oscillator | 1 | Yes |

>[!NOTE]
>For information on parts not mentioned below, refer to [MY OTHER PROJECT](https://github.com/sillyhatday/GAMEBOY-MBC5-2MB)

### MBC3, BA6129AF

You will need to find these from an exsisting game. MBC3 games are less common and more expensive than their counterparts. Japanese Hamtaro games were a good place to get donor parts cheaply. The SRAM managment chip has modern soloutions but may as well just use the one from the donor.

### MBC3 Type

*The following section I have copied from https://github.com/MouseBiteLabs the Bucket Mouse with their permission. Please check out their work. I started a table and I'm unsure if they used some of my values in this one, but they can have all the credit for it. I've just slightly modified it to be more suitable to my project*

The MBC3 chip you use from the donor cartridge can be one of a few different types:

![mbc3](https://github.com/sillyhatday/GAMEBOY-FLASHCART-MBC5-2MB/assets/65309612/83c6f545-b811-4e65-b120-140bcd1276f3)

[Images of MBC3 chips from Game Boy Hardware Database.]

Current Draw Measurements
The revision of MBC3 chip you are using will influence the current draw out of the battery when the game is off, and thus how long your battery life will last. Using the real-time clock function on the MBC3 will draw more current than if you do not.

For the test set up, I am replacing the battery with a regulated DC power supply set for 3 VDC for consistency, on a cart board with an MM1134 chip for U4, and brand new AS6C62256 SRAM. The "no RTC" measurements have Z1 (or C3) shorted, and the "with RTC" measurements have R2, C2, Z1, and X1 populated. I am using a Fluke 117 Multimeter in DC mV mode for measurements.

| Rev |	P/N |	Current draw (without RTC) |	Battery Life Estimate (no RTC, CR2025) |	Current draw (with RTC) |	Battery Life Estimate (RTC, CR2025) |	Battery Life Estimate (RTC, CR2032) |
|----|----|----|----|----|----|----|
| MBC3 |	LR385364 |	0.2 uA |	>50 years |	1.8 uA |	10 years |	14 years |
| MBC3 |	BU3631K |	0.6 uA |	31 years |	1.6 uA |	12 years |	16 years |
| MBC3 |	P-1 |	0.4 uA |	47 years |	3.8 uA |	5 years |	7 years |
| MBC3A |	LR38536B |	0.2 uA |	>50 years |	1.5 uA |	13 years |	18 years |
| MBC3A |	BU3632K |	0.5 uA |	37 years |	1.5 uA |	13 years |	18 years |
| MBC3A |	P-2 |	0.5 uA |	37 years |	3.9 uA |	5 years |	7 years |
| MBC3B |	BU3634K |	0.6 uA |	31 years |	1.5 uA |	13 years |	18 years |
| MBC3B |	P-2 |	0.4 uA |	47 years |	3.7 uA |	5 years |	7 years |

>[!IMPORTANT]
>Take away 0.05uA for SRAM current usage in Bucket Mouse testing method. We are using FRAM here and it's power pin is not connected to the battery.*

## Change Log

| Date | Notes |
| ---- | ---- |
| 24/06/2026 | Coming back to tackle this mess |
| 18/09/2023 | Moved FRAM power pin from battery to cartridge VCC. No point keeping FRAM powered at all, it's just wasting battery power. 6.3uA current draw to 4.3uA |
| 16/06/2023 | Tidied up readme a bit and a minor PCB revision. Updated battery holder footprint and added a version without JLC markings. You know what to do. |
| 19/04/2023 | Finished readme. *That was a lie* |
| 18/04/2023 | Initial release of v1.1 gerbers |

## License

This work is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you must give appropriate credit, provide a link to the license, and indicate if any changes were made.
