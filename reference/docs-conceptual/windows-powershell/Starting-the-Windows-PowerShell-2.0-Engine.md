---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用 Windows PowerShell 2.0 引擎
ms.openlocfilehash: e00fb71c7fc32f5b48bc17ef5b25f910a846c893
ms.sourcegitcommit: 1748b2bdfae81d98097962c6c25c25df4bced1d8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84262608"
---
# <a name="using-the-windows-powershell-20-engine"></a>使用 Windows PowerShell 2.0 引擎

Windows PowerShell 已設計為可回溯相容先前的版本。 針對 Windows PowerShell 2.0 撰寫的 Cmdlet、提供者、嵌入式管理單元、模組及指令碼，在新版 Windows PowerShell 中仍以同樣方式執行。 不過，Microsoft .NET Framework 4 變更了執行時間啟用原則。
針對 Windows PowerShell 2.0 撰寫並使用 Common Language Runtime (CLR) 2.0 編譯的 Windows PowerShell 主機程式，需要在使用 CLR 4.0 (或更高版本) 編譯的新版 Windows PowerShell 中修改才能執行。

Windows PowerShell 2.0 引擎只有在現有指令碼或主機程式無法執行時才會使用 ，因為其與 Windows PowerShell 5.1 不相容。 這種情況的範例包括舊版的 Exchange 或 SQL Server 模組。 這種情況應該很少見。

許多需要 Windows PowerShell 2.0 引擎的程式都會自動啟動它。 這些指示是針對需要手動啟動引擎的罕見情況。

## <a name="deprecation-and-security-concerns"></a>淘汰和安全性考量

Windows PowerShell 2.0 已於 2017 年 8 月淘汰。 如需詳細資訊，請參閱 PowerShell 部落格上的[公告][]。

Windows PowerShell 2.0 缺少第 3、4 和 5 版中新增的大量強化與安全性功能。 強烈建議，如果可以的話，請使用者避免使用。 如需詳細資訊，請參閱 [Shell 與指令碼語言安全性的比較][]和 [PowerShell ♥ Blue Team][blueteam]。

## <a name="installing-and-enabling-required-programs"></a>安裝和啟用必要的程式

啟動 Windows PowerShell 2.0 引擎之前，請啟用 Windows PowerShell 2.0 引擎和 Microsoft .NET Framework 3.5 (含 Service Pack 1)。 如需相關指示，請參閱[安裝 Windows PowerShell][]。

已安裝 Windows Management Framework 3.0 或更高版本的系統都具有所有必要元件。 不需要進一步設定。 如需安裝 Windows Management Framework 的相關資訊，請參閱[安裝與設定 WMF][]。

## <a name="how-to-start-the-windows-powershell-20-engine"></a>如何啟動 Windows PowerShell 2.0 引擎

當您啟動 Windows PowerShell 時，預設會啟動最新版本。 若要啟動含 Windows PowerShell 2.0 引擎的 Windows PowerShell，請使用 `PowerShell.exe` 的 Version 參數。 您可以在任何命令提示字元 (包括 Windows PowerShell 和 Cmd.exe) 執行命令。

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>如何啟動含 Windows PowerShell 2.0 引擎的遠端工作階段

若要在遠端工作階段中執行 Windows PowerShell 2.0 引擎，請在載入 Windows PowerShell 2.0 引擎的遠端電腦上建立工作階段設定 (又稱_端點_)。 工作階段組態會儲存於遠端電腦上，而且任何授權使用者皆可用來建立使用 Windows PowerShell 2.0 引擎的工作階段。

這是通常由系統管理員所執行的進階工作。

下列程序使用 [Register-PSSessionConfiguration][] Cmdlet 的 **PSVersion** 參數，來建立使用 Windows PowerShell 2.0 引擎的工作階段設定。 您也可以使用 [New-PSSessionConfigurationFile][] Cmdlet 的 **PowerShellVersion** 參數來建立可載入 Windows PowerShell 2.0 引擎之工作階段的工作階段設定檔，以及使用 [Set-PSSessionConfiguration][] 參數的 **PSVersion** 參數來將工作階段設定變更為使用 Windows PowerShell 2.0 引擎。

如需有關工作階段設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files][]。
如需有關設定和安全性等工作階段設定的詳細資訊，請參閱 [about_Session_Configurations][]。

### <a name="to-start-a-remote-windows-powershell-20-session"></a>啟動遠端 Windows PowerShell 2.0 工作階段

1. 若要建立需要 Windows PowerShell 2.0 引擎的工作階段設定，請使用 `Register-PSSessionConfiguration` cmdlet 的 **PSVersion** 參數 (值為 `2.0`)。
   在「伺服器端」或連線接收端的電腦上，執行此命令。

   下列範例命令會在 Server01 電腦上建立 PS2 工作階段設定。 若要執行此命令，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. 若要在使用 PS2 工作階段設定的 Server01 電腦上建立工作階段，請使用建立遠端工作階段之 Cmdlet (例如 `New-PSSession cmdlet) 的 **ConfigurationName** 參數。

   當使用工作階段設定的工作階段啟動時，會將 Windows PowerShell 2.0 引擎自動載入工作階段。

   下列命令會在 Server01 電腦上啟動使用 PS2 工作階段設定的工作階段。 命令會將工作階段儲存於 `$s` 變數中。

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>如何使用 Windows PowerShell 2.0 引擎啟動背景工作

若要使用 Windows PowerShell 2.0 引擎啟動背景工作，請使用 [Start-Job][] Cmdlet 的 **PSVersion** 參數。

下列命令會使用 Windows PowerShell 2.0 引擎啟動背景工作。

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

如需背景工作的詳細資訊，請參閱 [about_Jobs][]。

<!-- link references -->
[公告]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Shell 與指令碼語言安全性的比較]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[安裝 Windows PowerShell]: install/Installing-Windows-PowerShell.md
[安裝與設定 WMF]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfiguration
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
