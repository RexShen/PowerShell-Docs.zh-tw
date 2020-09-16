---
ms.date: 12/06/2019
keywords: powershell,cmdlet
title: Windows PowerShell 系統需求
ms.openlocfilehash: 883da2f91c4a0b46e4bccbacd9933a52f8f476f6
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236079"
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell 系統需求

本文列出 Windows PowerShell 3.0、Windows PowerShell 4.0、Windows PowerShell 5.0 與 Windows PowerShell 5.1 的系統需求， 以及特殊功能，例如 Windows PowerShell 整合式指令碼環境 (ISE)、通用訊息模型 (CIM) 命令與工作流程。

Windows® 8.1 和 Windows Server® 2012 R2 包含所有必要的程式。 本文是專為舊版 Windows 使用者所撰寫。

## <a name="operating-system-requirements"></a>作業系統需求

### <a name="windows-powershell-51"></a>Windows PowerShell 5.1

Windows PowerShell 5.1 可在下列版本的 Windows 上執行。 若要執行 Windows PowerShell 5.1，請安裝 Windows Management Framework 5.1。 如需詳細資訊，請參閱[安裝與設定 WMF 5.1](../wmf/setup/install-configure.md)。

|              Windows 版本               |                           系統需求                            |
| ------------------------------------------ | ----------------------------------------------------------------------- |
| Windows Server 2019                        | 依預設安裝                                                    |
| Windows Server 2016                        | 依預設安裝                                                    |
| Windows Server 2012 R2                     | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012                        | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 (含 Service Pack 1) | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 1607 版和更新版本             | 依預設安裝                                                    |
| Windows 10 1507 版和 1511 版              | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 8.1                                | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 (含 Service Pack 1)              | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-50"></a>Windows PowerShell 5.0

Windows PowerShell 5.0 在下列版本的 Windows 上執行。 若要執行 Windows PowerShell 5.0，請安裝 Windows Management Framework 5.1。 如需詳細資訊，請參閱[安裝與設定 WMF 5.1](../wmf/setup/install-configure.md)。 Windows Management Framework 5.1 將取代 Windows Management Framework 5.0。

|              Windows 版本               |                           系統需求                            |
| ------------------------------------------ | ----------------------------------------------------------------------- |
| Windows Server 2019                        | 依預設安裝較新版本                                     |
| Windows Server 2016                        | 依預設安裝較新版本                                     |
| Windows Server 2012 R2                     | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012                        | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 (含 Service Pack 1) | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 1607 版和更新版本             | 依預設安裝較新版本                                     |
| Windows 10 1507 版和 1511 版              | 依預設安裝                                                    |
| Windows 8.1                                | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 (含 Service Pack 1)              | 安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-40"></a>Windows PowerShell 4.0

Windows PowerShell 4.0 是在下列版本的 Windows 上執行。 若要執行 Windows PowerShell 4.0，請為作業系統安裝指定的 Windows Management Framework 版本。

|               Windows 版本               |                                             系統需求                                             |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Windows 8.1                                 | 依預設安裝                                                                                       |
| Windows Server 2012 R2                      | 依預設安裝                                                                                       |
| Windows® 7 (含 Service Pack 1)              | 安裝 [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855) |
| Windows Server® 2008 R2 (含 Service Pack 1) | 安裝 [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855) |

### <a name="windows-powershell-30"></a>Windows PowerShell 3.0

Windows PowerShell 3.0 是在下列版本的 Windows 上執行。 若要執行 Windows PowerShell 3.0，請為作業系統安裝指定的 Windows Management Framework 版本。

|               Windows 版本               |                                             系統需求                                             |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Windows 8                                   | 依預設安裝                                                                                       |
| Windows Server 2012                         | 依預設安裝                                                                                       |
| Windows® 7 (含 Service Pack 1)              | 安裝 [Windows Management Framework 3.0](https://www.microsoft.com/download/details.aspx?id=34595) |
| Windows Server® 2008 R2 (含 Service Pack 1) | 安裝 [Windows Management Framework 3.0](https://www.microsoft.com/download/details.aspx?id=34595) |
| Windows Server 2008 (含 Service Pack 2)     | 安裝 [Windows Management Framework 3.0](https://www.microsoft.com/download/details.aspx?id=34595) |

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework 需求

下表顯示 Windows PowerShell 的 .NET Framework 需求。

|        版本         |                                                                                 .NET 需求                                                                                  |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Windows PowerShell 5.1 | 需要完整安裝 Microsoft .NET Framework 4.5。 Windows 8.1 和 Windows Server 2012 R2 預設包含 Microsoft .NET Framework 4.5。                           |
| Windows PowerShell 5.0 | 需要完整安裝 Microsoft .NET Framework 4.5。 Windows 8.1 和 Windows Server 2012 R2 預設包含 Microsoft .NET Framework 4.5。                           |
| Windows PowerShell 4.0 | 需要完整安裝 Microsoft .NET Framework 4.5。 Windows 8.1 和 Windows Server 2012 R2 預設包含 Microsoft .NET Framework 4.5。                           |
| Windows PowerShell 3.0 | 需要完整安裝 Microsoft .NET Framework 4。 Windows 8 和 Windows Server 2012 預設會包括 Microsoft .NET Framework 4.5 (這滿足此需求)。 |

使用下列連結，從 Microsoft 下載中心下載 Microsoft .NET Framework。

|                     版本                      |                                                     連結                                                     |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| .NET Framework 4.5 (`dotNetFx45_Full_setup.exe`) | [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919)                               |
| .NET Framework 4 (`dotNetFx40_Full_setup.exe`)   | [Microsoft .NET Framework 4 (Web 安裝程式)](https://www.microsoft.com/download/details.aspx?id=17851) |

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0

Windows PowerShell 5.0 需要先在 Windows Server 2008 R2 SP1 及 Windows 7 SP1 上預先安裝 Windows Management Framework 4.0。

## <a name="ws-management-30"></a>WS-Management 3.0

Windows PowerShell 3.0 和 Windows PowerShell 4.0 需要可支援 WinRM 服務和 WSMan 通訊協定的 WS-Management 3.0。 這個程式包含在 Windows 8.1、Windows Server 2012 R2、Windows 8、Windows Server 2012、Windows Management Framework 4.0 和 Windows Management Framework 3.0 中。

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3.0

Windows PowerShell 3.0 和 Windows PowerShell 4.0 需要 Windows Management Instrumentation 3.0 (WMI)。 這個程式包含在 Windows 8.1、Windows Server 2012 R2、Windows 8、Windows Server 2012、Windows Management Framework 4.0 和 Windows Management Framework 3.0 中。 如果電腦上未安裝此程式，則不會執行需要 WMI 的功能 (例如 CIM 命令)。

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0

Windows PowerShell 3.0、Windows PowerShell 4.0 及 Windows PowerShell 5.0 由 Common Language Runtime (CLR) 4.0 編譯。

## <a name="graphical-user-interface-requirements"></a>圖形化使用者介面需求

Windows PowerShell 是不需要圖形化使用者介面的主控台應用程式。
其適用於沒有螢幕或監視器的電腦，或使用者介面 (例如 Windows Server 2012 R2 或 Windows Server 2012 的 Server Core 安裝選項)。

某些項目需要圖形化使用者介面。 如需詳細資料，請參閱每個項目的說明文章。

- Windows PowerShell 整合式指令碼環境 (ISE)。 如需詳細資訊，請參閱 [Windows PowerShell ISE 簡介](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise)。
- 指令程式
  - [Out-GridView](/powershell/module/microsoft.powershell.utility/out-gridview)
  - [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command)
  - [Show-ControlPanelItem](/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)
  - [Show-EventLog](/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)
- 參數
  - [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 的 **ShowWindow** 參數。
  - [Register-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) 的 **ShowSecurityDescriptorUI** 參數和 [Set-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) Cmdlet。

## <a name="windows-powershell-engine-requirements"></a>Windows PowerShell 引擎需求

Windows PowerShell 4.0 設計成可回溯相容至 Windows PowerShell 3.0 和 Windows PowerShell 2.0。 針對 Windows PowerShell 2.0 和 Windows PowerShell 3.0 撰寫的 Cmdlet、提供者、嵌入式管理單元、模組及指令碼，在 Windows PowerShell 4.0 中仍以同樣方式執行。

不過，因為 Microsoft .NET Framework 4 中執行階段啟用原則的變更，所以針對 Windows PowerShell 2.0 所撰寫並使用通用語言執行平台 (CLR) 2.0 編譯的 Windows PowerShell 主機程式必須經過修改，才能在 Windows PowerShell 3.0 (使用 CLR 4.0 編譯) 中執行。

Windows PowerShell 2.0 引擎的最低需求為 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 Service Pack 1 可滿足這項需求。 Microsoft .NET Framework 4 和更新版本的 Microsoft .NET Framework 不滿足這項需求。

如需新增或安裝 Windows PowerShell 2.0 引擎以及新增或安裝所需 Microsoft .NET Framework 版本的資訊，請參閱[安裝 Windows PowerShell 2.0 引擎](Installing-the-Windows-PowerShell-2.0-Engine.md)。 如需啟動 Windows PowerShell 2.0 引擎的相關資訊，請參閱[啟動 Windows PowerShell 2.0 引擎](../Starting-the-Windows-PowerShell-2.0-Engine.md)。

## <a name="windows-preinstallation-environment"></a>Windows 預先安裝環境

Windows PowerShell 2.0、Windows PowerShell 3.0 和 Windows PowerShell 4.0 能在 Windows 預先安裝環境 (Windows PE) 中執行。 不過，不支援下列 Cmdlet。

- 背景智慧型傳送服務 (BITS) Cmdlet。 如需詳細資訊，請參閱 [BitsTransfer](/powershell/module/bitstransfer/?view=win10-ps)。
- [Get-EventLog](/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)
- [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)
- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)
- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Windows PE 上沒有 **WinRm** 服務。

## <a name="see-also"></a>另請參閱

[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)

[啟動 Windows PowerShell](../Starting-Windows-PowerShell.md)

[Windows Management Framework](../wmf/overview.md)
