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

Maybe I also should use the PCIe lane at Gen 3.0 speeds (setting `dtparam=pciex1_gen=3` in `/boot/firmware/config.txt`)?

Some relevant links (partly posts from myself):
* [geerlingguy / raspberry-pi-pcie-devices: Test PCIe switches and adapters #14 (my comment)](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/14#issuecomment-2141448525)
* [geerlingguy / raspberry-pi-pcie-devices: ASMedia Technology Inc. Device 1064 M.2 NVME to Mini SAS Expansion Card Support 4 Ports SATA3.0 6Gbps HDD SSD SATA Controller SFF8087 #600 (my comment)](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/600#issuecomment-2143579129)
* [Raspberry Pi forums: Raspberry Pi 5 PCIe Bus Error - ASM1166](https://forums.raspberrypi.com/viewtopic.php?t=363682)

It seems this ASM1166 chip is problematic with Raspberry Pi?
**Edit** It seems it works now, with the help from Ezaul [here](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/600#issuecomment-2143909849).
Specifically, to make it work (without really understanding what this does):
```shell
# backup current dtb
sudo cp /boot/firmware/bcm2712-rpi-5-b.dtb /boot/firmware/bcm2712-rpi-5-b.dtb.bak
# decompile current dtb
dtc -I dtb -O dts /boot/firmware/bcm2712-rpi-5-b.dtb -o ~/test.dts
```
Then edit the dts file (e.g. `nano ~/test.dts`), look for `pcie@110000` section, look for `msi-parent = ...`, and change that value to the same as the `phandle` value in the same section. Then save, and then:
```shell
# recompile dtb
dtc -I dts -O dtb ~/test.dts -o ~/test.dtb
# move back to firmware dir
sudo mv ~/test.dtb /boot/firmware/bcm2712-rpi-5-b.dtb
# (Ignore the potential error/warning:
#  mv: failed to preserve ownership for '/boot/firmware/bcm2712-rpi-5-b.dtb': Operation not permitted)
# reboot
sudo reboot
```
And now it seems to work! `dmesg`:
```
[    8.101051] ata1: link is slow to respond, please be patient (ready=0)
[    8.367081] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    8.374843] ata1.00: ATA-11: ST4000NE001-2MA101, EN01, max UDMA/133
[    8.394013] ata1.00: 7814037168 sectors, multi 16: LBA48 NCQ (depth 32), AA
[    8.401503] ata1.00: Features: NCQ-sndrcv
[    8.420145] ata1.00: configured for UDMA/133
[    8.424652] scsi 0:0:0:0: Direct-Access     ATA      ST4000NE001-2MA1 EN01 PQ: 0 ANSI: 5
[    8.433197] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.433244] sd 0:0:0:0: [sda] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
[    8.446314] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    8.451576] sd 0:0:0:0: [sda] Write Protect is off
[    8.456394] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.456423] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.465537] sd 0:0:0:0: [sda] Preferred minimum I/O size 4096 bytes
[    8.745187] ata2: SATA link down (SStatus 0 SControl 300)
[    8.914641] sd 0:0:0:0: [sda] Attached SCSI disk
[    9.057245] ata3: SATA link down (SStatus 0 SControl 300)
[    9.369195] ata4: SATA link down (SStatus 0 SControl 300)
[    9.681197] ata5: SATA link down (SStatus 0 SControl 300)
[    9.993191] ata6: SATA link down (SStatus 0 SControl 300)
```
You might need to redo this procedure after updating the kernel.

I also bought another JMB575-based SATA controller now to test whether that works more out-of-the-box. Let's see...
