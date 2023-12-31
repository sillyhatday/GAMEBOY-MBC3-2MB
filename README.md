# GAMEBOY-FLASHCART-MBC3-2MB

## MBC3 based Gameboy flashcart using FRAM. Final version tested and working

Using footprints from https://github.com/HDR Be sure to check out their designs as well.

This is a working Gameboy flash cartridge. I've made a few different types of cartridges, but thought this would be the most popular due to being compatible with the InsideGadgets GBxCart RW.

This uses FRAM to preserve game saves when the backup battery eventually dies. The battery is only needed to keep the real time clock running. Battery failure will only ruin the games clock, which in pokemon games are able to be reset upon boot after a failure. The clock system uses much more power than just keeping information saved in SRAM.

![Gameboy MBC3 Cart V2 0 Front](https://github.com/sillyhatday/GAMEBOY-FLASHCART-MBC3-2MB/assets/65309612/cc5ee666-9f06-434c-87f0-f232f6a9f846)
![Gameboy MBC3 Cart V2 0 Back](https://github.com/sillyhatday/GAMEBOY-FLASHCART-MBC3-2MB/assets/65309612/e5bc61fd-ddb7-4291-ba2f-46ccb9bd910c)
![IMG_5675](https://github.com/sillyhatday/GAMEBOY-FLASHCART-MBC3-2MB/assets/65309612/5128a3c5-a692-4713-9426-b49466c5832b)
![IMG_5672](https://github.com/sillyhatday/GAMEBOY-FLASHCART-MBC3-2MB/assets/65309612/8d694206-e6dc-48d0-b54f-b6b2889acf9e)

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

## EEPROM 29F016B

I've found them available from Aliexpress very easily. Lately the prices of these have risen. Once available for about £1 per chip are not £1.60 per chip. These are a 16-bit address and 8-bit data bus EEPROM. The write enable pin is brought to the audio pin on the Gameboy cartridge header. This is compatible with the GBxCart RW. The pin is held to 5v to keep it disabled during usage through a pullup resistor. You can buy 0603 spec 10k resistors or reuse the resistor on an original Nintendo doner PCB. I've not seen any need for this pull up resistor, but I can see it will cause a problem down the line somehow without it. 70 hours into Pokemon Yellow I wouldn't want the EEPROM to get corrupted and loose your save. I'm not sure if the audio pin is held low by the Gameboy, I think it is, so likely there isn't a need for it. You can omit it if you like. You'll save 500uA of current usage.

## SRAM FM18W08

The SRAM isn't SRAM, its the modern FRAM that was made to replace battery backed SRAM in industrial PLC applications (among other things I'm sure). Once more Aliexpress has these in a small supply. These are the most expensive part of building this, apart from the donor MBC5 chip, depends on where you get the MBC5. The FRAM is available on eBay but the prices are egregious. You can get quality versions of the FRAM from reputable suppliers like Mouser and Digikey. The FM1808, FM18W08, FM1808B and FM18L08 all work in this desgin. FM1808 and the FM18L08 are out of production, so any you find will be old stock or poor copies. Bear in mind that the L version is a 3.3v part that is able to stand an extreme of 5v at its input, so I don't suggest using that if possible.

So in my tinkering with all this, I can suggest that you spend £12 per chip for a quality item. Aliexpress and eBay are full of either copies or factory rejected parts. You can find them for around £2 per chip and you get junk. In a batch of 5 from Aliexpress, none of them worked. From another batch, I went through 4 before finding a working one. In the end I went through 8 chips before getting one that works. So 9 chips x £2 is £18 for one working chip. Better off spending the £12 for one.

## MBC3, BA6129AF

You will need to find these from an exsisting game. These are tougher to find over the MBC5, due to them only being used in games that used real time clock functionality. So far I have got two from a Japanese version of Hamtaro. I see that the USA can get cheap versions of Mary-Kate and Ashley games to source parts from. You'll likely want to use this to play versions of Pokemon that make use of the real time clock, such as Silver, Gold and Crystal along with any ROM hacks. In theory these are compatible with all MBC1 and 5 games. That is not the case but certainly some of those games can be used on this too.

### MBC3 Type

*The following section I have copied from https://github.com/MouseBiteLabs the Bucket Mouse. Please check out their work. I started a table and I'm unsure if they used some of my values in this one, but they can have all the credit for it. I've just slightly modified it to be more suitable to my project*

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

*Take away 0.05uA for SRAM current usage in Bucket Mouse testing method. We are using FRAM here and it's power supply is not connected to the battery.*

## 74LVC1G332GW

This OR gate is needed to allow games to be saved properly. Some MBC1 and 99% of MBC5 do not require it. Due to the MBC3 controlling the write access to the FRAM, the correct write pulses aren't done. This doesn't effect SRAM but is not compatible with FRAM.

## Change Log

18/09/2023

Moved FRAM power pin from battery to cartridge VCC. No point keeping FRAM powered at all, it's just wasting battery power. 6.3uA current draw to 4.3uA 

16/06/23

Tidied up readme a bit and a minor PCB revision. Updated battery holder footprint and added a version without JLC markings. You know what to do.

19/04/23

Finished readme.

18/04/23

Initial release V1.1 of gerbers. Readme unfinished.
