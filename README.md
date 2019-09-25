# lr-atari800-individualconfiguration-helper
 Helper files for the lr-atari800 port showing the usage of individual configuration files on the rpi.

## 1. Core option atari800_individualconfiguration must be set to "enabled"

To achive this the shell script

  `lr-atari800-rpi-1-set-core-options.sh`

can be used (or taken as an assumption).

In addition to enabling the option atari800_individualconfiguration it sets all other
core options, that are used in the emulator initialization process.

The following values will be set:
```
  atari800_artifacting = "disabled"
  atari800_cassboot = "disabled"
  atari800_individualconfiguration = "enabled"
  atari800_internalbasic = "disabled"
  atari800_keyboard = "poll"
  atari800_ntscpal = "NTSC"
  atari800_opt1 = "disabled"
  atari800_opt2 = "disabled"
  atari800_resolution = "336x240"
  atari800_sioaccel = "enabled"
  atari800_system = "400/800 (OS B)"
```

## 2. Individual emulators have to be defined

For this the shell script

  `lr-atari800-rpi-2-copy-emulators-config.sh`

might be used.

The provided file "emulators.cfg" will replace the default atari800 "emulators.cfg" file.
The content of the provided "emulators.cfg" might also be taken only as an assumption.

## 3. Individual emulators are needed to give each emulator its own configuration file

Building required emulators can be done using

  `lr-atari800-rpi-3-build-lr-emulators.sh`

This will copy the existing "atari800_libretro.so" emulator to get the needed differentiation.

For example (to get an idea):
```
  lr-atari800.so (will be used for an Atari 800 48KB NTSC machine without BASIC and without artifacting)
  lr-atari800-artifact-bb1.so (will be used for an Atari 800 48KB NTSC machine without BASIC and with artifacting brown/blue 1 enabled)
  lr-atari800-pal.so (will be used for an Atari 800 48KB PAL machine without BASIC and without artifacting)
  lr-atari800xl.so (will be used for an Atari 800 XL 64KB NTSC machine without BASIC and without artifacting)
  lr-atari800xl-pal-artifact-simple.so (will be used for an Atari 800 XL 64KB PAL machine without BASIC and with simple PAL artifacting)
```
  ... and so on.

## 4. Individual configfiles are needed. Each configfile has to match exactly the appropriate emulator name plus the file extension ".cfg"

This can be achieved be using the script:

  `lr-atari800-rpi-4-copy-configfiles.sh`

It just copies all files in the folder "/configfiles" to the required rpi config folder.
It is recommended to take the configfiles just as an assumption.

This configfiles display my personal configuration.
Personal changes have to be done for the following (and for every file!):

- concerning personal used (and installed) BIOS files (which reflect the following entries):
```
  ROM_OS_A_NTSC=/home/pi/RetroPie/BIOS/Atari OS Rev A (1979) (Atari) (NTSC) (400-800).rom
  ROM_OS_A_PAL=/home/pi/RetroPie/BIOS/ATARIOSA.ROM
  ROM_OS_B_NTSC=/home/pi/RetroPie/BIOS/Atari REVBNTSC.ROM
  ROM_OS_AA00R10=/home/pi/RetroPie/BIOS/Atari 1200xL.rom
  ROM_OS_AA00R11=
  ROM_OS_BB00R1=/home/pi/RetroPie/BIOS/Atari 600XL.rom
  ROM_OS_BB01R2=/home/pi/RetroPie/BIOS/ATARIXL.ROM
  ROM_OS_BB02R3=
  ROM_OS_BB02R3V4=/home/pi/RetroPie/BIOS/Atari 1450R3VX.ROM
  ROM_OS_CC01R4=
  ROM_OS_BB01R3=/home/pi/RetroPie/BIOS/Atari 800XE.rom
  ROM_OS_BB01R4=/home/pi/RetroPie/BIOS/Atari XEGS.rom
  ROM_OS_BB01R59=
  ROM_OS_BB01R59A=
  ROM_5200=/home/pi/RetroPie/BIOS/5200.rom
  ROM_5200_A=
  ROM_BASIC_A=/home/pi/RetroPie/BIOS/Atari Basic rev A.rom
  ROM_BASIC_B=/home/pi/RetroPie/BIOS/Atari Basic rev B.rom
  ROM_BASIC_C=/home/pi/RetroPie/BIOS/ATARIBAS.ROM
  ROM_XEGAME=
  ROM_400/800_CUSTOM=/home/pi/RetroPie/BIOS/ATARIOSB.ROM
```

- concerning personal used external colour palette (which reflect the following entries):
```
  COLOURS_NTSC_EXTERNAL_PALETTE=/opt/retropie/configs/atari800/act/Real.act
  COLOURS_NTSC_EXTERNAL_PALETTE_LOADED=1
  COLOURS_NTSC_ADJUST_EXTERNAL_PALETTE=1
```
  and/or
```
  COLOURS_PAL_EXTERNAL_PALETTE=/opt/retropie/configs/atari800/act/Real.act
  COLOURS_PAL_EXTERNAL_PALETTE_LOADED=1
  COLOURS_PAL_ADJUST_EXTERNAL_PALETTE=1
```
All other values are set appropriate as needed.
