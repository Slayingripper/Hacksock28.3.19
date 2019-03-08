# Hacksock28.3.19

## Prerequisites 
any linux distro (ubuntu shell on windows is fine) 
Raspberry pi
Pifm (LIBARY)
Putty
Arduino IDE 


## Transmiting FM signals from a raspberry pi 
Firstly lets do a git clone of the PiFm libary
```
git clone https://github.com/rm-hull/pifm.git
```

```
cd pifm
```

It uses the hardware on the raspberry pi that is actually meant to generate spread-spectrum clock signals on the GPIO pins to output FM Radio energy. This means that all you need to do to turn the Raspberry-Pi into a (ridiculously powerful) FM Transmitter is to plug in a wire as the antenna (as little as 20cm will do) into GPIO pin 4 and run the code posted below.

The python library calls a C program. The C program maps the Peripheral Bus (0x20000000) in physical memory into virtual address space using /dev/mem and mmap. To do this it needs root access, hence the sudo. Next it sets the clock generator module to enabled and sets it to output on GPIO4 (no other accessible pins can be used).

Modulation is done by adjusting the frequency using the fractional divider between 103.325Mhz and 103.275Mhz, which makes the audio signal.

## Expanding on this idea 
```
https://github.com/F5OEO/rpitx
```
