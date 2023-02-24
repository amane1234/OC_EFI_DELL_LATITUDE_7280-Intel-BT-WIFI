# Dell Latitude 7280 (Kaby Lake) Hackintosh
[![](https://img.shields.io/badge/EFI-Release-informational?style=flat&logo=apple&logoColor=white&color=9debeb)](https://github.com/Lorys89/DELL_LATITUDE_7280/releases)



EFI for Dell Latitude 7280 with OpenCore bootloader

![descrizione](./Screenshot/pc.jpg)

### Computer Spec:

| Component        | Brank                              |
| ---------------- | ---------------------------------- |
| CPU              | Intel i5 7300U (2C-4T 3MB KBL)     |
| iGPU             | Intel® HD 620 Graphics             |
| Lan              | Intel I219-LM                      |
| Audio            | Realtek ALC256                     |
| Ram              | Crucial 8 GB DDR4 2133 Mhz         |
| Wifi + Bluetooth | intel 3165                         |
| NVMe             | SAMSUNG 980 500 GB (MACOS+WIN 11)  |
| SmBios           | MacBookPro 14,1                    |
| BootLoader       | OpenCore 0.8.9                     |
| macOS            | Ventura                            |

You need to manually download and install itlwm.kext (or airportitlwm.kext) to use WIFI



![infomac](./Screenshot/infomac.png)

### What works and What doesn't or WIP:

- [x] Intel HD 620 iGPU eDP with Backlight Output
- [x] Intel HD 620 iGPU HDMI Output 
- [x] Intel HD 620 iGPU Type-C to HDMI Output
- [x] Intel HD 620 iGPU - H264 & HEVC
- [x] ALC256 Internal Speakers
- [x] ALC256 Internal microphone
- [x] ALC256 Combojack headphones
- [x] ALC256 Combojack microphone
- [x] ALC256 HDMI Audio Output
- [x] ALC256 TYPE-C to HDMI Audio Output
- [x] All USB-A 3.1 Ports (TYPE-C 3.1 Included)
- [x] SpeedStep / Sleep / Wake
- [x] HID Key PWRB & SLPB 
- [x] I2C ALPS Touchpad with gesture
- [x] Keyboard (PS2-Internal) with backlight
- [x] Brightness Key
- [x] F11 Print Screen Key
- [x] F1 & F2 & F3 Sound Key
- [x] Wi-Fi and Bluetooth BCM94352Z (DELL DW1560) Module
- [x] Lan Intel I219-LM
- [x] SSD NVME Slot-1 PciE
- [x] Micro SD Cardreader
- [x] WebCam (USB-Internal)
- [x] All Sensors CPU, IGPU, BATTERY, NVME, FAN
- [x] ACPI Battery
- [x] NVRAM (Native)
- [x] Recovery (macOS) boot from OpenCore
- [x] Windows 11 boot from OpenCore

## Peripherals & TouchPad Setting & Benchmarks

![infohack](./Screenshot/periferiche.png)
![infodp2](./Screenshot/pci-list.png)
![infopci](./Screenshot/pci-dev.png)
![Temp-Fan-Control](./Screenshot/Temp-Fan-Control.png)
![speedtest](./Screenshot/speedtest.png)
![touchpad](./Screenshot/touchpad.png)
![trascinamento](./Screenshot/trascinamento.png)
![5finger](./Screenshot/fingermgmt.png)
![CPU](./Screenshot/CPU.png)
![openCL](./Screenshot/openCL.png)
![metal](./Screenshot/metal.png)
![videoproc](./Screenshot/videoproc.png)

### Post Install:

Open terminal and run install.sh from TOOLS EFI MOD/ComboJack_Installer. After reboot insert jack and appears this image
![jack](./Screenshot/Combojackfix.png)

See [ioreg](./MacBook%20Pro%2014%2C1.ioreg) for more clarification


### MacOS bootable USB creation:
- Read the Dortania guide for creating your USB from Windows or macOS
- [Guide Dortania](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) - USB creation


## Bios settings
### Enable :
* SATA Operation : AHCI
* Fastboot : Minimal
* Integrated NIC : Enable


### Disable : 
* Secure Boot
* VT-D
* Intel SGX
* Wake on AC
* Wake on Dell USB-C Dock
* Enable UEFI Network Stack
* CFG lock and DVMT

## IMPORTANT : To unlock CFG and DVMT, restart and at the opencore GUI, choose the modGRUBShell.efi

![CFG-LOCK](./Screenshot/CFG-LOCK.png)

To set CFG LOCK Disabled

Type : setup_var 0x4ED 0x0


![DMT-PRE](./Screenshot/DVMT-PRE.png)

To set DVMT PRE Allocated to 64 MB

Type : setup_var 0x795 0x2

![DMT-PRE](./Screenshot/DVMT-TOT.png)

TO set DVMT Total GFX Mem to MAX

Type : setup_var 0x796 0x3


## Credits

- [Apple](https://apple.com) for macOS.
- [Acidanthera](https://github.com/acidanthera) for OpenCore and all the lovely hackintosh work.
- [Juico](https://github.com/juico) for fix Alps i2c touchpad.
