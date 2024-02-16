# Dell Latitude 7280 (Kaby Lake) Hackintosh


EFI for Dell Latitude 7280 with OpenCore EFI

### Laptop Spec

| Component        | Brank                              |
| ---------------- | ---------------------------------- |
| CPU              | Intel i5 7300U (2C-4T 3MB KBL)     |
| iGPU             | Intel® HD 620 Graphics             |
| Lan              | Intel I219-LM                      |
| Audio            | Realtek ALC256                     |
| Ram              | Crucial 8 GB DDR4 2133 Mhz         |
| Wifi + Bluetooth | intel 3165                         |
| NVMe             | MICRON 256 GB                      |
| SmBios           | MacBookPro 14,1                    |
| BootLoader       | OpenCore 0.9.5                     |
| macOS            | Sonoma                             |


You need to manually download and install itlwm.kext (or airportitlwm.kext) to use WIFI

itlwm / Airportitlwm : https://github.com/OpenIntelWireless/itlwm

Heliport : https://github.com/OpenIntelWireless/HeliPort

### What works and What doesn't:

Since intelbluetooth card is not officially supported in MacOS, it might be laggy when it comes to pairing.

Exchanging bluetooth card that support MacOS would be a great idea.

3.5mm headphone jack works yet poor sound quality. Use bluetooth connections instead.

Every function works quiet well.

### SMBIOS:

This hackintosh EFI uses MacBookPro 14,1 SMBIOS.

Create your own MacBookPro 14,1 SMBIOS with GenSMBIOS

https://github.com/corpnewt/GenSMBIOS

### Post Install:

Open terminal and run install.sh from TOOLS EFI MOD/ComboJack_Installer.
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


### Post Install regarding Sleep:

**To improve Sleep and battery life, I recommand to follow those things:**

- Disable Airdrop
- Disable Powernap and internet awake


**pmset options: **
```
sudo pmset standby 1
sudo pmset autopoweroff 1
sudo pmset powernap 0
sudo pmset proximitywake 0
sudo pmset tcpkeepalive 0
```


**If your hibernatemode is NVRAM at config.plist, you may set hibernatemode 25 by:**

```
sudo pmset hibernatemode 25
```
To improve battery life when the laptop is in Sleep state (S3 / S4)

