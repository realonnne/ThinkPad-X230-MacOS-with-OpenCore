# ThinkPad X230 MacOS with OpenCore

MacOS（目前为Catalina'10.15.7'和Big-Sur'11.2`）正在使用ThinkPad X230

**状态：正在工作**

[![ThinkPad](https://img.shields.io/badge/ThinkPad-X230-blue.svg)](https://psref.lenovo.com/syspool/Sys/PDF/withdrawnbook/ThinkPad_X230.pdf) [![release](https://img.shields.io/badge/Download-latest-brightgreen.svg)](https://github.com/banhbaoxamlan/X230-Hackintosh/releases/latest) [![OpenCore](https://img.shields.io/badge/OpenCore-0.6.6-blue.svg)](https://github.com/acidanthera/OpenCorePkg/releases/latest) [![MacOS Catalina](https://img.shields.io/badge/macOS-10.15.7-brightgreen.svg)](https://www.apple.com/macos/catalina/) [![MacOS Big Sur](https://img.shields.io/badge/macOS-11.2-purple.svg)](https://www.apple.com/macos/big-sur/)

**免责声明:** 在开始之前，请阅读完整的自述文件。我对你可能造成的任何损失概不负责。
[![捐赠](https://img.shields.io/badge/%E6%8D%90%E8%B5%A0-%E6%94%AF%E4%BB%98%E5%AE%9D-blue)](https://github.com/kikileaf/ThinkPad-X230-MacOS-with-OpenCore/blob/main/Support.png) [![捐赠](https://img.shields.io/badge/%E6%8D%90%E8%B5%A0-%E5%BE%AE%E4%BF%A1-green)](https://github.com/kikileaf/ThinkPad-X230-MacOS-with-OpenCore/blob/main/Support.png)

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
| :------------------ | :------ |
| AirportBrcmFixup    | 2.1.1   |
| AppleALC            | 1.5.7   |
| BrcmPatchRAM        | 2.5.5   |
| EFICheckDisabler    | 0.5.0   |
| IntelMausi          | 1.0.5   |
| Lilu                | 1.5.1   |
| USBInjectAll        | 0.7.1   |
| VirtualSMC          | 1.2.0   |
| VoodooPS2Controller | 2.2.1   |
| WhateverGreen       | 1.4.7   |

</details>

<details>
<summary><strong>UEFI 驱动</strong></summary>

| 驱动            | 版本              |
| :-------------- | :---------------- |
| OpenHfsPlus.efi | OpenCorePkg 0.6.6 |
| OpenCanopy.efi  | OpenCorePkg 0.6.6 |
| OpenRuntime.efi | OpenCorePkg 0.6.6 |

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

## 安装后

<details>
<summary><strong>生成自己的SMBIOS</strong></summary>

要设置SMBIOS信息，请使用 [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)

- 运行GenSMBIOS，选择选项1下载MacSerial，选择选项3以选择SMBIOS

  - MacBookPro10,2
  - MacBookPro11,5 (支持Big Sur 及10、x和更高版本)

- 打开 `Config.plist`, 找到 PlatformInfo >> Generic

  - 把 `Serial` 部分复制到 SystemSerialNumber 上

  - 把 `Board Serial` 部分复制到 MLB 上

  - 把 `SmUUID` 部分复制到 SystemUUID 上

**提醒您想要一个无效的序列号或有效的序列号，但是这些序列号没有被使用，您想要得到一条信息，比如：“无效的序列号”或“购买日期没有被验证”***[苹果支票覆盖范围](https://checkcoverage.apple.com/)

</details>

<details>
<summary><strong>CPU电源管理</strong></summary>

通过优化CPU电源管理提高电池寿命的建议附加步骤:

- 打开 Config.plist, 找到 `ACPI>>Delete` : 删除  CpuPm和Cpu0Ist
- 打开 Terminal, 复制并粘贴以下命令:

  ```bash
  curl -o ~/ssdtPRGen.sh https://raw.githubusercontent.com/Piker-Alpha/ssdtPRGen.sh/master/ssdtPRGen.sh
  chmod +x ~/ssdtPRGen.sh
  ./ssdtPRGen.sh
  ```

- 定制的 `SSDT.aml`  位于能力的mac**/Users/yourusername/Library/ssdtPRGen** 下

- 重命名为`SSDT-PM.aml` , 并放在你的EFI磁盘 **EFI/OC/ACPI/** 下

- 打开 `Config.plist`, 添加 `ACPI>>Add>>SSDT-PM.aml`

- 重启MAC


</details>

<details>
<summary><strong>USB端口</strong></summary>

如果您使用的是不同的型号和其他文件夹的替代kext 将不适合您。尝试：

- [USBMap](https://github.com/corpnewt/USBMap)

- [Hackintool](https://github.com/headkaze/Hackintool)

</details>

<details>
<summary><strong>功能齐全的多媒体Fn键</strong></summary>

- 下载并安装  [ThinkpadAssistant](https://github.com/MSzturc/ThinkpadAssistant/releases)
- 打开应用程序并检查 `launch on login` 选项

</details>

<details>
<summary><strong>使用PrtSc键作为屏幕截图快捷方式</strong></summary>

- 在“系统首选项>键盘>快捷键>屏幕截图”下`
- 单击“屏幕截图和录制选项”选项
- 按键盘上的“PrtSc”（显示为“F13”）

</details>

## 状态

<details>
<summary><strong>能用的和不能用的</strong></summary>

- [√] 电池百分比
- [√] 蓝牙
- [√] 亮度调节
- [√] 摄像头
- [√] CPU电源管理
- [√] 支持基座`ThinkPad UltraSeries 3`
- [√] GPU Intel HD 4000 图形 QE/CI
- [√] 英特尔以太网
- [√] 键盘 `音量和亮度热键`
- [√] 睡眠/唤醒
- [√] 声音`耳机自动检测，静音，音量控制完全工作`
- [√] 触摸板`1-4个手指滑动工作`
- [√] TrackPoint工作得很好。就像在Windows或Linux上一样`
- [√] eGPU 

</details>

<details>

<summary><strong>什么不起作用：警告：</strong></summary>

- [ ] 指纹阅读器
- [ ] VGA
- [ ] SD卡读卡器 (禁止使用 `SSDT-SDC.aml`)

</details>

### 打赏
![Donate](https://s3.ax1x.com/2021/02/12/yrVp3d.png)
