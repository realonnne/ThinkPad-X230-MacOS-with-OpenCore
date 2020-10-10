#无线
　　
　　# # DW1510
　　
　　——下载文件”10.14.6_IO80211Family.kext。压缩,提取和替换IO80211Family kext在* * / S / L / E * *
　　——打开“配置。plist”,使:
　　——“ACPI > >添加> > SSDT-WIFI.aml”
　　——“内核> >添加> > BlueTooth_BCM.kext”
　　
　　
　　奖金:重新写DW1510苹果机驱动[这](https://prasys.info/2009/12/09/rebranding-broadcom-802-11abgn-cards-as-airport/)
　　
　　
## BCM94352HMB (DW1550)
　　
　　——下载(AirportBrcmFixup) (https://github.com/acidanthera/AirportBrcmFixup/releases/latest)和(BrcmPatchRAM) (https://github.com/acidanthera/BrcmPatchRAM/releases/latest), kexts复制到* * EFI / OC / kexts / * *
　　——AirportBrcmFixup.kext
　　——BrcmBluetoothInjector.kext
　　——BrcmFirmwareData.kext
　　——BrcmPatchRAM3.kext
　　——打开“配置。plist”,使:
　　——“ACPI > >添加> > SSDT-WIFI.aml”
　　——“内核> >添加> > AirportBrcmFixup.kext”
　　——“内核> >添加> > BrcmBluetoothInjector.kext”
　　——“内核> >添加> > BrcmFirmwareData.kext”
　　——“内核> >添加> > BrcmPatchRAM3.kext”
　　
　　# #英特尔无线(AX200 7260ac,等)
　　
　　在这里看到更多:[打开 Intel Wireless](https://openintelwireless.github.io/)
