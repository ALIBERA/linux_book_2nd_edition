 # linux_book_2nd_edition
Linux Driver Development for Embedded Processors 2nd Edition

The source code of the drivers and device tree for NXP i.MX7, Microchip SAMA5D27 and Broadcomm BCM2837 processors can be downloaded from drivers_source_code.zip. These drivers have been implemented using the v4.9 LTS kernel. The evaluation boards and their configurations used to develop these drivers are explained in detail throughout this book.

The source code of the drivers and device tree for SAMA5D27-SOM1 (SAMA5D27 System On Module) can be downloaded from linux_4.14_sama5d27-SOM_drivers.zip. These drivers have been implemented using the v4.14 LTS kernel. The ATSAMA5D27-SOM1-EK1 evaluation platform (https://www.microchip.com/developmenttools/ProductDetails/atsama5d27-som1-ek1) has been used for the development of these 4.14 kernel drivers. The Microchip SAMA5D27-SOM1 Practical Labs Setup is described in the Linux_4.14_SAMA5D27-SOM1_practical_labs.pdf file included in this GitHub repository.

Since the end of March 2019, a new chapter and an appendix have been added to the text of the book. These are: Chapter 13, “Linux USB Device Drivers” and Appendix, “Porting Kernel Modules to the Microchip SAMA5D27-SOM1”. These two new chapters can also be downloaded from the Github of this book for readers who have acquired the book before that date. In the USB chapter, you will learn how to create a fully functional USB HID device based on the Microchip PIC32MX microcontroller that will send/receive data to/from a Linux USB Host device based on the Microchip SAMA5D27 processor; several custom Linux USB device drivers will be developed throughout this chapter. The Appendix will explain the hardware settings for the ATSAMA5D27-SOM1-EK1 board that are needed to test the practical labs described throughout this book; to run the labs on this new board, you will get the SAMA5D27-SOM1 Linux drivers based on the kernel 4.14, and the SAMA5D27-SOM1 device tree settings from the Appendix_linux_4.14_sama5d27-SOM_drivers.zip file, which is included in the GitHub repository of this book.

Since the end of November 2019, the Linux drivers included in this book have been adapted to run on the Raspberry Pi 4 Model B board using Linux kernel version 4.19. The kernel 4.19 modules developed for the Raspberry Pi 4 Model B board are included in the linux_4.19_rpi4_drivers.zip file and can be downloaded from this GitHub repository. The Raspberry Pi 4 Practical Labs Setup is described in the Linux_4.9_RaspberryPi4_practical_labs document included in this repository.

The repository git.freescale.com is not working anymore, all content was migrated to either one of these repositories:

github.com/NXP

github.com/NXPMicro

https://source.codeaurora.org/external/imx/

Following the next i.MX Release Manifest:

https://source.codeaurora.org/external/imx/imx-manifest/about/

You have to replace the instructions in pag.34 of "Chapter 1 : Building the System" for the next ones:

~$ mkdir fsl-release-bsp

~$ cd fsl-release-bsp/

~/fsl-release-bsp$ git config --global user.name "Your Name"

~/fsl-release-bsp$ git config --global user.email "Your Email"

~/fsl-release-bsp$ git config --list

~/fsl-release-bsp$ repo init -u https://source.codeaurora.org/external/imx/fsl-arm-yocto-bsp.git -b imx-morty -m imx-4.9.11-1.0.0_ga.xml

~/fsl-release-bsp$ repo sync -j4

~/fsl-release-bsp$ DISTRO=fsl-imx-x11 MACHINE=imx7dsabresd source fsl-setup-release.sh -b build_imx7d

Replace IMX_FIRMWARE_SRC variable in the recipe “firmware-imx_6.0.bb”: 

~$ gedit  ~/fsl-release-bsp/sources/meta-fsl-bsp-release/imx/meta-bsp/recipes-bsp/firmware-imx/firmware-imx_6.0.bb

IMX_FIRMWARE_SRC ?= "git://github.com/NXP/imx-firmware;protocol=git"

~/fsl-release-bsp/build_imx7d$ bitbake fsl-image-validation-imx



