#具有OpenCore的ThinkPad X230 MacOS

在ThinkPad X230上运行的MacOS（当前为Catalina`10.15.6`）

**状态：进行中**

<img align="right" src="https://ftp.bmp.ovh/imgs/2020/10/afdccda005d2aed8.png" alt="ThinkPad X230 Catalina" width="300"/>

[![ThinkPad](https://img.shields.io/badge/ThinkPad-X230-blue.svg)](https://psref.lenovo.com/syspool/Sys/PDF/withdrawnbook/ThinkPad_X230.pdf) [![release](https://img.shields.io/badge/Download-latest-brightgreen.svg)](https://github.com/banhbaoxamlan/X230-Hackintosh/releases/latest) [![OpenCore](https://img.shields.io/badge/OpenCore-0.6.1-blue.svg)](https://github.com/acidanthera/OpenCorePkg/releases/latest) [![MacOS Catalina](https://img.shields.io/badge/macOS-10.15.6-brightgreen.svg)](https://www.apple.com/macos/catalina/)

**免责声明：**
开始之前请阅读整个自述文件。我对您可能造成的任何损失不承担任何责任。

## 介绍

<details>

<summary><strong>我的硬件</strong></summary>

| Specifications      | Detail                                      |
| :------------------ | :------------------------------------------ |
| Computer model      | Lenovo ThinkPad X230 (Type: 2325)           |
| Processor           | Intel Core i7-3520M (2C4T, 2.9/3.6Ghz, 4MB) |
| Memory              | Crucial 16GB DDR3L 1867MHz, dual-channel    |
| Hard Disk           | Crucial BX500 3D-NAND 240GB                 |
| Integrated Graphics | Intel HD Graphics 4000                      |
| Display             | 12.5" HD (1366x768) TN - B125XW01.V0        |
| Audio               | Realtek ALC3202 (Layout-id: `18`)           |
| Ethernet            | Intel 82579LM Gigabit Network Connection    |
| WIFI+BT             | AzureWave AW-CB160H (BCM94360HMB)           |
| Keyboard            | 6-row, multimedia Fn keys, LED backlight    |
| Dock                | ThinkPad UltraBase Series 3                 |

</details>

<details>

<summary><strong>硬件兼容性</strong></summary>

　这EFI适合任何X230不管CPU模型,大量的内存,显示分辨率和内部存储。
　　
　　1. 可选的自定义CPU电源管理指南(见下面安装后)

  1.修改
　　- 1440 p显示模型应该改变 `NVRAM>>Add>>7C436110-AB2A-4BBB-A880-FE41995C9F82>>UIScale`: 2
     ——X220 7-row键盘应该使用 : `SSDT-X220-KBD.aml`

</details>

<details>

<summary><strong>主要软件</strong></summary>

| Component      | Version           |
| :------------- | :---------------- |
| MacOS Catalina | 10.15.6 (19G2021) |
| OpenCore       | 0.6.1             |

</details>

<details>

<summary><strong>内核扩展</strong></summary>

| Kext                | Version |
| :------------------ | :------ |
| AirportBrcmFixup    | 2.0.9   |
| AppleALC            | 1.5.2   |
| BrcmPatchRAM        | 2.5.4   |
| EFICheckDisabler    | 0.5.0   |
| IntelMausi          | 1.0.3   |
| Lilu                | 1.4.7   |
| USBPorts            |         |
| VirtualSMC          | 1.1.6   |
| VoodooPS2Controller | 2.1.6   |
| WhateverGreen       | 1.4.2   |

</details>

<details>

<summary><strong>UEFI驱动程序</strong></summary>

| Driver          | Version           |
| :-------------- | :---------------- |
| HfsPlus.efi     | OcBinaryData      |
| OpenRuntime.efi | OpenCorePkg 0.6.2 |

</details>


## 安装

<details>

<summary><strong>如何安装macOS</strong></summary>

要安装macOS，请遵循提供的指南 [Dortania](https://dortania.github.io/getting-started/)

有用的工具 [CorpNewt](https://github.com/corpnewt) 和 [headkaze](https://github.com/headkaze/Hackintool)

完整的EFI可在 [releases](https://github.com/banhbaoxamlan/X230-Hackintosh/releases/latest) 页

</details>

<details>

<summary><strong>BIOS设置 :100:</strong></summary>

提供了一种安装修改后的BIOS的简单方法 [here](https://github.com/n4ru/1vyrain/) (无需外部编程器).

| Main | Sub #1                                 | Sub #2 | Sub #3 | Setting |
| :------------ | :----------- | ------------- | ------------- | ------------- |
| Config | Network | Wake On Lan |  | Disabled |
|  | Serial ATA (SATA) | Mode |  | AHCI |
| Advanced | System Agent (SA) configuration | Graphics Configuration | DVMT Pre-Allocated | 128MB |
|  |  |  | DVMT Total Gfx Mem | MAX |
| Security | Security Chip |  |  | Disabled |
|  | Memory Protection | Execution Prevention |  | Enabled |
|  | Anti-Theft | Current Setting |  | Disabled |
|  |  | Computrace | Current Setting | Disabled |
|  | Secure Boot |  |  | Disabled |
| Startup | UEFI/Legacy Boot |  |  | UEFI Only |
|  |  | CSM Support |  | Disabled |

</details>

## 安装后


<details>

<summary><strong>生成自己的SMBIOS</strong></summary>

　　对于设置SMBIOS信息,使用[GenSMBIOS] (https://github.com/corpnewt/GenSMBIOS)
　　
　　——运行GenSMBIOS,选择选项1下载MacSerial SMBIOS选项3和选择
　　
　　——MacBookPro10 2


- 打开 `Config.plist`,找到PlatformInfo > >通用

  - 复制 `Serial` 到 SystemSerialNumber.

  - 复制 `Board Serial` 到 MLB.

  - 复制 `SmUUID` 到 SystemUUID.

* *提醒,你想要一个无效的串行或有效的序列号,但那些没有在使用,你想拿回一个消息:“Purchase Date not Validated”* *(苹果序列号检查)(https://checkcoverage.apple.com/)

</details>

<details>

<summary><strong>CPU电源管理</strong></summary>

　　推荐额外的步骤来改善与优化电池寿命CPU电源管理:
　　
　　打开终端,复制并粘贴以下命令:
　　
　　”“bash

  curl -o ~/ssdtPRGen.sh https://raw.githubusercontent.com/Piker-Alpha/ssdtPRGen.sh/master/ssdtPRGen.sh
  chmod +x ~/ssdtPRGen.sh
  ./ssdtPRGen.sh
  ```

- 一个定制的 `SSDT.aml` 将在目录 **/Users/yourusername/Library/ssdtPRGen**中

- 重命名为 `SSDT-PM.aml` ,复制到 **EFI/OC/ACPI/**

- 打开 `Config.plist`, 添加 `ACPI>>Add>>SSDT-PM.aml`

- 重启电脑

</details>

<details>

<summary><strong>USB端口映射</strong></summary>

　　如果您使用的是不同的模型和替代kext从不为你工作。试一试:
　　
　　——(USBMap) (https://github.com/corpnewt/USBMap)
　　
　　——(Hackintool) (https://github.com/headkaze/Hackintool)

</details>

<details>

<summary><strong>功能齐全的多媒体Fn的钥匙</strong></summary>

　　下载并安装(ThinkpadAssistant) (https://github.com/MSzturc/ThinkpadAssistant/releases)
　　——打开应用程序,检查“登录启动”选项
</details>

<details>

<summary><strong>使用敲击PrtSc截图快捷键</strong></summary>

- 路径 `SystemPreferences > Keyboard > Shortcuts > Screenshots`
　　——点击截图和记录选项键映射
　　——按“敲击PrtSc”在你的键盘(应该是“F13”)

</details>

<details>  
<summary><strong>Mac引导装载程序GUI</strong></summary>
　——下载二进制资源(https://github.com/acidanthera/OcBinaryData)和(OpenCanopy.efi) (https://github.com/acidanthera/OpenCorePkg/releases)
　　-副本(资源文件夹)(https://github.com/acidanthera/OcBinaryData)“EFI / OC”
　　——添加OpenCanopy。efi“efi / OC /驱动程序”
　　——这些变化在“config.plist”:
    - `Misc >> Boot >> PickerMode`: `External`
    - `Misc >> Boot >> PickerAttributes`:`1`
    - `UEFI >> Drivers` and add `OpenCanopy.efi`

</details>

## Status

<details>
<summary><strong>什么在工作 :white_check_mark:</strong></summary>

- [x] 电池百分比
　　——[x]蓝牙
　　——[x]亮度
　　——[x]相机
　　——[x] CPU电源管理
　　——[x]码头支持“ThinkPad UltraSeries 3 '
　　——英特尔HD 4000 - [x] GPU图形QE / CI
　　——[x]英特尔以太网
　　——[x]键盘的数量和亮度快捷键
　　——[x]睡眠/唤醒
　　——[x]声音的耳机自动检测、静音、音量控制完全工作的
　　——[x] Touchpad的手指滑动作品的
　　——[x]指点杆的作品完美。就像在Windows或Linux上的

　　——[x] eGPU  (由 [lese9855](https://github.com/lese9855) 已经证实 [#11](https://github.com/banhbaoxamlan/X230-Hackintosh/issues/11))

</details>

<details>

<summary><strong>什么不可用 :warning:</strong></summary>

- [ ] 指纹阅读器
- [ ] VGA
- [ ] SD读卡器 (禁用`SSDT-SDC.aml`)

</details>

<details>

<summary><strong>已知Bug :heavy_exclamation_mark:</strong></summary>

- [ ] 指点杆从睡眠中醒来后不工作

</details>

## Credits

[Apple](https://www.apple.com) for macOS

[Acidanthera](https://github.com/acidanthera) for all the kexts/utilities that they made

[Rehabman](https://github.com/RehabMan) and [Daliansky](https://github.com/daliansky) for the patches and guides and kexts

[George Kushnir](https://github.com/n4ru) for modified BIOS

[Dortania](https://github.com/dortania) for for the OpenCore Install Guide

[MSzturc](https://github.com/MSzturc) for ThinkpadAssistant

[simprecicchiani](https://github.com/simprecicchiani) for inspirational ThinkPad configurations
