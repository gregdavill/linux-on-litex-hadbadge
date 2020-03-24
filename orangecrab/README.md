# Linux On Litex Vexriscv
OrangeCrab edition
 

-----

## Steps:

Press button on OrangeCrab and insert USB connection, this will start the OrangeCrab with the bootloader active.

Load ECP5 bitstream @ 0x00080000 (VexRiscv + Litex BIOS + emulator + rootfs + devicetree)
Note this will take a little while to load
```sh 
dfu-util -d 1209:5bf0 -D ecp5_flash_image.bin
```
There is a bug in the packing of bitstream into the image above, so for new we'll reload just the FPGA bitsteam.
```sh 
dfu-util -d 1209:5bf0 -D ecp5_compress_qspi_38.8M.bit
```



OrangeCrab will now restart automatically.

You should see a new ttyACM appear under dmesg. Note UART is blocked until a connection to the ttyACM is established.

Connect to it
```sh
lxterm /dev/ttyACM0
```