# sample project for Arduino on Meson

A sample for making C code for Arduino based on my ATMmega328PB sample
Tested on knock-off Arduino with stock firmware, acts the same as a regular
Arduino

## Instructions:
The whole thing depends on the cross compilation file to be set up properly,
if you use anything other than the ATmega328P, you'll need to change the file
to the right MCU in the `-mmcu=` flag and reconfigure meson/re-setup meson

after that, all sources that must be build will be in `src` with  a `meson.build`
returning `sources` there, add to it for anything else necessary

In the main `meson.build` there is the required things to build the final elf and
flash it with a custom target, the relevant options are:

- programmer
    what programmer protocol should be used by avrdude, default is `arduino`
- processor
    What processor will avrdude try to flash to, default is `m328p` 
    The port avrdude will try to communicate over, `/dev/ttyUSB0` is the default, change as necessary
- memory
    What memory part will avrdude try to flash to, `flash` is the default

### Building:
The project comes with a simple blink program in `src/main.c`
`meson compile` will build the program
`meson compile flash` will flash the program and rebuild if necessary

Really, that's it! should be easily expansible if you need any more

## Changelog
[changelog.md]
