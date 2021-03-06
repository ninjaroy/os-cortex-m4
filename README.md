Introduction
============
A small operating system on STM32F429 Discovery. Still in early development.

Build Instructions
==================

* [OpenOCD](http://openocd.sourceforge.net/)
```
    git clone git://git.code.sf.net/p/openocd/code openocd
    cd openocd
    ./bootstrap
    ./configure --prefix=/usr/local \
        --enable-stlink
    echo -e "all:\ninstall:" > doc/Makefile
    make
    sudo make install
```
* [GNU Tools for ARM Embedded Processors](https://launchpad.net/gcc-arm-embedded)
```
    apt-get install gcc-arm-none-eabi
```
If you encounter the problems of missing packages, try to execute the
following commands in advance:
```
    sudo add-apt-repository ppa:terry.guo/gcc-arm-embedded
    sudo apt-get update
```

In addition, you need to download [STM32F429I-Discovery firmware](http://www.st.com/web/en/catalog/tools/PF259429)
and extract it to the toplevel directory where `stm32f429-r3d` exists.

```
    unzip stsw-stm32138.zip
```

Then, get the latest source from GitHub and then build:
```
    git clone https://github.com/jserv/stm32f429-r3d
    cd project
    make
```

Please confirm STM32F429 Discovery is properly connected to USB, and let's flash the device:
```
    make flash
```

Be patient when OpenOCD is flashing.

Debug
=====
```
    make debug
    arm-none-eabi-gdb --eval-command="target remote :3333" project.elf
```

Note on VSCode
==============
If use VS Code for development, complete environment has been prepared for you. You might need to change some settings in c_cpp_properties.json
