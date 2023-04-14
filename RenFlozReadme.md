# Readme for the RenFloz Ender-3

## Printer data

```
CPU: STM32F103RCT7

# cat ./Marlin/src/core/boards.h | grep BTT_SKR_MINI_E3_V2_0
BOARD: BOARD_BTT_SKR_MINI_E3_V2_0

# cat Marlin/src/pins/pins.h | grep BTT_SKR_MINI_E3_V2_0
env: STM32F103RC_btt

steppers: TMC-2209
```

## Firmware

### Building

```
pio run -e STM32F103RC_btt
```

### Flashing

```
# Copy the firmware.bin on SD-card
cp .pio/build/STM32F103RC_btt/firmware.bin /media/flozzone/6261-B653

# Remove the FIRMWARE.CUR file to upgrade with new firmware
# Don't know if this is actually really needed, have to figure out
rm /media/flozzone/6261-B653/FIRMWARE.CUR

# Savely remove the SD-card or sync
sync

# Put the SD-card into the printer and reboot
```

## Slicer

Currently we are working with the Cura Slicer. Prusa slicer should be slightly better, a print-nerd told me ;)

### Initial G-Code

There might be the need for special G-Code to be entered in the slicer to start up out printer. This
is the place where we will collect them.

## Roadmap

### Octoprint on a RaspberryPI

Octoprint is a print server where the printer is connected to. It accepts sliced gcode over WiFi or
LAN.

Advantages:

* No SD-card handling all the time
* Direct printing from the slicer
* Provides ability to connect a camera

### Printer Enclosure

Advantages:

* Keep dust away from printer
* Raise print area temperature to printing temperature. Improves bed adhesion.
* Safer transportation, especially if printer is moved from home to home.
* Allows to build a storage box underneath the printer
* Allows to keep the power supply and controller to be cooled from outside the print area,
  since the heated print area would heat up the electronics too.
* Lower the noise from the printer
* Filament spool can be mounted on the enclosure

Disadvantages:

* It will be heavier
* It will be bigger: Taller for the storage box and slightly wider and deeper to fit the printer.

Points to consider when building:

* It should be possible to easily take out the printer from the enclosure for modifications
* The display should be reachable from outside the print area, since it should stay closed
  while printing to keep up with the temperature.
