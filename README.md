# Linux On Litex Vexriscv
HADbadge edition
 

-----

## Steps:

Load ECP5 bitstream @ 0x00000000 (CART) (VexRiscv + Litex BIOS)
```sh 
dfu-util -d 1d50:614b -a 2 -D ecp5_compress_qspi_38.8M.bit
```

Load Linux @ 0x00200000 (CART) (Image, emulator, etc)
```sh
dfu-util -d 1d50:614b -a 4 -D flash_image.bin
```


Reboot hadbadge, boot ECP5 bitstream from cartridge using IPL.

You should see a new ttyACM appear under dmesg. Note UART is blocked until a connection to the ttyACM is established.

Connect to it
```sh
screen /dev/ttyACM0
```