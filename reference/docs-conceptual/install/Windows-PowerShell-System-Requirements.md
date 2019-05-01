---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 系統需求
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: a9a7dc434d26876d6747526ad3ef6fa598376ac1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058296"
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell 系統需求
本主題列出適用於 Windows PowerShell 3.0、Windows PowerShell 4.0、Windows PowerShell 5.0 及 Windows PowerShell 5.1，以及適用於一些特殊功能 (例如 Windows PowerShell 整合式指令碼環境 (ISE)、CIM 命令與工作流程) 的系統需求。

Windows® 8.1 和 Windows Server® 2012 R2 包含所有必要的程式。 本主題是針對舊版 Windows 使用者所設計。

## <a name="operating-system-requirements"></a>作業系統需求
Windows PowerShell 5.1 可在下列版本的 Windows 上執行。

- Windows Server 2019；預設會加以安裝

- Windows Server 2016；預設會加以安裝

- Windows Server 2012 R2；必須安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) \(英文\) 才能執行 Windows PowerShell 5.1

- Windows Server 2012；必須安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) \(英文\) 才能執行 Windows PowerShell 5.0

- Windows Server 2008 R2 Service Pack 1；必須安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) \(英文\) 才能執行 Windows PowerShell 5.1

- Windows 10 1607 版及更新版本；預設會加以安裝

- Windows 10 1507 版、1511 版；必須安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) \(英文\) 才能執行 Windows PowerShell 5.1

- Windows 8.1；必須安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) \(英文\) 才能執行 Windows PowerShell 5.1

- Windows 7 Service Pack 1；必須安裝 [Windows Management Framework 5.1](https://aka.ms/wmf5download) \(英文\) 才能執行 Windows PowerShell 5.1

Windows PowerShell 5.0 (由 Windows PowerShell 5.1 取代) 可在下列版本的 Windows 上執行。

- Windows Server 2019；預設會安裝較新版本

- Windows Server 2016；預設會安裝較新版本

- Windows Server 2012 R2；必須安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 才能執行 Windows PowerShell 5.0

- Windows Server 2012；必須安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 才能執行 Windows PowerShell 5.0

- Windows Server® 2008 R2 Service Pack 1)；必須安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 才能執行 Windows PowerShell 5.0

- Windows 10 1607 版及更新版本；預設會安裝較新版本

- Windows 10 1507 版、1511 版；預設會加以安裝

- Windows 8.1；必須安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) \(英文\) 才能執行 Windows PowerShell 5.0

- Windows 7 Service Pack 1；必須安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 才能執行 Windows PowerShell 5.0

Windows PowerShell 4.0 是在下列版本的 Windows 上執行。

- 預設安裝的 Windows 8.1

- 預設安裝的 Windows Server 2012 R2

- Windows® 7 (含 Service Pack 1)，請安裝 [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) 來執行 Windows PowerShell 4.0

- Windows Server® 2008 R2 (含 Service Pack 1)，請安裝 [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) 來執行 Windows PowerShell 4.0

Windows PowerShell 3.0 是在下列版本的 Windows 上執行。

- 預設安裝的 Windows 8

- 預設安裝的 Windows Server 2012

- Windows® 7 (含 Service Pack 1)，請安裝 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) 來執行 Windows PowerShell 3.0

- Windows Server® 2008 R2 (含 Service Pack 1)，請安裝 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) 來執行 Windows PowerShell 3.0

- Windows Server 2008 (含 Service Pack 2)，請安裝 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) 來執行 Windows PowerShell 3.0

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework 需求
Windows PowerShell 5.1 需要完整安裝 Microsoft .NET Framework 4.5。 Windows 8.1 和 Windows Server 2012 R2 預設包含 Microsoft .NET Framework 4.5。

Windows PowerShell 5.0 需要安裝完整的 Microsoft .NET Framework 4.5。 Windows 8.1 和 Windows Server 2012 R2 預設包含 Microsoft .NET Framework 4.5。

Windows PowerShell 4.0 需要完整安裝 Microsoft .NET Framework 4.5。 Windows 8.1 和 Windows Server 2012 R2 預設包含 Microsoft .NET Framework 4.5。

Windows PowerShell 3.0 需要完整安裝 Microsoft .NET Framework 4。 Windows 8 和 Windows Server 2012 預設會包括 Microsoft .NET Framework 4.5 (這滿足此需求)。

若要安裝 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)，請參閱 Microsoft 下載中心上的 [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919)。

若要安裝 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完整安裝，請參閱 Microsoft 下載中心上的 [Microsoft .NET Framework 4 (Web 安裝程式)](https://go.microsoft.com/fwlink/?LinkID=212931)。

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0
Windows PowerShell 5.0 需要先在 Windows Server 2008 R2 SP1 及 Windows 7 SP1 上預先安裝 Windows Management Framework 4.0。

## <a name="ws-management-30"></a>WS-Management 3.0
Windows PowerShell 3.0 和 Windows PowerShell 4.0 需要可支援 WinRM 服務和 WSMan 通訊協定的 WS-Management 3.0。 這個程式包含在 Windows 8.1、Windows Server 2012 R2、Windows 8、Windows Server 2012、Windows Management Framework 4.0 和 Windows Management Framework 3.0 中。

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3.0
Windows PowerShell 3.0 和 Windows PowerShell 4.0 需要 Windows Management Instrumentation 3.0 (WMI)。 這個程式包含在 Windows 8.1、Windows Server 2012 R2、Windows 8、Windows Server 2012、Windows Management Framework 4.0 和 Windows Management Framework 3.0 中。 如果電腦上未安裝此程式，則不會執行需要 WMI 的功能 (例如 CIM 命令)。

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0
Windows PowerShell 3.0、Windows PowerShell 4.0 及 Windows PowerShell 5.0 由 Common Language Runtime (CLR) 4.0 編譯。

## <a name="graphical-user-interface-requirements"></a>圖形化使用者介面需求
Windows PowerShell 是不需要圖形化使用者介面的主控台應用程式。 同樣地，它也適用於沒有螢幕或監視器的電腦或者使用者介面 (例如 Windows Server 2012 R2 或 Windows Server 2012 的 Server Core 安裝選項)。

不過，某些項目 (例如下列項目) 需要圖形化使用者介面。 如需詳細資料，請參閱每個項目的說明主題。

- Windows PowerShell 整合式指令碼環境 (ISE)

- Cmdlet

    1.  [Out-GridView](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Show-Command](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Show-ControlPanelItem](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Show-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- 參數

    1.  [Get-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 的 **ShowWindow** 參數。

    2.  [Register-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) 的 **ShowSecurityDescriptorUI** 參數和 [Set-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) Cmdlet。

## <a name="windows-powershell-engine-requirements"></a>Windows PowerShell 引擎需求
Windows PowerShell 4.0 設計成可回溯相容至 Windows PowerShell 3.0 和 Windows PowerShell 2.0。 針對 Windows PowerShell 2.0 和 Windows PowerShell 3.0 撰寫的 Cmdlet、提供者、嵌入式管理單元、模組及指令碼，在 Windows PowerShell 4.0 中仍以同樣方式執行。

不過，因為 Microsoft .NET Framework 4 中執行階段啟用原則的變更，所以針對 Windows PowerShell 2.0 所撰寫並使用通用語言執行平台 (CLR) 2.0 編譯的 Windows PowerShell 主機程式必須經過修改，才能在 Windows PowerShell 3.0 (使用 CLR 4.0 編譯) 中執行。

Windows PowerShell 2.0 引擎至少需要 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 Service Pack 1 可滿足此需求。 Microsoft .NET Framework 4 和更新版本的 Microsoft .NET Framework 不滿足此需求。

如需新增或安裝 Windows PowerShell 2.0 引擎以及新增或安裝所需 Microsoft .NET Framework 版本的資訊，請參閱[安裝 Windows PowerShell 2.0 引擎](Installing-the-Windows-PowerShell-2.0-Engine.md)。 如需啟動 Windows PowerShell 2.0 引擎的相關資訊，請參閱[啟動 Windows PowerShell 2.0 引擎](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)。

## <a name="windows-preinstallation-environment"></a>Windows 預先安裝環境
Windows PowerShell 2.0、Windows PowerShell 3.0 和 Windows PowerShell 4.0 能在 Windows 預先安裝環境 (Windows PE) 中執行。 不過，不支援下列 Cmdlet。

- [背景智慧型傳送服務 (BITS) Cmdlet](https://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Save-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Update-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Update-Help)

此外，Windows PE 上沒有 **WinRm** 服務。

## <a name="see-also"></a>另請參閱
- [開始使用 Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [安裝 Windows PowerShell](Installing-Windows-PowerShell.md)
- [啟動 Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)
