#### Identifying CPU information


```
[root@ip-172-31-22-143 ~]# lscpu
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              1
On-line CPU(s) list: 0
Thread(s) per core:  1
Core(s) per socket:  1
Socket(s):           1
NUMA node(s):        1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               63
Model name:          Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz
Stepping:            2
CPU MHz:             2399.894
BogoMIPS:            4800.02
Hypervisor vendor:   Xen
Virtualization type: full
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            30720K
NUMA node0 CPU(s):   0
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology cpuid tsc_known_freq pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm cpuid_fault invpcid_single pti fsgsbase bmi1 avx2 smep bmi2 erms invpcid xsaveopt
```

#### Run the “-e” option in the terminal; it will gather CPU related data and display it in Human Readable Format:

```
root@ip-172-31-22-143 ~]# lscpu -e
CPU NODE SOCKET CORE L1d:L1i:L2:L3 ONLINE
0   0    0      0    0:0:0:0       yes
```

#### DMI Id give us particular hardware information of system. Dmidecode with options ‘-t ‘or ‘–type‘ and ‘Id‘ will provide us the exact infromation. Id 6 will give us Memory Module information.



```
[root@ip-172-31-22-143 ~]# dmidecode -t 6
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.
```



#### To get the information about Manufacturer, Model and Serial Number of system, use the following command as shown below.

```
root@Tuttu:~# dmidecode -t system
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Dell Inc.
	Product Name: Inspiron 3542
	Version: Not Specified
	Serial Number: C1GC712
	UUID: 4c4c4544-0031-4710-8043-c3c04f373132
	Wake-up Type: Power Switch
	SKU Number: 0651
	Family:                       

Handle 0x0013, DMI type 12, 5 bytes
System Configuration Options
	Option 1: To Be Filled By O.E.M.

Handle 0x0016, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected
```

#### Command to display information of the hard drive

```
root@Tuttu:~# hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       ST1000LM048-2E7172                      
	Serial Number:      WL1JZGBL
	Firmware Revision:  SDM1    
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
	Used: unknown (minor revision code 0x001f) 
	Supported: 10 9 8 7 6 5 
	Likely used: 10
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:    16514064
	LBA    user addressable sectors:   268435455
	LBA48  user addressable sectors:  1953525168
	Logical  Sector size:                   512 bytes
	Physical Sector size:                  4096 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      953869 MBytes
	device size with M = 1000*1000:     1000204 MBytes (1000 GB)
	cache/buffer size  = unknown
	Form Factor: 2.5 inch
	Nominal Media Rotation Rate: 5400
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 254
	Recommended acoustic management value: 208, current value: 208
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	    	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	    	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Gen3 signaling speed (6.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	Idle-Unload when NCQ is active
	   *	READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
	   *	DMA Setup Auto-Activate optimization
	   *	Device-initiated interface power management
	    	Asynchronous notification (eg. media change)
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Write Same (AC2)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
	   *	DOWNLOAD MICROCODE DMA command
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	178min for SECURITY ERASE UNIT. 178min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000c500be14e033
	NAA		: 5
	IEEE OUI	: 000c50
	Unique ID	: 0be14e033
Checksum: correct
```
#### Command to test hard disk drive speed :

```
[root@ip-172-31-22-143 ~]# hdparm -t /dev/xvda

/dev/xvda:
 Timing buffered disk reads: 246 MB in  3.02 seconds =  81.35 MB/sec
```

#### PCI / Hardware information

```
This will display information about all the devices.

[root@ip-172-31-22-143 ~]# lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
00:02.0 VGA compatible controller: Cirrus Logic GD 5446
00:03.0 Unassigned class [ff80]: XenSource, Inc. Xen Platform Device (rev 01)
```

#### Display Kernel Drivers, This is very helpful when you like to know the name of the kernel module that will be handling the operations of a particular device

```
[root@ip-172-31-22-143 ~]# lspci -v
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
	Subsystem: Red Hat, Inc. Qemu virtual machine
	Physical Slot: 0
	Flags: fast devsel

00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
	Subsystem: Red Hat, Inc. Qemu virtual machine
	Physical Slot: 1
	Flags: medium devsel

00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II] (prog-if 80 [ISA Compatibility mode-only controller, supports bus mastering])
	Subsystem: XenSource, Inc. Device 0001
	Physical Slot: 1
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable)
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable)
	I/O ports at c100 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
	Subsystem: Red Hat, Inc. Qemu virtual machine
	Physical Slot: 1
	Flags: fast devsel, IRQ 9

00:02.0 VGA compatible controller: Cirrus Logic GD 5446 (prog-if 00 [VGA controller])
	Subsystem: XenSource, Inc. Device 0001
	Physical Slot: 2
	Flags: fast devsel
	Memory at f0000000 (32-bit, prefetchable) [size=32M]
	Memory at f3000000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]

00:03.0 Unassigned class [ff80]: XenSource, Inc. Xen Platform Device (rev 01)
	Subsystem: XenSource, Inc. Xen Platform Device
	Physical Slot: 3
	Flags: fast devsel, IRQ 28
	I/O ports at c000 [size=256]
	Memory at f2000000 (32-bit, prefetchable) [size=16M]
	Kernel driver in use: xen-platform-pci
  ```

#### Information on USB Hardware

```
$ lsusb
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0cf3:0036 Qualcomm Atheros Communications 
Bus 001 Device 003: ID 064e:c233 Suyin Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 002 Device 003: ID 046d:c542 Logitech, Inc. USB2.0 Hub
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```




