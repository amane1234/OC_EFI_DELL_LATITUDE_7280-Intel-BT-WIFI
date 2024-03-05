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
<p align="center">
  <img src = "/Screenshot/Combojackfix.png">
</p>

<p align="center">
  See [ioreg](./MacBook%20Pro%2014%2C1.ioreg) for more clarification
</p>

### MacOS bootable USB creation:
- Read the Dortania guide for creating your USB from Windows or macOS
- [Guide Dortania](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) - USB creation


## Bios settings
### Enable :
* SATA Operation : AHCI
* Fastboot : Minimal
* Integrated NIC : Enable
* VT-D
  

### Disable : 
* Secure Boot
* Intel SGX
* Wake on AC
* Wake on Dell USB-C Dock
* Enable UEFI Network Stack


## IMPORTANT : Using modGRUBShell.efi to unlock CFG-LOCK & DVMT value

![CFG-LOCK](./Screenshot/CFG-LOCK.png)


Type : setup_var 0x4ED 0x0 to unlock CFG-LOCK <br><br>

![DMT-PRE](./Screenshot/DVMT-TOT.png)


Type : setup_var 0x796 0x3 to set DVMT Total GFX Mem to MAX<br><br>


### Post Install regarding Sleep:

**To improve Sleep and battery life, I recommand to follow those things:**

- Disable Airdrop
- Disable Powernap and internet awake


**pmset options: **
```
sudo pmset standby 0
sudo pmset autopoweroff 0
sudo pmset powernap 0
sudo pmset proximitywake 0
sudo pmset tcpkeepalive 0
```




**(Experimental) Enable S4 Sleep:**

You need to adjust some parameters in config.plist in order to enable S4 (Hibernation) state.

```
ThirdPartyDrives = True (Set True if you are using 2.5 inch SSD or mSATA M.2 SSD)

HibernateMode = NVRAM

```

And you need to adjust your hibernationmode by pmset.

```

sudo pmset -a hibernationmode 25

```

Hibernation function should work after adjusting these values.

There are some issue, however

- After waking up from S4 sleep, you will face a blackscreen. Wait until the display turn off or press the power button to turn off the display.

After waking up, your display will properly work.

- Touchpad will not work after waking up from hibernation. (This needed to be fix!)
