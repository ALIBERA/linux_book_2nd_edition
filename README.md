 # linux_book_2nd_edition
linux driver development for embedded processors 2nd edition

The source code of the drivers and device tree for NXP i.MX7, Microchip SAMA5D27 and Broadcomm BCM2837 processors can be downloaded from drivers_source_code.zip. These drivers have been implemented using the v4.9 LTS kernel. The evaluation boards and their configurations used to develop these drivers are explained in detail throughout this book.

The source code of the drivers and device tree for SAMA5D27-SOM1 (SAMA5D27 System On Module) can be downloaded from linux_4.14_sama5d27-SOM_drivers.zip. These drivers have been implemented using the v4.14 LTS kernel. The ATSAMA5D27-SOM1-EK1 evaluation platform (https://www.microchip.com/developmenttools/ProductDetails/atsama5d27-som1-ek1) has been used for the development of these 4.14 kernel drivers. The Microchip SAMA5D27-SOM1 Practical Labs Setup is described in the Linux_4.14_SAMA5D27-SOM1_practical_labs.pdf file included in this GitHub repository.

Since the end of March 2019, a new chapter and an appendix have been added to the text of the book. These are: Chapter 13, “Linux USB Device Drivers” and Appendix, “Porting Kernel Modules to the Microchip SAMA5D27-SOM1”. These two new chapters can also be downloaded from the Github of this book for readers who have acquired the book before that date. In the USB chapter, you will learn how to create a fully functional USB HID device based on the Microchip PIC32MX microcontroller that will send/receive data to/from a Linux USB Host device based on the Microchip SAMA5D27 processor; several custom Linux USB device drivers will be developed throughout this chapter. The Appendix will explain the hardware settings for the ATSAMA5D27-SOM1-EK1 board that are needed to test the practical labs described throughout this book; to run the labs on this new board, you will download the SAMA5D27-SOM1 Linux drivers based on the kernel 4.14, and the SAMA5D27-SOM1 device tree settings from the GitHub repository of this book.
