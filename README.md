# Hackintosh - EFI

Computer Specifications:

| Hardware             | Spec                      |
| -------------------- | ------------------------- |
| **Opencore Version** | 0.9.9                     |
| **Ammount of RAM**   | 32GB                      |
| **Graphics Card**    | RX 6650 XT                |
| **Motherboard**      | Asrock B450m Steel Legend |
| **Processor**        | AMD RYZEN 5 5600          |
| **OS**               | MacOS Sonoma 14.4      |

# Important

Update **config.plist** in PlatformInfo > Generic with YOUR informations.
<br><br>
_1. MLB (Board Serial)
<br> 2. ROM (Mac Address)
<br> 3. SystemSerialNumber (Serial)
<br> 4. SystemUUID (SmUUID)_

Please use [_genSMBIOS_](https://github.com/corpnewt/GenSMBIOS/archive/refs/heads/master.zip) for generate values for above itens.
<br>
Please use [_ProperTree_](https://github.com/corpnewt/ProperTree/archive/refs/heads/master.zip) for configure/edit your config.plist.

- USB port mapping is **REQUIRED**.
- **`XhciPortLimit`** - Please `**ENABLE**` to map the USB ports
  - You can use USBMap.command Utility - [USBMap](https://github.com/corpnewt/USBMap).
- **`SetupVirtualMap`** in config.plist:
  - B550, A520 and TRx40 boards should **`DISABLE`** this;
  - Newer BIOS versions of X570 also require this **`DISABLE`**;
  - X470 and B450 with late 2020 BIOS updates also require this **`DISABLE`**.
- **`DevirtualiseMmio`** - TRx40 users please **`ENABLE`** this flag.

# BIOS Settings

### Disable

- Fast Boot
- Secure Boot
- Serial/COM Port
- Parallel Port
- Compatibility Support Module (CSM)(Must be off, GPU errors like `gIO` are common when this option in enabled)

### Enable

- Above 4G decoding
  - This must be on, if you can't find the option then add `npci=0x2000` to `boot-args`.
  - Do not have both this option and `npci` in `boot-args` enabled at the same time.
  - If you are on a Gigabyte/Aorus or an AsRock motherboard, enabling this option may break certain drivers(ie. Ethernet) and/or boot failures on other OSes, if it does happen then disable this option and opt for `npci` instead.
  - 2020+ BIOS Notes: When enabling Above4G, Resizable BAR Support may become an available on some X570 and newer motherboards. Please ensure this is **`DISABLED`** instead of set to Auto.
- EHCI/XHCI Hand-off
- OS type: Windows 8.1/10 UEFI Mode
- SATA Mode: AHCI
