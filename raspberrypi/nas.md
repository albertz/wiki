My Raspberry Pi 5 with 8GB:
`dmesg` says:
```
...
Machine model: Raspberry Pi 5 Model B Rev 1.0
...
Kernel command line: reboot=w coherent_pool=1M 8250.nr_uarts=1 pci=pcie_bus_safe snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1  smsc95xx.macaddr=2C:CF:67:1D:E3:DA vc_mem.mem_base=0x3fc00000 vc_mem.mem_size=0x40000000  console=ttyAMA10,115200 multipath=off dwc_otg.lpm_enable=0 console=tty1 root=LABEL=writable rootfstype=ext4 rootwait fixrtc cfg80211.ieee80211_regdom=GB
...
[    2.351382] pci 0000:01:00.0: 4.000 Gb/s available PCIe bandwidth, limited by 5.0 GT/s PCIe x1 link at 0000:00:00.0 (capable of 15.752 Gb/s with 8.0 GT/s PCIe x2 link)

```

I want to attach a couple of SATA HDDs to it.

I used a PCI-e-to-NVME-M.2 bridge and then a M.2-to-SATA bridge.
I see the SATA controller:
`lspci` shows:
```
0000:01:00.0 SATA controller: ASMedia Technology Inc. ASM1166 Serial ATA Controller (rev 02)
```
However, attaching some SATA HDD (to SATA1) does not seem to work.
`dmesg` shows:
```
[    2.645731] ata1: SATA max UDMA/133 abar m8192@0x1b00082000 port 0x1b00082100 irq 43 lpm-pol 0
[    2.654400] ata2: SATA max UDMA/133 abar m8192@0x1b00082000 port 0x1b00082180 irq 43 lpm-pol 0
[    2.663052] ata3: SATA max UDMA/133 abar m8192@0x1b00082000 port 0x1b00082200 irq 43 lpm-pol 0
[    2.671702] ata4: SATA max UDMA/133 abar m8192@0x1b00082000 port 0x1b00082280 irq 43 lpm-pol 0
[    2.680351] ata5: SATA max UDMA/133 abar m8192@0x1b00082000 port 0x1b00082300 irq 43 lpm-pol 0
[    2.689004] ata6: SATA max UDMA/133 abar m8192@0x1b00082000 port 0x1b00082380 irq 43 lpm-pol 0
...
[    8.120087] ata1: link is slow to respond, please be patient (ready=0)
[    8.591928] ata1: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
[    8.855645] ahci 0000:01:00.0: AHCI controller unavailable!
[    9.150697] ahci 0000:01:00.0: AHCI controller unavailable!
[   16.261460] ata2: failed to resume link (SControl FFFFFFFF)
[   20.896760] ata2: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
[   22.639355] ahci 0000:01:00.0: AHCI controller unavailable!
[   23.223717] ahci 0000:01:00.0: AHCI controller unavailable!
[   31.197445] ata3: failed to resume link (SControl FFFFFFFF)
[   35.832740] ata3: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
[   37.575346] ahci 0000:01:00.0: AHCI controller unavailable!
[   38.159703] ahci 0000:01:00.0: AHCI controller unavailable!
[   46.133448] ata4: failed to resume link (SControl FFFFFFFF)
[   50.768736] ata4: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
[   52.511342] ahci 0000:01:00.0: AHCI controller unavailable!
[   53.095689] ahci 0000:01:00.0: AHCI controller unavailable!
[   61.069459] ata5: failed to resume link (SControl FFFFFFFF)
[   65.704729] ata5: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
[   67.447328] ahci 0000:01:00.0: AHCI controller unavailable!
[   68.031675] ahci 0000:01:00.0: AHCI controller unavailable!
[   76.005443] ata6: failed to resume link (SControl FFFFFFFF)
[   80.640729] ata6: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
[   82.383335] ahci 0000:01:00.0: AHCI controller unavailable!
```
Maybe because the PCI-e-to-NVME-M.2 bridge does not have enough power?
