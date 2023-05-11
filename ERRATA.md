Since March 2023 source.codeaurora.org is closed. NXP is migrating from CodeAurora to GitHub. Now, you can find any source code at the following link: https://github.com/nxp-imx

In the page 34 of "Chapter 1: Building the System" you must replace the instruction:

repo init -u https://source.codeaurora.org/external/imx/imx-manifest -b imx-linux-morty -m imx-4.9.11-1.0.0_ga.xml 

with the new instruction:

repo init -u https://github.com/nxp-imx/imx-manifest -b imx-linux-morty -m imx-4.9.11-1.0.0_ga.xml 

And this is the new instruction in page 39 to download the kernel sources:

~$ git clone https://github.com/nxp-imx/linux-imx -b imx_4.9.11_1.0.0_ga
