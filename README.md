# GAMEBOY-FLASHCART-MBC3-2MB
MBC3 based Gameboy flashcart using FRAM

Using footprints from https://github.com/HDR Be sure to check out their designs as well.

This is a working Gameboy flash cartridge. I've made a few different types of cartridges, but thought this would be the most popular due to being compatible with the InsideGadgets GBxCart RW.

This uses FRAM to preserve game saves when the backup battery eventually dies. The battery is only needed to keep the real time clock running. Battery failure will only ruin the games clock, which in pokemon games are able to be reset upon boot after a failure. The clock system uses much more power than just keeping information saved in SRAM.

![Gameboy MBC3 Cart Front](https://user-images.githubusercontent.com/65309612/233170648-b1a93514-2ca5-401a-8317-f28b5eb1a6b6.jpg)
![Gameboy MBC3 Cart Back](https://user-images.githubusercontent.com/65309612/233170666-66f15a34-23f5-46ab-b77b-153c60b77e46.jpg)
![20230419_194524](https://user-images.githubusercontent.com/65309612/233172349-abfa717a-c454-454d-86bf-366a7aec2b89.jpg)

**Parts List**

Battery Holder: Plastic low profile holder from Aliexpress

C1, C2: 15pF 0603

C3, C4, C5, C6: 100nF 0603

R1: 1K 0603

R2: 330K 0603

R3: 10K 0603

U1: BA612AF or whatever chip that is to be taken from your MBC3 cartridge

U2: MBC3

U3: 74LVC1G332W TSOP Sourced loads for cheap on Aliexpress

U4: 29F016

U5: FM1808 or FM10W08 or FM18L08

Y1: Crystal from donor cart

You can reuse the passives from the donor cart to save buying all of them.

**EEPROM AM29F016B**

I've found them available from Aliexpress very easily. Lately the prices of these have risen. Once available for about £1 per chip are not £1.60 per chip. These are a 16-bit address and 8-bit data bus EEPROM. The write enable pin is brought to the audio pin on the Gameboy cartridge header. This is compatible with the GBxCart RW. The pin is held to 5v to keep it disabled during usage through a pullup resistor. You can buy 0603 spec 10k resistors or reuse the resistor on an original Nintendo doner PCB. I've not seen any need for this pull up resistor, but I can see it will cause a problem down the line somehow without it. 70 hours into Pokemon Yellow I wouldn't want the EEPROM to get corrupted and loose your save. I'm not sure if the audio pin is held low by the Gameboy, I think it is, so likely there isn't a need for it. You can omit it if you like. You'll use 500uA of current usage.

**SRAM FM18W08**

The SRAM isn't SRAM, its the modern FRAM that was made to replace battery backed SRAM in industrial PLC applications (among other things I'm sure). Once more Aliexpress has these in a small supply. These are the most expensive part of building this, apart from the donor MBC5 chip, depends on where you get the MBC5. The FRAM is available on eBay but the prices are egregious. You can get quality versions of the FRAM from reputable suppliers like Mouser and Digikey. The FM1808, FM18W08, FM1808B and FM18L08 all work in this desgin. FM1808 and the FM18L08 are out of production, so any you find will be old stock or poor copies. Bear in mind that the L version is a 3.3v part that is able to stand an extreme of 5v at its input, so I don't suggest using that if possible.

So in my tinkering with all this, I can suggest that you spend £12 per chip for a quality item. Aliexpress and eBay are full of either copies or factory rejected parts. You can find them for around £2 per chip and you get junk. In a batch of 5 from Aliexpress, none of them worked. From another batch, I went through 4 before finding a working one. In the end I went through 8 chips before getting one that works. So 9 chips x £2 is £18 for one working chip. Better off spending the £12 for one.

**MBC3, BA6129AF**

You will need to find these from an exsisting game. These are tougher to find over the MBC5, due to them only being used in games that used real time clock functionality. So far I have got two from a Japanese version of Hamtaro. I see that the USA can get cheap versions of Mary-Kate and Ashley games to source parts from. You'll likely want to use this to play versions of Pokemon that make use of the real time clock, such as Silver, Gold and Crystal along with any ROM hacks. In theory these are compatiblw with all MBC1 and 5 games. That is not the case but certainly some of those games can be used on this too.

**74LVC1G332GW**

This OR gate is needed to allow games to be saved properly. Some MBC1 and 99% of MBC5 do not require it. Due to the MBC3 controlling the write access to the FRAM, the correct write pulses aren't done. This doesn't effect SRAM but is not compatible with FRAM.

19/04/23

Finished readme.

18/04/23

Initial release V1.1 of gerbers. Readme unfinished.
