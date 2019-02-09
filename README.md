# ESP32-PICO-V4 Eagle Socket Library

## UNTESTED ON A REAL BOARD - USE AT YOUR OWN RISK

## Why?

The [ESP32-Pico-V4 Board](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/get-started-pico-kit.html) is
about [$8 at DigiKey](https://www.digikey.com/product-detail/en/espressif-systems/ESP32-PICO-KIT/1904-1030-ND/9381703?utm_adgroup=RF%20&%20RFID) making it a fabulous, cheap, easy to use compute daughterboard for projects.

## Why Not the ESP32 Thing from SparkFun?

I have one of [these](https://www.sparkfun.com/products/13907) boards too, but they are $21 not $8.  Also, as a daughterboard you probably don't need the battery charging circuit, and they use a 26MHz main crystal frequency, not 40MHz like the PICO-V4.

## Actual Physical Parts - WARNING

The board mounts on a 2x20 header pair 0.7in apart.  The "bottom" 3 pins on each side are not populated (bottom is where the antenna is, top is where the USB Connection is).  I had a hard time finding 1x20 headers but finally found some from (Pheonix Enterprises)[https://www.peconnectors.com/female-headers-pcb-1x-row-.100/hws15775/] for $0.68 (x1).

**WARNING** 

Got the real boards back and the drill holes are too small for the part I chose - or the other way around, 
the part pins are too big for the drill holes.  I'll be fixing this part soon.  For my prototype boards I am going 
to hand-cut single row female headers to fit.  My next run of boards I'll fix it correctly.

**WARNING**

## Power Supply Considerations

The [Reference Material](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/get-started-pico-kit.html#power-supply-options) cautions against powering the board simultaneously from the USB port and an external 3V3 source.  However, there's
likely insufficient headroom 3V3 current from the onboard AMS1117 regulator to power any offboard devices.  My solution is to add
a solid state normally-closed relay driven from the EXT_5V line.  The relay connects the motherboards 3V3 to PICO-V4's VDD33 
input.  That line will only be powered from the USB, so when it's plugged in it will drive the relay open, isolating the PICO-V4.
The relay I'm using currently is the [Panasonic AQY412SX](https://www.digikey.com/products/en?keywords=255-6088-1-ND).

## License

This part may be freely used under the terms of the [Creative Commons License](https://creativecommons.org/licenses/by-sa/4.0/legalcode).

