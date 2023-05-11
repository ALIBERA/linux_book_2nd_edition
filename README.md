 # linux_book_2nd_edition
Linux Driver Development for Embedded Processors 2nd Edition

The source code of the drivers and device tree for NXP i.MX7, Microchip SAMA5D27 and Broadcomm BCM2837 processors can be downloaded from drivers_source_code.zip. These drivers have been implemented using the v4.9 LTS kernel. The evaluation boards and their configurations used to develop these drivers are explained in detail throughout this book.

The source code of the drivers and device tree for SAMA5D27-SOM1 (SAMA5D27 System On Module) can be downloaded from linux_4.14_sama5d27-SOM_drivers.zip. These drivers have been implemented using the v4.14 LTS kernel. The ATSAMA5D27-SOM1-EK1 evaluation platform (https://www.microchip.com/developmenttools/ProductDetails/atsama5d27-som1-ek1) has been used for the development of these 4.14 kernel drivers. The Microchip SAMA5D27-SOM1 Practical Labs Setup is described in the Linux_4.14_SAMA5D27-SOM1_practical_labs.pdf file included in this GitHub repository.

Since the end of March 2019, a new chapter and an appendix have been added to the text of the book. These are: Chapter 13, “Linux USB Device Drivers” and Appendix, “Porting Kernel Modules to the Microchip SAMA5D27-SOM1”. These two new chapters can also be downloaded from the Github of this book for readers who have acquired the book before that date. In the USB chapter, you will learn how to create a fully functional USB HID device based on the Microchip PIC32MX microcontroller that will send/receive data to/from a Linux USB Host device based on the Microchip SAMA5D27 processor; several custom Linux USB device drivers will be developed throughout this chapter. The Appendix will explain the hardware settings for the ATSAMA5D27-SOM1-EK1 board that are needed to test the practical labs described throughout this book; to run the labs on this new board, you will get the SAMA5D27-SOM1 Linux drivers based on the kernel 4.14, and the SAMA5D27-SOM1 device tree settings from the Appendix_linux_4.14_sama5d27-SOM_drivers.zip file, which is included in the GitHub repository of this book.

Since the end of November 2019, the Linux drivers included in this book have been adapted to run on the Raspberry Pi 4 Model B board using Linux kernel version 4.19. The kernel 4.19 modules developed for the Raspberry Pi 4 Model B board are included in the linux_4.19_rpi4_drivers.zip file and can be downloaded from this GitHub repository. The Raspberry Pi 4 Practical Labs Setup is described in the Linux_4.9_RaspberryPi4_practical_labs document included in this repository.

Since March 2023 source.codeaurora.org is closed. NXP is migrating from CodeAurora to GitHub. Now, you can find any source code at the following link: https://github.com/nxp-imx

In the page 34 of "Chapter 1: Building the System" you must replace the instruction: 

repo init -u https://source.codeaurora.org/external/imx/imx-manifest -b imx-linux-morty -m imx-4.9.11-1.0.0_ga.xml 

with the new instruction:

repo init -u https://github.com/nxp-imx/imx-manifest -b imx-linux-morty -m imx-4.9.11-1.0.0_ga.xml

The following instructions have been tested on an Ubuntu 16.04 64-bit distribution.

Install python 3.6 in your Ubuntu 16.04 64-bit distribution using the following instructions: 

~$ sudo add-apt-repository ppa:deadsnakes/ppa

~$ sudo apt-get update

~$ sudo apt-get install python3.6

~$ sudo apt install python3-pip

~$ sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1

~$ sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.5 2

~$ sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.6 3

Now, you can use python 2.7, 3.5 and 3.6 in your machine. The default python version is 3.6.

The following code shows how to download the NXP Yocto BSP recipe layers. For this building, a directory called "fsl-release-bsp" is created:

~$ mkdir fsl-release-bsp

~$ cd fsl-release-bsp/

~/fsl-release-bsp$ git config --global user.name "Your Name"

~/fsl-release-bsp$ git config --global user.email "Your Email"

~/fsl-release-bsp$ git config --list

~/fsl-release-bsp$ repo init -u https://github.com/nxp-imx/imx-manifest -b imx-linux-morty -m imx-4.9.11-1.0.0_ga.xml

~/fsl-release-bsp$ repo sync -j4

Before starting the build, it must be initialized:

~/fsl-release-bsp$ DISTRO=fsl-imx-x11 MACHINE=imx7dsabresd source fsl-setup-release.sh -b build_imx7d

Now, replace IMX_FIRMWARE_SRC variable in the recipe "firmware-imx_6.0.bb" with the following line of code to avoid errors during the building:

~$ gedit ~/fsl-release-bsp/sources/meta-fsl-bsp-release/imx/meta-bsp/recipes-bsp/firmware-imx/firmware-imx_6.0.bb

IMX_FIRMWARE_SRC ?= "git://github.com/NXP/imx-firmware;protocol=git"

You have to change the python version from 3.6 to 2.7 to build the image. Execute the following commands and enter 1 (2.7 version):

~$ sudo update-alternatives --config python

You may now build the Linux image:

~/fsl-release-bsp/build_imx7d$ bitbake fsl-image-validation-imx

If you still get errors in the imx-firmware during the building, then execute the following instructions:

~/fsl-release-bsp/build_imx7d$ bitbake firmware-imx -c cleanall

~/fsl-release-bsp/build_imx7d$ bitbake firmware-imx

~/fsl-release-bsp/build_imx7d$ bitbake fsl-image-validation-imx

And this is the new instruction to download the kernel sources:

~$ git clone https://github.com/nxp-imx/linux-imx -b imx_4.9.11_1.0.0_ga

Since the beginning of March 2020, the Linux drivers included in this book have been adapted to run on the NXP i.MX 7Dual MCIMX7SABRE board using Linux kernel v4.19 LTS. The NXP i.MX 7Dual Linux drivers and device tree settings are included in the linux_4.19_imx7_drivers.zip file, which can be downloaded from the Github repository of this book. The NXP i.MX 7Dual Practical Labs Setup is described in the Linux_4.19_i.MX7D_practical_labs document included in this repository.

Since the end of March 2020, the Linux drivers included in this book have been adapted to run on the ST STM32MP1 processor using the STM32MP157C-DK2 board and Linux kernel v4.19 LTS. The ST STM32MP1 Linux drivers and device tree settings are included in the linux_4.19_stm32mp1_drivers.zip file, which can be downloaded from the Github repository of this book. The NXP STM32MP1 Practical Labs Setup is described in the Linux_4.19_STM32MP1_practical_labs document included in this repository.

Since the end of July 2020, the Linux drivers included in this book have been adapted to run on the ST STM32MP1 processor using the STM32MP157C-DK2 board and Linux kernel v5.4 LTS. The ST STM32MP1 Linux drivers and device tree settings are included in the linux_5.4_stm32mp1_drivers.zip file, which can be downloaded from the Github repository of this book. The STM32MP1 Practical Labs Setup is described in the Linux_5.4_STM32MP1_practical_labs document included in this repository. 

Since the beginning of September 2020, a new LAB 11.5 has been added to the labs of Chapter 11 to reinforce the concepts of creating IIO drivers, and apply in a practical way the creation of a gpio controller driver, reinforcing thus the theory developed during Chapter 11. This new driver will control the Maxim MAX11300 PIXI device. This lab can be downloaded from the Github repository of this book. In this lab, you will also see how to write applications to control GPIOs by using two different methods. The first method will control the GPIO using a device node and the second method will control the GPIO using the functions of the libgpiod library. You will learn how to configure Eclipse to build and debug these applications. You can choose between several processor boards to execute this lab:

•	STM32MP157C-DK2 board from ST: The instructions to execute this lab are included in the Linux_5.4_STM32MP1_practical_labs document.

•	Raspberry Pi 4 Model B: The instructions to execute this lab are included in the Linux_5.4_rpi4_practical_labs document.

•	Raspberry Pi 3 Model B: The instructions to execute this lab are included in the Linux_5.4_rpi3_practical_labs document.

You will also need a PIXI™ CLICK from MIKROE for the LAB 11.5. The documentation of this board can be found at 
https://www.mikroe.com/pixi-click

Since the beginning of October 2020, a new LAB 7.4 has been added to the labs of Chapter 7 to reinforce the concepts of creating NESTED THREADED GPIO irqchips drivers, and apply in a practical way how to create a gpio controller with interrupt capabilities. You will also develop an user application that request GPIO interrupts from user space using GPIOlib APIs. This new lab can be downloaded from this GitHub repository. You can choose between several processor boards to execute this LAB 7.4:

•	STM32MP157C-DK2 board from ST: The instructions to execute this lab are included in the Linux_5.4_STM32MP1_practical_labs document.

•	Raspberry Pi 4 Model B: The instructions to execute this lab are included in the Linux_5.4_rpi4_practical_labs document.

•	Raspberry Pi 3 Model B: The instructions to execute this lab are included in the Linux_5.4_rpi3_practical_labs document.

You will also need an EXPAND 6 Click from MIKROE for the LAB 7.4. The documentation of this board can be found at 
https://www.mikroe.com/expand-6-click

Since the end of October 2020, a new LAB 7.5 has been added to the labs of Chapter 7, that explains how to create pinctrl and pwm controller drivers. You will use the same boards of the LAB 7.4 to develop this driver.

Since the end of November 2020, the Linux drivers included in this book have been adapted to run on the Raspberry Pi 4 Model B and Raspberry Pi 3 Model B boards using the Linux kernel version 5.4 LTS. The kernel 5.4 modules developed for these boards are included in the linux_5.4_rpi4_drivers.zip and linux_5.4_rpi3_drivers.zip files and can be downloaded from this GitHub repository. The Practical Labs Setup are described in the Linux_5.4_rpi4_practical_labs and Linux_5.4_rpi3_practical_labs documents included in this repository. 

Since the beginning of January 2021, a new LAB 10.3 has been added to the labs of Chapter 10 to reinforce the concepts of creating Input Subsystem drivers.This lab can be downloaded from the Github repository of this book. You can choose between several processor boards to execute this LAB 10.3:

•	STM32MP157C-DK2 board from ST: The instructions to execute this lab are included in the Linux_5.4_STM32MP1_practical_labs document.

•	Raspberry Pi 4 Model B: The instructions to execute this lab are included in the Linux_5.4_rpi4_practical_labs document.

•	Raspberry Pi 3 Model B: The instructions to execute this lab are included in the Linux_5.4_rpi3_practical_labs document.

You will also need the the MOD-Wii-UEXT-NUNCHUCK from Olimex for the LAB 10.3. The documentation of this board can be found at 
https://www.olimex.com/Products/Modules/Sensors/MOD-WII/MOD-Wii-UEXT-NUNCHUCK/open-source-hardware

Since the beginning of January 2021, a new LAB 11.6 has been added to the labs of Chapter 11. This lab will explain in detail how to develop “provider” and “consumer” drivers. You will use the same boards of the LAB 10.3 to develop this driver.

The document "Practical Labs Hardware" has been added to the github to detail all the needed hardware to test the lab examples included in this book.



