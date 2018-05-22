---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: Windows Management Framework (WMF)
ms.openlocfilehash: ae50e8d1495d7075163714ed873940d2d1d19b8e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) 是一種傳遞機制，可在各式各樣的 Windows 和 Windows Server 中提供一致的管理介面。
安裝 WMF 後，客戶即可順暢自如地在其混合了各種作業系統的環境中操作。
WMF 會更新指定 Windows 和 Windows Server 版本的管理功能，於安裝較低版本的 Windows 和 Windows Server (一般是低 2 個版本) 時提供。

WMF 安裝新增及 (或) 更新下列功能︰

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell 整合式指令碼環境 (ISE)
- Windows 遠端管理 (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell Web 服務 (Management OData IIS 擴充功能)
- 軟體清查記錄 (SIL)
- 伺服器管理員 CIM 提供者

## <a name="wmf-release-notes"></a>WMF 版本資訊

如需深入了解 PowerShell 的各種增強功能以及指定 WMF 的其他元件，請參閱下列版本資訊連結︰

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>各 Windows 作業系統的 WMF 可用性

| 作業系統版本 | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | 隨產品附贈 |  |  |  |  |
| Windows 10 | 隨產品附贈 | 隨產品附贈  | | | |
| Windows Server 2012 R2| 是 | 是 | 隨產品附贈 |  |  |
| Windows 8.1 | 是 | 是 |  隨產品附贈 |  |  |
| Windows Server 2012 | 是 | 是 | 是 |  隨產品附贈 | |
| Windows 8 |  |  |  | 隨產品附贈 | |
| Windows Server 2008 R2 SP1 | 是 | 是 | 是 |  是| 隨產品附贈 |
| Windows 7 SP1  | 是 | 是 | 是 | 是 | 隨產品附贈 |
| Windows Server 2008 SP2 | | | | 是 | 是 |
| Windows Vista | | | | | 是 |
| Windows Server 2003| | | |  | 是 |
| Windows XP | | | |  | 是 |

**隨產品附贈**：`specified WMF` 的功能已和指定版本的 Windows 和 Windows Server 一起出貨。
因此，`specified WMF` 不需要安裝在指定的作業系統版本上。
