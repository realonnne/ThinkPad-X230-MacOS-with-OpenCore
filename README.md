# ThinkPad X230 MacOS with OpenCore

MacOS（目前为Catalina'10.15.7'和Big-Sur'11.0.1`）正在使用ThinkPad X230

**状态：正在工作**

[![ThinkPad](https://img.shields.io/badge/ThinkPad-X230-blue.svg)](https://psref.lenovo.com/syspool/Sys/PDF/withdrawnbook/ThinkPad_X230.pdf) [![release](https://img.shields.io/badge/Download-latest-brightgreen.svg)](https://github.com/kikileaf/ThinkPad-X230-MacOS-with-OpenCore/releases) [![OpenCore](https://img.shields.io/badge/OpenCore-0.6.3-blue.svg)](https://github.com/acidanthera/OpenCorePkg/releases/latest) [![MacOS Catalina](https://img.shields.io/badge/macOS-10.15.7-brightgreen.svg)](https://www.apple.com/macos/catalina/) [![MacOS Big Sur](https://img.shields.io/badge/macOS-11.0.1-purple.svg)](https://www.apple.com/macos/big-sur/)

**免责声明:** 在开始之前，请阅读完整的自述文件。我对你可能造成的任何损失概不负责。

## 介绍

<details>
<summary><strong>我的硬件</strong></summary>

| 规格                | 细节                                        |
| :------------------ | :------------------------------------------ |
| 计算机型号          | Lenovo ThinkPad X230 (Type: 2325)           |
| CPU                 | Intel Core i5-3380M (2C4T, 2.9/3.6Ghz, 3MB) |
| 内存                | Crucial 16GB DDR3L 1600MHz, dual-channel    |
| 硬盘                | Samsung 860 Evo 250GB                       |
| 显卡                | Intel HD Graphics 4000                      |
| 屏幕                | 12.5" HD (1366x768)                         |
| 声卡                | Realtek ALC3202 (Layout-id: `18`)           |
| 以太网卡            | Intel 82579LM Gigabit Network Connection    |
| WIFI+BT             | AzureWave AW-CE123H (BCM94360HMB)           |
| 键盘                | 7排, 多功能 Fn 键盘,                        |
| Dock                | ThinkPad Mini Dock Plus系列3                |

</details>

<details>
<summary><strong>硬件兼容性</strong></summary>

无论CPU型号、RAM数量、显示分辨率和内部存储，该EFI都适用于任何X230。

  1. 可选的自定义CPU电源管理指南（请参阅下面的安装后）
  2. 被改进的
      - 1440p显示器型号应该改变 `NVRAM>>Add>>7C436110-AB2A-4BBB-A880-FE41995C9F82>>UIScale`: 2

</details>

<details>
<summary><strong>主软件</strong></summary>

| 组成部分       | 版本              |
| :------------- | :---------------- |
| MacOS Big Sur  | 11.0.1            |
| MacOS Catalina | 10.15.7           |
| OpenCore       | 0.6.3             |

</details>

<details>
<summary><strong>内核扩展</strong></summary>

| Kext                | 版本 |
| :------------------ | :------ |
| AirportBrcmFixup    | 2.1.1   |
| AppleALC            | 1.5.4   |
| BrcmPatchRAM        | 2.5.5   |
| EFICheckDisabler    | 0.5.0   |
| IntelMausi          | 1.0.4   |
| Lilu                | 1.4.9   |
| USBInjectAll        | 0.7.1   |
| VirtualSMC          | 1.1.8   |
| VoodooPS2Controller | 2.1.8   |
| WhateverGreen       | 1.4.4   |

</details>

<details>
<summary><strong>UEFI drivers</strong></summary>

| Driver          | 版本           |
| :-------------- | :---------------- |
| HfsPlus.efi     | OcBinaryData      |
| OpenCanopy.efi  | OpenCorePkg 0.6.3 |
| OpenRuntime.efi | OpenCorePkg 0.6.3 |

</details>

## 安装

<details>
<summary><strong>如何安装macOS</strong></summary>

要安装macOS，请遵循 [Dortania](https://dortania.github.io/getting-started/)

有用的工具[CorpNewt](https://github.com/corpnewt) 和 [headkaze](https://github.com/headkaze/Hackintool)

完整的EFI可在 [releases](https://github.com/kikileaf/kikileaf-ThinkPad-X230-MacOS-with-OpenCore/releases/latest) page

</details>

<details>
<summary><strong>BIOS设置 :100:</strong></summary>

一个简单的方法来安装修改后的BIOS是可用的 [here](https://github.com/n4ru/1vyrain/) (no external programmer required).

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

### Support
![Donate](https://github.com/kikileaf/ThinkPad-X230-MacOS-with-OpenCore/blob/main/Support.png)
