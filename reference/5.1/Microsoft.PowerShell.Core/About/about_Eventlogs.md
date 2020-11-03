---
description: Windows PowerShell 會建立名為 "Windows PowerShell" 的 Windows 事件記錄檔，以記錄 Windows PowerShell 事件。 您可以在事件檢視器中或使用取得事件的 Cmdlet （例如 Cmdlet）來查看此記錄檔 `Get-EventLog` 。 根據預設，Windows PowerShell 引擎和提供者事件會記錄在事件記錄檔中，但您可以使用事件記錄檔喜好設定變數來自訂事件記錄檔。 例如，您可以新增有關 Windows PowerShell 命令的事件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208040"
---
# <a name="about-eventlogs"></a>關於檢視

## <a name="short-description"></a>簡短描述

Windows PowerShell 會建立名為 "Windows PowerShell" 的 Windows 事件記錄檔，以記錄 Windows PowerShell 事件。 您可以在事件檢視器中或使用取得事件的 Cmdlet （例如 Cmdlet）來查看此記錄檔 `Get-EventLog` 。 根據預設，Windows PowerShell 引擎和提供者事件會記錄在事件記錄檔中，但您可以使用事件記錄檔喜好設定變數來自訂事件記錄檔。 例如，您可以新增有關 Windows PowerShell 命令的事件。

## <a name="long-description"></a>完整描述

Windows PowerShell 事件記錄檔會記錄 Windows PowerShell 作業的詳細資料，例如啟動和停止程式引擎，以及啟動和停止 Windows PowerShell 提供者。 您也可以記錄有關 Windows PowerShell 命令的詳細資料。

Windows PowerShell 事件記錄檔位於 [應用程式和服務記錄檔] 群組中。 Windows PowerShell 記錄是不使用 Windows 事件技術的傳統事件記錄檔。 若要查看記錄，請使用針對傳統事件記錄檔設計的指令程式，例如 `Get-EventLog` 。

## <a name="viewing-the-windows-powershell-event-log"></a>查看 Windows PowerShell 事件記錄檔

您可以在事件檢視器中或使用和 Cmdlet 來查看 Windows PowerShell 事件記錄檔 `Get-EventLog` `Get-WmiObject` 。 若要查看 Windows PowerShell 記錄檔的內容，請輸入：

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

若要檢查事件和其屬性，請使用 `Sort-Object` Cmdlet、 `Group-Object` Cmdlet，以及 Cmdlet `Format`)  (指令程式 `Format` 。

例如，若要查看記錄中依事件識別碼分組的事件，請輸入：

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

或者，輸入：

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

若要查看所有傳統事件記錄檔，請輸入：

```powershell
Get-EventLog -List
```

您也可以使用 `Get-WmiObject` Cmdlet，以 (WMI) 類別來檢查事件記錄檔，以使用事件相關的 Windows Management Instrumentation。 例如，若要查看事件記錄檔的所有屬性，請輸入：

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

若要尋找 Win32 事件相關 WMI 類別，請輸入：

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

如需詳細資訊，請輸入 "Get-help Get-EventLog" 和 "Get-help >get-wmiobject"。

## <a name="selecting-events-for-the-windows-powershell-event-log"></a>選取 Windows PowerShell 事件記錄檔的事件

您可以使用事件記錄檔喜好設定變數來判斷 Windows PowerShell 事件記錄檔中記錄的事件。

有六個事件記錄檔喜好設定變數：這三個記錄元件各有兩個變數：引擎 (Windows PowerShell 程式) 、提供者及命令。 LifeCycleEvent 變數會記錄正常開始和停止事件。 健全狀況變數會記錄錯誤事件。

下表列出事件記錄檔喜好設定變數。

|變數                  |描述                                    |
|--------------------------|-----------------------------------------------|
|$LogEngineLifeCycleEvent  |記錄 PowerShell 的啟動和停止          |
|$LogEngineHealthEvent     |記錄 PowerShell 程式錯誤                 |
|$LogProviderLifeCycleEvent|記錄 PowerShell 提供者的啟動和停止|
|$LogProviderHealthEvent   |記錄 PowerShell 提供者錯誤                |
|$LogCommandLifeCycleEvent |記錄命令的開始和完成   |
|$LogCommandHealthEvent    |記錄命令錯誤                            |

 (如需 Windows PowerShell 提供者的詳細資訊，請參閱 [about_Providers](about_Providers.md)。 ) 

依預設，只會啟用下列事件種類：

* $LogEngineLifeCycleEvent
* $LogEngineHealthEvent
* $LogProviderLifeCycleEvent
* $LogProviderHealthEvent

若要啟用事件種類，請將該事件種類的喜好設定變數設定為 $true。 例如，若要啟用命令生命週期事件，請輸入：

```powershell
$LogCommandLifeCycleEvent
```

或者，輸入：

```powershell
$LogCommandLifeCycleEvent = $true
```

若要停用事件種類，請將該事件種類的喜好設定變數設定為 $false。 例如，若要停用命令生命週期事件，請輸入：

```powershell
$LogProviderLifeCycleEvent = $false
```

除了指出 Windows PowerShell 引擎和核心提供者已啟動的事件之外，您還可以停用任何事件。 這些事件會在執行 Windows PowerShell 設定檔之前，以及在主機程式準備接受命令之前產生。

變數設定只適用于目前的 Windows PowerShell 會話。
若要將它們套用至所有 Windows PowerShell 會話，請將它們新增至您的 Windows PowerShell 設定檔。

## <a name="logging-module-events"></a>記錄模組事件

從 Windows PowerShell 3.0 開始，您可以將模組和嵌入式管理單元的 LogPipelineExecutionDetails 屬性設定為 TRUE，以記錄 Windows PowerShell 模組和嵌入式管理單元中的 Cmdlet 和函式的執行事件。 在 Windows PowerShell 2.0 中，這項功能僅適用于嵌入式管理單元。

當 LogPipelineExecutionDetails 屬性值為 TRUE (`$true`) 時，Windows PowerShell 會將會話中的 Cmdlet 和函式執行事件寫入事件檢視器中的 Windows PowerShell 記錄。 這項設定只會在目前的會話中生效。

若要啟用模組中的 Cmdlet 和函式的執行事件記錄，請使用下列命令順序。

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

若要在嵌入式管理單元中啟用 Cmdlet 的執行事件記錄，請使用下列命令順序。

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

若要停用記錄，請使用相同的命令順序將屬性值設定為 FALSE (`$false`) 。

您也可以使用 [開啟模組記錄] 群組原則設定來啟用和停用模組和嵌入式管理單元記錄。 原則值包含模組和嵌入式管理單元名稱的清單。 支援萬用字元。

針對模組設定 [開啟模組記錄] 時，模組的 LogPipelineExecutionDetails 屬性值在所有會話中都是 TRUE，而且無法變更。

[開啟模組記錄] 群組原則設定位於下列群組原則路徑：

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

使用者設定原則的優先順序高於電腦設定原則，而這兩個原則會優先考慮模組和嵌入式管理單元的 LogPipelineExecutionDetails 屬性值。

如需此群組原則設定的詳細資訊，請參閱 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)。

## <a name="security-and-auditing"></a>安全性和審核

Windows PowerShell 事件記錄檔的設計目的是要指出活動並提供作業詳細資料來進行疑難排解。

不過，就像大部分的 Windows 應用程式事件記錄一樣，Windows PowerShell 的事件記錄檔並非設計成安全的。 它不應該用來審核安全性或記錄機密或專屬資訊。

事件記錄檔是設計來供使用者讀取和瞭解。 使用者可以讀取和寫入記錄檔。 惡意使用者可以讀取本機或遠端電腦上的事件記錄檔、記錄 false 資料，然後防止記錄其活動。

## <a name="notes"></a>備忘稿

模組作者的作者可以將記錄功能新增至其模組。 如需詳細資訊，請參閱 [撰寫 Windows PowerShell 模組](/powershell/scripting/developer/module/writing-a-windows-powershell-module)。

## <a name="see-also"></a>另請參閱

[Get-EventLog](xref:Microsoft.PowerShell.Management.Get-EventLog)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Preference_Variables](about_Preference_Variables.md)
