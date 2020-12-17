---
title: 在 Arm 上安裝 PowerShell Core
description: 在 Arm 型系統上安裝 PowerShell Core
ms.date: 11/11/2020
ms.openlocfilehash: 85a2cccb18341ffee8c81430bc8490e5d3e97b41
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892067"
---
# <a name="powershell-core-on-arm"></a>Arm 上的 PowerShell Core

Arm 上的 PowerShell 支援是以 **.NET Core 支援的 OS 生命週期原則** 為基礎。

PowerShell 7.1 是以 [.NET Core 3.1 支援的 OS 生命週期原則](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) \(英文\) 為基礎，而且支援下列平台：

|         OS          |          版本           | 架構 |          生命週期           |
| ------------------- | -------------------------- | ------------- | ---------------------------- |
| Windows Nano 伺服器 | 1803+ 版              | Arm32         | [Windows][Windows-lifecycle] |
| Alpine Linux        | 3.10+                      | Arm64         | [Alpine][Alpine-lifecycle]   |
| Debian              | 9+                         | Arm32、Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu              | 20.10、20.04、18.04、16.04 | Arm32、Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

PowerShell 7.0 是以 [.NET Core 5.0 支援的 OS 生命週期原則](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) \(英文\) 為基礎，並且支援下列平台：

|        OS         |          版本           | 架構 |          生命週期           |
| ----------------- | -------------------------- | ------------- | ---------------------------- |
| Windows 10 用戶端 | 1607+ 版              | Arm64         | [Windows][Windows-lifecycle] |
| Alpine Linux      | 3.11+                      | Arm64         | [Alpine][Alpine-lifecycle]   |
| Debian            | 9+                         | Arm32、Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu            | 20.10、20.04、18.04、16.04 | Arm32、Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

[Windows-lifecycle]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[Alpine-lifecycle]: https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases
[Debian-lifecycle]: https://wiki.debian.org/DebianReleases
[Ubuntu-lifecycle]: https://wiki.ubuntu.com/Releases

如需安裝指示，請參閱下列文章：

- [Arm 上的 Windows 10](installing-powershell-core-on-windows.md#installing-the-zip-package)
- [Windows 10 IoT 企業版](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-enterprise)
- [Windows 10 IoT 核心版](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-core)
- [Raspbian](installing-powershell-core-on-linux.md#raspbian)
