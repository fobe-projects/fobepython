The steps below let you create and install the firmware file. For
a .uf2 type file taken from the MicroPython downloads source only
step 4 is needed. For the .hex version of the firmware file, steps
1, 3 and 4 are required.

1. Download and install u2fconv.py. It is available e.g. in the tools
   directory of MicroPython.

2. Create a firmware for the FoBE Quill nRF52840 Mesh if needed, with the command

   `make BOARD=FOBE_QUILL_NRF52840_MESH -j8`

   in the directory build-FOBE_QUILL_NRF52840_MESH-s140. The firmware file will have the
   name firmware.uf2.

3. Create the .uf2 file if needed in the build directory with the command:

   `uf2conv.py -c -f 0xADA52840 -o firmware.uf2 firmware.hex`

   It must report the start address as 0x27000. If you omit the -o option,
   the output file will have the name flash.uf2.

4. Enable the upload mode by pushing reset twice or calling
   machine.bootloader() and copy the file firmware.uf2 to the board drive,
   which will pop up on your PC.

In case the FoBE Quill nRF52840 Mesh bootloader is lost or overwritten, it can be found
at https://github.com/fobe-projects/fobe-nrf52-arduino.git in different
formats. Using a JLINK adapter or interface, it can be uploaded as hex version.
The bootloader is as well available through the Arduino IDE.

