# Arduino-Controller-for-Upfitter-Switches
Finally got around to 'properly' wiring the upfitter switches to a microcrontroller setup in the tool box. Have 2AWG wire going from battery to jump posts in the back for solid power that will go to a large air compressor in the back powered by a 2000W power inverter. The upfitter switches run to the tool box straight from the 10 or 20A leads through a nice Deutsch connetor onto a breadboard. Theyre then regulated to 12V, 10000 ohm resistor to drop more over to a 2N2222 transistor that pulls 4 arduino pins to ground. These arduino pins are programmed as pull up resistors. Arduino and breadboard have common power from a 5v voltage regulator in attempts to not brick another ATMEGA328P and its bootloader. Pins 8/9 output to a 2 way DC motor controller controlling the cutout exhaust. 



This infrastructure is so robust so that it can eventually control the air compressor as mentioned, multiple lights, train horn, etc. The modularity is also key in that I can add bluetooth, special programming for flashing lights, and much more through just some simple code updates whenever I want. 



Right now i've confirmed that the whole system works save the resistors and on through the Arduino: mostly because i'm waiting on the new Arduino board to come in the mail. Still need to decide how I want the programming to be done to open the exhaust. Some problems ive come across are that the LVD that powers the arduino has constant power and if the upfitter switch is on, sending power, and the truck is shut off, it will look to the arduino as if the upfitter switch has been shut off, triggering a close of the cutout. This isnt the biggest problem but definately not ideal. The solution that I am considering the most is stealing a button input from the steering wheel as the cutout exhaust controller as a button is much better for this type of function than a switch. 



When the new Arduino comes in the mail later I plan to reburn the bootloader to a few of the microcontrollers that i have so when i inevitably brick another one, I have more backups. Or maybe the system will work as intended now and hopefully not brick another one, only time will tell.



After those problems are sorted, I need to cut out a spot in the tool box and mount my relay switch box. This is going to take a lot of wiring, which im not really looking forward to, especially considering that I still have no use for it. Maybe when I get some lights ill get some more motivation to wire the relays up.



