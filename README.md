# libopencm3-proj-template
project template for stm32F103XXX Microcontrollers using meson build system.


## how to use it

Modify `meson.build` according to your needs.  

`libocm3Path` - libopencm3 directory path  
`srcfiles` - define source files here.

You need to issue `./build.sh` for once.
 ```shell
$ ./build.sh  
$ cd builddir
```
ninja - generates elf file.  
```shell
$ ninja 
``` 

ninja hex - generates hex file.  
```shell
$ ninja hex
```
ninja size - gives the summary of hex file size.  
```shell
$ ninja size
```
ninja upload - upload hex file to stm32 via stlink programmer.  
```shell  
$ ninja upload  
```
ninja reset - reset the stm32 mcu.  
```shell
$ ninja reset
```

A typical working example:
```shell
[ami@aarav libopencm3-proj-template]$ ./build.sh
The Meson build system
Version: 0.44.0
Source dir: /home/ami/repos/libopencm3-proj-template
Build dir: /home/ami/repos/libopencm3-proj-template/builddir
Build type: cross build
Project name: stm32f1-project
Native C++ compiler: c++ (gcc 7.2.1)
Cross C++ compiler: arm-none-eabi-g++ (gcc 7.2.0)
Host machine cpu family: x86_64
Host machine cpu: x64
Target machine cpu family: stm32
Target machine cpu: STM32F1
Build machine cpu family: x86_64
Build machine cpu: x86_64
Program arm-none-eabi-size found: YES (/bin/arm-none-eabi-size)
Program arm-none-eabi-objcopy found: YES (/bin/arm-none-eabi-objcopy)
Program st-info found: YES (/bin/st-info)
Program st-flash found: YES (/bin/st-flash)
Library opencm3_stm32f1 found: YES
Message: Found libopencm3 library at /home/ami/repos/libopencm3
Message: cross compiling for cortex-m3
Message:
                  ninja - generates elf file.
                  ninja hex - generates hex file.
                  ninja upload - upload hex file to stm32 via stlink programmer.
                  ninja probe - probe stlink programmer.
                  ninja size - gives the summary of hex file size.
                  (C) Amitesh Singh
Build targets in project: 5
Found ninja-1.8.2 at /bin/ninja
[ami@aarav libopencm3-proj-template]$ cd builddir/
[ami@aarav builddir]$ ninja
[2/2] Linking target blink.
[ami@aarav builddir]$ ninja hex
[0/1] Running external command hex.
[ami@aarav builddir]$ ninja size
[2/3] Running external command size.
   text    data     bss     dec     hex filename
   1216      12       0    1228     4cc /home/ami/repos/libopencm3-proj-template/builddir/blink
[ami@aarav builddir]$ ninja upload
[0/1] Running external command upload.
st-flash 1.4.0
2017-12-28T00:04:00 INFO src/common.c: Loading device parameters....
2017-12-28T00:04:00 INFO src/common.c: Device connected is: F1 Medium-density device, id 0x20036410
2017-12-28T00:04:00 INFO src/common.c: SRAM size: 0x5000 bytes (20 KiB), Flash: 0x10000 bytes (64 KiB) in pages of 1024 bytes
2017-12-28T00:04:00 INFO src/common.c: Attempting to write 1228 (0x4cc) bytes to stm32 address: 134217728 (0x8000000)
Flash page at addr: 0x08000400 erased
2017-12-28T00:04:00 INFO src/common.c: Finished erasing 2 pages of 1024 (0x400) bytes
2017-12-28T00:04:00 INFO src/common.c: Starting Flash write for VL/F0/F3/F1_XL core id
2017-12-28T00:04:00 INFO src/flash_loader.c: Successfully loaded flash loader in sram
  2/2 pages written
2017-12-28T00:04:00 INFO src/common.c: Starting verification of write complete
2017-12-28T00:04:00 INFO src/common.c: Flash written and verified! jolly good!

```
