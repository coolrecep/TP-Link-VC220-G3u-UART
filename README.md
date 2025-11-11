# TP-Link VC220-G3u (Turk Telekom) Internals

This repository contains device information and a full UART boot log for the **TP-Link VC220-G3u** DSL modem, specifically the version provided by the Turkish ISP **Turk Telekom**.

The information is intended for security research, firmware analysis, and general hacking purposes.

## Hardware Specifications (from boot log)

* **Model:** TP-Link VC220-G3u
* **SoC:** EcoNet EN751221
* **CPU:** MIPS 34Kc @ 900 MHz (detected as 4 CPUs/TCs)
* **RAM:** 128MB DDR3
* **Flash:** 128MB SPI NAND (Gigadevice, mfr_id=0xc8, dev_id=0x1)
* **Wi-Fi (2.4GHz):** MediaTek MT7603 (device_id = 0x7603)
* **Wi-Fi (5GHz):** MediaTek MT7613/MT7663 (device_id = 0x7663)
* **Ethernet:** Mix of Gigabit and Fast Ethernet PHYs
* **USB:** Yes (xHCI Host Controller detected)

## Software Information

* **Bootloader:** `EN751221 version 1.1 free bootbase`
* **Bootloader Access:** Yes, there is a **1-second** interrupt prompt:
    `Press any key in 1 secs to enter boot command mode.`
* **Linux Kernel:** `Linux version 2.6.36` (Build date: Wed Nov 20 02:02:23 UTC 2024)
* **UART Console:** `ttyS0` is enabled.

## MTD Flash Partitions

The device uses an SPI NAND flash with the following MTD partition layout. The presence of `kernel_2` and `rootfs_2` indicates an A/B (dual-boot) partition scheme, likely for failsafe firmware updates.

```

Creating 11 MTD partitions on "EN7512-SPI\_NAND":
0x000000000000-0x000000020000 : "boot"
0x000000020000-0x0000000a0000 : "romfile"
0x0000000a0000-0x0000001a0000 : "config"
0x0000001a0000-0x0000001e0000 : "radio"
0x0000001e0000-0x0000003e0000 : "kernel"
0x0000003e0000-0x0000023e0000 : "rootfs"
0x0000001e0000-0x0000023e0000 : "ker\_rofs"
0x0000023e0000-0x0000025e0000 : "kernel\_2"
0x0000025e0000-0x0000045e0000 : "rootfs\_2"
0x0000023e0000-0x0000045e0000 : "ker\_rofs\_2"
0x0000045e0000-0x000007300000 : "reserve\_area"

```

## Full UART Boot Log

<details>
  <summary>Click to expand the full boot log</summary>

```

Welcome to minicom 2.10

OPTIONS: I18n
Port /dev/serial0, 15:38:17 [U]

Press CTRL-A Z for help on special keys

BGA IC
Xtal:1
DDR3 init.
DRAMC init done.
Calculate size.
DRAM size=128MB
Set new TRFC.
ddr-1066

7512DRAMC V1.2.2 (0)
Set SPI Flash Clock to 25 Mhz

EN751221 at Fri Mar 19 05:35:52 UTC 2021 version 1.1 free bootbase

Memory size 128MB

Set SPI Flash Clock to 25 Mhz
spi\_nand\_probe: mfr\_id=0xc8, dev\_id=0x1
Dected SPI NAND Flash : \_SPI\_NAND\_DEVICE\_ID\_F50L1G41LB, Flash Size=0x8000000
bmt pool size: 81
BMT & BBT Init Success

Press any key in 1 secs to enter boot command mode.
............
\<... full log trimmed for brevity ...\>

```
</details>
```
