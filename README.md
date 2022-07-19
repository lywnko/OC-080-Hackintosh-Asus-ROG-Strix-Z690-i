# OC-080-Hackintosh-Asus-ROG-Strix-Z690-i
OC-080 Hackintosh Asus ROG Strix Z690-i Gaming WiFi 
Introduction:from

https://www.tonymacx86.com/threads/asus-z690-proart-creator-wifi-thunderbolt-4-i7-12700k-amd-rx-6800-xt.318311/page-109#post-2321018

For the past several months I had been thinking of building my first mini-ITX system. That plan came to fruition today with the following system:

    Meshlicious mini-ITX case in white with PCIe 4.0 riser cable
    Asus ROG Strix Z690-i Gaming WiFi motherboard
    Intel i5-12600K processor *
    Sapphire RX 6600 XT GPU *
    Cooler Master V750 SFX White Edition Power Supply
    Lian Li Galahad AIO 240 White Edition liquid cooler
    G.Skill TridentZ 32GB DDR5-5600 CL40-40-40-76 non-RGB RAM
    Silicon Power 1TB PCIe 3.0 NVMe SSD *
    Keychron Q3 customizable keyboard (what a beast this is, wow)
    Fenvi BCM94360NG WiFi/BT card
    Right Angle DisplayPort cable Model C

This build cannibalizes some parts from other systems and uses some new parts. Parts marked above with an asterisk were cannibalized.

Build Notes:
The Meshlicious mini-ITX case is remarkably easy to build in, featuring an internal skeleton wrapped on 4 sides with mesh panels. Build quality is superb; the white finishing is equally impeccable. And the rear IO panel faces the rear, not the bottom. My top three considerations in choosing a mini-ITX case were:

    Compact size while still being easy to build in (not requiring esoterically tiny components)
    Excellent airflow
    Rear IO panel must face the rear, not the bottom

Replacing the built-in Intel WiFi/BT module with a Fenvi BCM94360NG was straightforward, but required the removal of VRM shroud/heatsink assembly. The assembly is a single L-shaped part that covers the rear IO and the top edge, so it's necessary to remove additional screws that fasten it to the top edge.

DisplayPort Cable:
Although the Meshlicious comes with an L-shaped DisplayPort cable, I chose to purchase a different one from Amazon. Several orientations of the cable are available, but Model C is the correct one. Parts list above contains a link. L-shaped cable is needed because GPU is installed with the bracket facing down towards the floor.

Thunderbolt:
Thunderbolt hot plug works with the SSDT provided in the EFI folder. Thunderbolt Bus, however, is not enabled in Monterey.

Benchmarks:
Benchmark Table v3.png


USB Port Map:
I started with the OpenCore 0.8.0 EFI folder for the Asus ProArt Z690-Creator, but with new serial numbers and all DeviceProperties commented out. That was sufficient to install Monterey 12.3.1 from scratch. Subsequently I created two custom USB port maps:

    SSDT-UIAC-ASUS-Z690-I-GAMING-15-PORTS.aml -- limited to 15 USB ports; XhciPortLimit kernel quirk must be disabled; good reliability
    SSDT-UIAC-ASUS-Z690-I-GAMING-ALL-PORTS.aml -- enables all USB ports; XhciPortLimit kernel quirk must be enabled; reliability varies (Asus AURA LED at HS02, for example, may not work)

USB port diagrams are shown below.

USB Map - Rear IO Panel.png
USB Map - Motherboard.png

​
The board shipped with BIOS 0229, which causes reboot issues so upgrading to BIOS 1403 (latest as of today) is strongly recommended. macOS Monterey 12.3.1 installed on the first attempt and has been running smoothly all day.

The on-board Intel WiFi/BT module was replaced with the Fenvi BCM94360NG. This supports AirDrop, Handoff, and all other macOS Continuity features. The photos in the gallery below were AirDropped from an iPhone.

With the custom USB port map installed, sleep and wake work properly. The 15-port USB map is recommended. If we use the "ALL" ports version, some ports may not activate -- such as the AURA LED port on HS02.

For anyone interested in this build, I'm attaching the OpenCore 0.8.0 EFI folder for the Asus ROG Strix Z690-i Gaming WiFi (mini-ITX). Simply enter your serial numbers in PlatformInfo --> DataHub and the name of your CPU in NVRAM. This build has also been added to HackinDROM.
OCC - CPU Name.png

Gallery of Build and Benchmarks:
IMG_6231_resize.jpg
IMG_6233_resize.jpg


Asus riser card supporting 4 SATA ports, one A-RGB header, front panel connectors, and a speaker connector:
IMG_6234_resize.jpg


Riser card installed, along with 2 G.Skill TridentZ DIMMs:
IMG_6235_resize.jpg


Removal of L-shaped VRM shroud/heatsink is necessary for accessing WiFi/BT module:
IMG_6237_resize.jpg


In this photo the WiFi/BT housing has been removed, exposing a black slot into which the Key A/E card fits:
IMG_6239_resize.jpg


Here's the standard Intel AX210 WiFi/BT module supporting WiFi 6E and BT 5.2, but isn't fully compatible with macOS:
IMG_6238_resize.jpg


We replace the Intel module with a Fenvi BCM94360NG based on a supported Broadcom chipset:
IMG_6240_resize.jpg


The interior steel frame:
IMG_6241_resize.jpg


Installing the main board. When assembling a mini-ITX system, perform a dry fit of all components in order to determine clearances and best ways of routing cables.
IMG_6244_resize.jpg


The Cooler Master 750W SFX power supply is surprisingly tiny.
IMG_6248_resize.jpg


With the main board, power supply and SATA SSD (under the PSU):
IMG_6251_resize.jpg


Thankfully the rear IO panel faces the rear (not the bottom) for easy access.
IMG_6253_resize.jpg


Installing the GPU behind the main board. Connected via PCIe 4.0 riser cable supplied with the case. Also supplied with the case is an L-shaped DisplayPort cable.
IMG_6257_resize.jpg


The fully assembled unit undergoing post-assembly testing. Cable management was done later.
IMG_6262_resize.jpg
