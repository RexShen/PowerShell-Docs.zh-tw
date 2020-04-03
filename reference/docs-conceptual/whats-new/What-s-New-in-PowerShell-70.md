---
title: PowerShell 7.0 的新功能
description: PowerShell 7.0 中發行的新功能與變更
ms.date: 03/04/2020
ms.openlocfilehash: 84631d9fa169c8d1b4cd4dd23eb3d7c1bca120bb
ms.sourcegitcommit: b0966d61293e28ecdb929c5065be9760884e4e7d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80263130"
---
# <a name="whats-new-in-powershell-70"></a>PowerShell 7.0 的新功能

PowerShell 7.0 為開放原始碼、跨平台 (Windows、macOS 和 Linux) 的 PowerShell 版本，建置來管理異質環境和混合式雲端。

在此版本中，我們引進了許多新功能，包括：

- 使用 `ForEach-Object -Parallel` 進行管線平行處理
- 新增運算子：
  - 三元運算子：`a ? b : c`
  - 管線鏈結運算子：`||` 和 `&&`
  - Null 條件運算子：`??` 和 `??=`
- 簡化的動態錯誤檢視和 `Get-Error` Cmdlet，可讓您更輕鬆地調查錯誤
- 相容性階層，可讓使用者在隱含的 Windows PowerShell 工作階段中匯入模組
- 自動新版本通知
- 能夠直接從 PowerShell 7 叫用 DSC 資源 (實驗性)

若要查看完整的功能和修正清單，請參閱[變更記錄](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md) \(英文\)。

## <a name="where-can-i-install-powershell"></a>我可以在哪裡安裝 PowerShell？

PowerShell 7 在 x64 上目前支援下列作業系統，包括：

- Windows 8.1 和 10
- Windows Server 2012、2012 R2、2016 及 2019
- macOS 10.13+
- Red Hat Enterprise Linux (RHEL) / CentOS 7
- Fedora 30+
- Debian 9
- Ubuntu LTS 16.04+
- Alpine Linux 3.8+

此外，PowerShell 7.0 支援 Debian、Ubuntu 和 ARM64 Alpine Linux 的 ARM32 和 ARM64 變體。

請查看適用於您慣用作業系統 [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7)、[macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) 或 [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) 的安裝指示。

雖然尚未正式支援，但該社群也會提供適用於 [Arch](https://aur.archlinux.org/packages/powershell/) 和 Kali Linux 的套件。

> [!NOTE]
> Debian 10 和 CentOS 8 目前不支援 WinRM 遠端處理。 如需設定 SSH 型遠端處理的詳細資訊，請參閱[透過 SSH 的 PowerShell 遠端處理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7)。

如需更多有關支援的作業系統和支援週期的最新資訊，請參閱 [PowerShell 支援週期](/powershell/scripting/powershell-support-lifecycle?view=powershell-7)。

## <a name="running-powershell-7"></a>執行中的 PowerShell 7

PowerShell 7 會安裝到新目錄，並與 Windows PowerShell 5.1 並存執行。 針對 PowerShell Core 6.x，PowerShell 7 會就地升級並移除 PowerShell Core 6.x。

- PowerShell 7 會安裝到 `%programfiles%\PowerShell\7`
- 系統會在 `$env:PATH` 中新增 `%programfiles%\PowerShell\7` 資料夾

PowerShell 7 安裝程式套件會升級舊版的 PowerShell Core 6.x：

- Windows 上的 PowerShell Core 6.x：`%programfiles%\PowerShell\6` 已由 `%programfiles%\PowerShell\7` 取代
- Linux：`/opt/microsoft/powershell/6` 已由 `/opt/microsoft/powershell/7` 取代
- macOS：`/usr/local/microsoft/powershell/6` 已由 `/usr/local/microsoft/powershell/7` 取代

> [!NOTE]
> 在 Windows PowerShell 中，啟動 PowerShell 的可執行檔名稱為 `powershell.exe`。 在版本 6 和更新版本中，已將這個可執行檔變更為支援並存執行。 啟動 PowerShell 7 的新可執行檔為 `pwsh.exe`。 預覽版將以 `pwsh-preview` (而不是 `pwsh`) 就地保留於 7-preview 目錄下。

## <a name="improved-backwards-compatibility-with-windows-powershell"></a>已改善與 Windows PowerShell 的回溯相容性

PowerShell 7.0 會標記要移轉到 .NET Core 3.1，大幅提高與現有的 Windows PowerShell 模組的回溯相容性。 這在 Windows 上包含許多模組，其需要 `Out-GridView` 和 `Show-Command` 之類的 GUI 功能，以及 Windows 隨附的許多角色管理模組。

針對 Windows，已將新的切換參數 **UseWindowsPowerShell** 新增至 `Import-Module`。 此參數會在 PowerShell 7 中建立 Proxy 模組，以使用本機 Windows PowerShell 處理序，隱含地執行該模組中包含的所有 Cmdlet。 如需詳細資訊，請參閱 [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7)。

如需哪些 Microsoft 模組使用 PowerShell 7.0 的詳細資訊，請參閱[模組相容性表格](https://aka.ms/PSModuleCompat) \(英文\)。

## <a name="parallel-execution-added-to-foreach-object"></a>已在 ForEach-Object 中新增平行執行

`ForEach-Object` Cmdlet (會逐一查看集合中的項目) 現在具備含有新 **Parallel** 參數的內建平行處理原則。

根據預設，平行指令碼區塊會使用已啟動平行工作之呼叫者的目前工作目錄。

此範例會從本機 Windows 電腦上的 5 個系統記錄中擷取 50,000 個記錄項目：

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

**Parallel** 參數會針對每個輸入記錄名稱指定平行執行的指令碼區塊。

新的 **ThrottleLimit** 參數會限制在指定時間平行執行的指令碼區塊數目。 預設值為 5。

在指令碼區塊中，使用 `$_` 變數來代表目前的輸入物件。 使用 `$using:` 範圍，將變數參考傳遞至執行中的指令碼區塊。

如需詳細資訊，請參閱 [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7)。

## <a name="ternary-operator"></a>三元運算子

PowerShell 7.0 引進了三元運算子，其行為類似簡化的 `if-else` 陳述式。
PowerShell 的三元運算子會根據 C# 三元運算子語法嚴密地進行模型化：

```
<condition> ? <if-true> : <if-false>
```

條件運算式一律會進行評估，並將結果轉換成**布林值**，以判斷下一個要評估的分支：

- 如果 `<condition>` 運算式為 True，就會執行 `<if-true>` 運算式
- 如果 `<condition>` 運算式為 False，就會執行 `<if-false>` 運算式

例如：

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

在此範例中，如果路徑存在，就會顯示 **Path exists**。 如果路徑不存在，則會顯示 **Path not found**。

如需詳細資訊，請參閱[關於 If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7)。

## <a name="pipeline-chain-operators"></a>管線鏈結運算子

PowerShell 7 會實作 `&&` 和 `||` 運算子，有條件地鏈結管線。 這些運算子在 PowerShell 中稱為「管線鏈結運算子」，類似於 **Bash** 和 **Zsh** 等殼層中的 AND 和 OR 清單，以及 Windows 命令殼層 (**cmd.exe**) 中的條件式處理符號。

如果左側管線成功，`&&` 運算子就會執行右側管線。 反過來說，如果左側管線失敗，`||` 運算子就會執行右側管線。

> [!NOTE]
> 這些運算子會使用 `$?` 和 `$LASTEXITCODE` 變數來判斷管線是否失敗。 這可讓您將其與原生命令搭配使用，而不只是與 Cmdlet 或函式搭配使用。

在這裡，第一個命令成功，且會執行第二個命令：

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

在這裡，第一個命令失敗，且不會執行第二個命令：

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

在這裡，第一個命令成功，且不會執行第二個命令：

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

在這裡，第一個命令失敗，因此會執行第二個命令：

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

如需詳細資訊，請參閱[關於管線鏈結運算子](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7)。

## <a name="null-coalescing-assignment-and-conditional-operators"></a>Null 聯合、指派和條件運算子

PowerShell 7 包含 Null 聯合運算子 `??`、Null 條件式指派 `??=`，以及 Null 條件式成員存取運算子 `?.` 和 `?[]`。

### <a name="null-coalescing-operator-"></a>Null 聯合運算子 ??

Null 聯合運算子 `??` 會傳回其左側運算元的值 (如果不是 Null)。
否則會評估右側運算元，並傳回其結果。 如果左側運算元評估為非 Null，則 `??` 運算子不會評估右側運算元。

```powershell
$x = $null
$x ?? 100
100
```

在下列範例中，將不會評估右側運算元：

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a>Null 條件式指派運算子 ??=

Null 條件式指派運算子 `??=` 只有當左側運算元評估為 Null 時，才會將右側運算元的值指派給左側運算元。 如果左側運算元評估為非 Null，則 `??=` 運算子不會評估右側運算元。

```powershell
$x = $null
$x ??= 100
$x
100
```

在下列範例中，將不會評估右側運算元：

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a>Null 條件式成員存取運算子 ?. 和 ?[] (實驗性)

> [!NOTE]
> 這是名為 **PSNullConditionalOperators** 的實驗性功能。 深入了解[關於實驗性功能](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)。

Null 條件運算子只有在其運算元評估為非 Null 時，才會允許對該運算元進行成員存取 `?.` 或元素存取 `?[]`；否則就會傳回 Null。

> [!NOTE]
> 由於 PowerShell 允許 `?` 作為變數名稱的一部分，因此，使用這些運算子時需要變數名稱的型式規格。 因此，必須在 `${a}` 之類的變數名稱前後，或是當 `?` 為變數名稱 `${a?}` 的一部分時，使用 `{}`。

在下列範例中，會傳回成員屬性 **Status** 的值：

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

下列範例將傳回 Null，而不會嘗試存取成員名稱 **Status**：

```powershell
$service = $Null
${Service}?.status
```

同樣地，使用 `?[]`，將會傳回元素的值：

```powershell
$a = 1..10
${a}?[0]
1
```

此外，當運算元為 Null 時，就不會存取元素，且會傳回 Null：

```powershell
$a = $null
${a}?[0]
```

如需詳細資訊，請參閱[關於運算元](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7)。

## <a name="new-view-conciseview-and-cmdlet-get-error"></a>新增 ConciseView 檢視和 Get-Error Cmdlet

已改善錯誤訊息的顯示，以使用新的預設檢視 **ConciseView** 來增強互動式與指令碼錯誤的可讀性。 使用者可以透過喜好設定變數 `$ErrorView` 來選取這些檢視。

使用 **ConciseView**，如果錯誤不是來自指令碼或剖析器錯誤，則會是單行錯誤訊息：

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

如果錯誤發生於指令碼執行期間或是剖析錯誤，PowerShell 就會傳回包含該錯誤的多行錯誤訊息，以及顯示錯誤在該行中所在位置的指標和錯誤訊息。 如果終端機不支援 ANSI 色彩逸出序列 (VT100)，則不會顯示色彩。

![指令碼的錯誤顯示](./media/What-s-New-in-PowerShell-70/myscript-error.png)

PowerShell 7 中的預設檢視為 **ConciseView**。 先前的預設檢視為 **NormalView**，而使用者可以藉由設定喜好設定變數 `$ErrorView` 來選取。

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> 已將新的屬性 **ErrorAccentColor** 新增至 `$Host.PrivateData`，以支援變更錯誤訊息的輔色。

新的 Cmdlet `Get-Error` 會在需要時，提供完整錯誤的全面詳細檢視。
根據預設，此 Cmdlet 會顯示最後發生之錯誤的完整詳細資料，包括內部例外狀況。

![顯示自 Get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

`Get-Error` Cmdlet 支援使用內建變數 `$Error` 來從管線輸入。
`Get-Error` 顯示所有透過管道傳送的錯誤。

```powershell
$Error | Get-Error
```

`Get-Error` Cmdlet 支援 **Newest** 參數，可讓您指定希望顯示目前工作階段中的錯誤數目。

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

如需詳細資訊，請參閱 [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7)。

## <a name="new-version-notification"></a>新版本通知

PowerShell 7 會使用更新通知來警示使用者是否有 PowerShell 的更新存在。
PowerShell 會以每天一次的頻率來查詢線上服務，以判斷是否有較新版本可供使用。

> [!NOTE]
> 更新檢查會在指定的 24 小時期間內的第一個工作階段中發生。 基於效能考量，更新檢查會在工作階段開始後的 3 秒開始。 只有在後續的工作階段開始時，才會顯示通知。

根據預設，PowerShell 會依據其版本/分支，訂閱兩個不同通知通道的其中一個。 支援、正式推出 (GA) 的 PowerShell 版本只會傳回已更新 GA 版本的通知。 預覽和候選版 (RC) 版本會通知預覽、RC 和 GA 版本的更新。

更新通知行為可以使用 `$Env:POWERSHELL_UPDATECHECK` 環境變數來變更。 支援下列值：

- **Default** 與未定義 `$Env:POWERSHELL_UPDATECHECK` 相同
  - GA 版本會通知 GA 版本的更新
  - 預覽/RC 版本會通知 GA 和預覽版本的更新
- **Off** 會關閉更新通知功能
- **LTS** 只會通知長期維護 (LTS) GA 版本的更新

> [!NOTE]
> 環境變數 `$Env:POWERSHELL_UPDATECHECK` 在第一次設定之後才會存在。

僅針對 `LTS` 版本設定版本通知：

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

將版本通知設定為 `Default` 行為：

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

如需詳細資訊，請參閱[關於更新通知](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7)。

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a>使用 Invoke-DSCResource 新增 DSC 資源支援 (實驗性)

> [!NOTE]
> 這是名為 **PSDesiredStateConfiguration.InvokeDscResource** 的實驗性功能。 深入了解[關於實驗性功能](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)。

`Invoke-DscResource` Cmdlet 會執行指定之 PowerShell Desired State Configuration (DSC) 資源的方法。

此 Cmdlet 會直接叫用 DSC 資源，而不需建立設定文件。 使用此 Cmdlet，設定管理產品就能使用 DSC 資源來管理 Windows 或 Linux。 當 DSC 引擎在啟用了偵錯的情況下執行時，此 Cmdlet 也會啟用資源的偵錯。

此命令會叫用名為 Log 的資源 **Set** 方法，並指定 **Message** 屬性。

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

如需詳細資訊，請參閱 [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7)。

## <a name="breaking-changes-and-improvements"></a>中斷性變更和改進

### <a name="breaking-changes"></a>重大變更

- 讓更新通知支援 LTS 和預設通道 (#11132)
- 更新 Test-Connection，使其運作方式與 Windows PowerShell 中的更相似 (#10697) (感謝 @vexx32！)
- 針對 ParenExpression、SubExpression 及 ArrayExpression 保留 $? (#11040)
- 將工作目錄設定為 Start-Job 中目前的目錄 (#10920) (感謝 @iSazonov！)
- 讓 $PSCulture 一律能夠反映工作階段內的文化特性變更 (#10138) (感謝 @iSazonov！)

### <a name="engine-updates-and-fixes"></a>引擎更新與修正

- 針對遠端案例之中斷點 API 的改進 (#11312)
- 修正會流失到另一個 Runspace 的 PowerShell 類別定義 (#11273)
- 修正 7.0.0-Preview1 中新增之 FirstOrDefault 基本類型所導致的格式迴歸 (#11258)
- 要在 PS7 遙測中追蹤的其他 Microsoft 模組 (#10751)
- 讓核准的功能成為非實驗性的 (#11303)
- 更新 ConciseView 以使用 TargetObject (如果適用) (#11075)
- 修正 CompletionCompleters 公用方法中的 NullReferenceException (#11274)
- 修正非 Windows 平台上的 Apartment 執行緒狀態檢查 (#11301)
- 更新設定 PSModulePath 以串連處理序和電腦環境變數 (#11276)
- 將 .NET Core 改為 3.1.0 (#11260)
- 修正 $env:PATH 前面的 $PSHOME 偵測 (#11141)
- 允許 pwsh 繼承 $env:PSModulePath，讓 powershell.exe 能夠正確啟動 (#11057)
- 移至 .NET Core 3.1 Preview 1 (#10798)
- 在檔案系統提供者中重構重新剖析標記檢查 (#10431) (感謝 @iSazonov！)
- 在指令碼記錄中使用 0x23CE 字元取代 CR 和新行 (#10616)
- 從 AppDomain.CurrentDomain.ProcessExit 取消註冊事件處理常式，以修正資源流失 (#10626)
- 新增對 ActionPreference.Break 的支援，以便在產生偵錯、錯誤、資訊、進度、詳細資訊或警告訊息時中斷偵錯工具 (#8205) (感謝 @KirkMunro！)
- 能夠在不指定 .CPL 擴充功能的情況下，於 PowerShell Core 內啟動控制台增益集。 (#9828)
- 支援 -split 運算子 (#8960) 中有負數 (感謝 @ece-jacob-scott！)

### <a name="general-cmdlet-updates-and-fixes"></a>一般 Cmdlet 更新與修正

- 修正在 UnixStat 實驗性功能中設定檔案變更日期的 Raspbian 問題 (#11313)
- 將 -AsPlainText 新增至 ConvertFrom-SecureString (#11142)
- 已新增 WinCompat 的 WindowsPS 版本檢查 (#11148)
- 修正某些 WinCompat 案例中的錯誤報告 (#11259)
- 新增原生的二進位解析程式 (#11032) (感謝 @iSazonov！)
- 更新字元寬度的計算，以正確遵循 CJK 字元 (#11262)
- 針對 macOS 新增 Unblock-File (#11137)
- 修正 Get-PSCallStack 中的迴歸 (#11210) (感謝 @iSazonov！)
- 移除使用 Job Cmdlet 時自動載入 ScheduledJob 模組的功能 (#11194)
- 將 OutputType 新增至 Get-Error Cmdlet，並保留原始類型名稱 (#10856)
- 修正 SupportsVirtualTerminal 屬性中的 Null 參考 (#11105)
- 在 Get-WinEvent 中新增限制檢查 (#10648) (感謝 @iSazonov！)
- 修正命令執行階段，如此就不會在 -ErrorVariable 中填入 StopUpstreamCommandsException (#10840)
- 針對原生命令，將輸出編碼設定為 [Console]::OutputEncoding (#10824)
- 支援範例中的多行程式碼區塊 (#10776) (感謝 @Greg-Smulko！)
- 將 Culture 參數新增至 Select-String Cmdlet (#10943) (感謝 @iSazonov！)
- 以後置反斜線修正 Start-Job 工作目錄路徑 (#11041)
- ConvertFrom-Json：預設會將集合解除包裝 (#10861) (感謝 @danstur！)
- 針對含有 -CaseSensitive 和 -AsHashtable 參數的 Group-Object Cmdlet 使用區分大小寫的雜湊表 (#11030) (感謝 @vexx32！)
- 在重建路徑以具備正確的大小寫時，如果列舉檔案失敗，就會處理例外狀況 (#11014)
- 修正 ConciseView 以顯示 Activity，而不是 myCommand (#11007)
- 允許 Web Cmdlet 忽略 HTTP 錯誤狀態 (#10466) (感謝 @vdamewood！)
- 修正將多個 CommandInfo 透過管道傳送到 Get-Command (#10929)
- 針對 Windows 重新新增 Get-Counter Cmdlet (#10933)
- 讓 ConvertTo-Json 將 [AutomationNull]::Value 和 [NullString]::Value 視為 $null (#10957)
- 從 ipv6 位址移除括弧以進行 SSH 遠端處理 (#10968)
- 修正當傳送至 pwsh 的命令只是空白時所造成的損毀 (#10977)
- 已新增跨平台的 Get-Clipboard 和 Set-Clipboard (#10340)
- 修正將系統檔案物件的原始路徑設定為不具額外的後置斜線 (#10959)
- 針對 ConvertTo-Json 支援 $null (#10947)
- 在 Windows 上重新新增 Out-Printer 命令 (#10906)
- 修正含有空格的 Start-Job -WorkingDirectory (#10951)
- 當 PSConfiguration.cs 中的設定為 Null 時，會傳回預設值 (#10963) (感謝 @iSazonov！)
- 將 IO 例外狀況處理為非終止 (#10950)
- 新增 GraphicalHost 組件，以啟用 Out-GridView、Show-Command 及 Get-Help -ShowWindow (#10899)
- 在 Get-HotFix 中透過管線取得 ComputerName (#10852) (感謝 @kvprasoon！)
- 修正參數的 Tab 鍵自動完成功能，如此便能顯示可用的一般參數 (#10850)
- 修正 GetCorrectCasedPath()，以便先檢查是否傳回任何系統檔案項目，然後再呼叫 First() (#10930)
- 將工作目錄設定為 Start-Job 中目前的目錄 (#10920) (感謝 @iSazonov！)
- 將 TabExpansion2 變更為不需要 -CursorColumn，並視為 $InputScript.Length (#10849)
- 處理主機可能無法傳回螢幕之資料列或資料行的情況 (#10938)
- 修正針對不支援之主機的輔色使用方式 (#10937)
- 重新新增 Update-List 命令 (#10922)
- 更新適用於 Clear-RecycleBin 的 FWLink (#10925)
- 在 Tab 鍵自動完成期間，如果無法讀取檔案屬性，即會略過檔案 (#10910)
- 針對 Windows 重新新增 Clear-RecycleBin (#10909)
- 新增 `$env:__SuppressAnsiEscapeSequences`，以控制是否要在輸出中使用 VT 逸出序列 (#10814)
- 新增 -NoEmphasize 參數，以便為 Select-String 輸出上色 (#8963) (感謝 @derek-xia！)
- 重新新增 Get-HotFix Cmdlet (#10740)
- 讓 Add-Type 可用於裝載 PowerShell 的應用程式中 (#10587)
- 在 LanguagePrimitives.IsNullLike() 中使用更有效率的評估順序 (#10781) (感謝 @vexx32！)
- 以 Format-Hex 改善混合式集合透過管道傳送的輸入，以及透過管道傳送之輸入串流的處理方式 (#8674) (感謝 @vexx32！)
- 當值不符合預期的類型時，在 SSHConnection 雜湊表中使用類型轉換 (#10720) (感謝 @SeeminglyScience！)
- 修正設定 -TotalCount 時 Get-Content -ReadCount 0 的行為 (#10749) (感謝 @eugenesmlv！)
- 重寫 Get-WinEvent 中的拒絕存取錯誤訊息 (#10639) (感謝 @iSazonov！)
- 針對列舉或類型條件約束的變數指派啟用 Tab 鍵自動完成 (#10646)
- 移除未使用且會導致格式問題的 SourceLength 遠端屬性 (#10765)
- 將 -Delimiter 參數新增至 ConvertFrom-StringData (#10665) (感謝 @steviecoaster！)
- 搭配 SSH 使用 Invoke-Command 時，為 ScriptBlock 新增位置參數 (#10721) (感謝 @machgo！)
- 如果有多行，但沒有 ConciseView 的指令碼名稱，則會顯示行內容資訊 (#10746)
- 將對 \\wsl$\ 路徑的支援新增至檔案系統提供者 (#10674)
- 在剖析器中針對 TokenKind.QuestionMark 新增遺漏的權杖文字 (#10706)
- 將每個 ForEach-Object -Parallel 執行中指令碼的目前工作目錄設定為與呼叫指令碼相同的位置。 (#10672)
- 針對 FindFirstStreamW 和 FindNextStreamW API，使用 Kernell32.dll 取代 api-ms-win-core-file-l1-2-2.dll (#10680) (感謝 @iSazonov！)
- 調整協助將指令碼格式化，以使其更能容忍 StrictMode (#10563)
- 將 -SecurityDescriptorSDDL 參數新增至 New-Service (#10483) (感謝 @kvprasoon！)
- 移除資訊輸出，合併 Test-Connection 中 Ping 的使用方式 (#10478) (感謝 @vexx32！)
- 不需存取，即可讀取特定的重新剖析點 (#10662) (感謝 @iSazonov！)
- 將 Clear-Host 輸出指向終端機 (#10681) (感謝 @iSazonov！)
- 使用 Format-Table 和 -Property 重新新增新行以利分組 (#10653)
- 在 Get-Random 上，從 -InputObject 中移除 [ValidateNotNullOrEmpty]，以允許空字串 (#10644)
- 將建議系統字串距離演算法設定為不區分大小寫 (#10549) (感謝 @iSazonov！)
- 修正 ForEach-Object -Parallel 輸入處理中的 Null 參考例外狀況 (#10577)
- 新增 PowerShell Core 群組原則定義 (#10468)
- 更新主控台主機，以支援可組合性案例中所使用的 XTPUSHSGR/XTPOPSGR VT 控制順序。 (#10208)
- 將 WorkingDirectory 參數新增至 Start-Job (#10324) (感謝 @davinci26！)
- 移除導致中斷點變更錯誤複寫到主機 Runspace 偵錯工具的事件處理常式 (#10503) (感謝 @KirkMunro！)
- 在 Microsoft.PowerShell.Commands.NativeMethods P/Invoke API 中，使用 Kernell32.dll 取代 api-ms-win-core-job-12-1-0.dll (#10417) (感謝 @iSazonov！)
- 修正變數指派的 New-Service 和 -OutVariable 中的錯誤輸出 (#10444) (感謝 @kvprasoon！)
- 修正結束代碼、命令列參數和含有空格之路徑的全域工具問題 (#10461)
- 將遞迴修正到 OneDrive - 變更 FindFirstFileEx() 以使用 SafeFindHandle 類型 (#10405)
- 如果 NVDA 螢幕助讀程式為作用中，即會略過在 Windows 上自動載入 PSReadLine (#10385)
- 將使用 PowerShell 建置的模組版本增加至 7.0.0.0 (#10356)
- 新增如果已經存在相同名稱的類型，即會在 Add-Type 中擲回錯誤 (#9609) (感謝 @iSazonov！)

### <a name="performance"></a>效能

- 避免在 Parser.SaveError 中使用 Closure (#11006)
- 改善在建立新 Regex 執行個體時的快取 (#10657) (感謝 @iSazonov！)
- 改善從 types.ps1xml、typesV3.ps1xml 及 GetEvent.types.ps1xml 處理 PowerShell 內建類型資料 (#10898)
- 更新 PSConfiguration.ReadValueFromFile，使其變得更快速且記憶體更有效率 (#10839)
- 新增適用於 Runspace 初始化的次要效能改善 (#10569) (感謝 @iSazonov！)
- 讓 ForEach-Object 能夠更快速地適用於其常用案例 (#10454)，並使用多個 Runspace 來修正 ForEach-Object -Parallel 效能問題 (#10455)

### <a name="code-cleanup"></a>程式碼清除

- 變更註解和元素文字以符合 Microsoft 標準 (#11304)
- 清除 Compiler.cs 中的樣式問題 (#10368) (感謝 @iSazonov！)
- 針對 CommaDelimitedStringCollection 移除未使用的類型轉換器 (#11000) (感謝 @iSazonov！)
- 清除 InitialSessionState.cs 中的樣式 (#10865) (感謝 @iSazonov！)
- 針對 PSSession 類別進行程式碼清除 (#11001)
- 移除無法運作的「當 Get-Help 第一次執行時，從 Get-Help 中執行 Update-Help」功能 (#10974)
- 修正樣式問題 (#10998) (感謝 @iSazonov！)
- 清除：使用內建類型別名 (#10882) (感謝 @iSazonov！)
- 移除未使用的設定索引鍵 ConsolePrompting，並避免在查詢 ExecutionPolicy 設定時建立不必要的字串 (#10985)
- 停用每日組建的更新通知檢查 (#10903) (感謝 @bergmeister！)
- 恢復 #10338 中遺失的偵錯 API (#10808)
- 移除不再使用的 WorkflowJobSourceAdapter 參考 (#10326) (感謝 @KirkMunro！)
- 藉由修正 PreserveSig 屬性來清除捷徑清單程式碼中的 COM 介面 (#9899) (感謝 @weltkante！)
- 新增註解，以描述為什麼 -ia 不是 -InformationAction 一般參數的別名 (#10703) (感謝 @KirkMunro！)
- 將 InvokeCommandCmdlet.cs 重新命名為 InvokeExpressionCommand.cs (#10659) (感謝 @kilasuit！)
- 新增與更新通知相關的次要程式碼清除 (#10698)
- 從遠端安裝指令碼移除即將淘汰的工作流程邏輯 (#10320) (感謝 @KirkMunro！)
- 更新說明格式以使用適當的大小寫 (#10678) (感謝 @tnieto88！)
- 清除認可中過去一個月發生的 CodeFactor 樣式問題 (#10591) (感謝 @iSazonov！)
- 修正 PSTernaryOperator 實驗性功能描述中的打字錯誤 (#10586) (感謝 @bergmeister！)
- 將 ActionPreference.Suspend 列舉值轉換為不支援的保留狀態，並在喜好設定變數中移除使用 ActionPreference.Ignore 的限制 (#10317) (感謝 @KirkMunro！)
- 使用 List<T> 取代 ArrayList，以取得更容易閱讀且可靠的程式碼，而不需變更功能 (#10333) (感謝 @iSazonov！)
- 對 TestConnectionCommand 進行程式碼樣式修正 (#10439) (感謝 @vexx32！)
- 清除 AutomationEngine，並移除額外的 SetSessionStateDrive 方法呼叫 (#10416) (感謝 @iSazonov！)
- 針對 ConvertTo-Csv 和 ConvertFrom-Csv，將預設的 ParameterSetName 再次重新命名為 Delimiter (#10425)

### <a name="tools"></a>工具

- 新增 SDKToUse 屬性的預設設定，使其建置於 VS 中 (#11085)
- Install-Powershell.ps1：新增參數以使用 MSI 安裝 (#10921) (感謝 @MJECloud！)
- 新增 install-powershell.ps1 的基本範例 (#10914) (感謝 @kilasuit！)
- 讓 Install-PowerShellRemoting.ps1 處理 PowerShellHome 參數中的空字串 (#10526) (感謝 @Orca88！)
- 在 install-powershell.sh 中，從 /etc/lsb-release 切換到 /etc/os-release (#10773) (感謝 @Himura2la！)
- 在 Windows 上的每日版本中檢查 pwsh.exe 和 pwsh (#10738) (感謝 @centreboard！)
- 移除 installpsh-osx.sh 中不必要的點選 (#10752)
- 更新 install-powershell.ps1，以檢查已經安裝的每日組建 (#10489)

### <a name="tests"></a>測試

- 讓不可靠的 DSC 測試暫止 (#11131)
- 修正字串資料測試，以正確驗證雜湊表的索引鍵 (#10810)
- 卸載測試模組 (#11061) (感謝 @iSazonov！)
- 增加測試 URL 的重試間隔時間 (#11015)
- 更新測試以正確描述測試動作。 (#10928) (感謝 @romero126！)
- 暫時略過不穩定的測試 TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)
- 讓事件處理常式流失測試呈現穩定狀態 (#10790)
- 在 CI YAML 中同步處理大小寫 (#10767) (感謝 @RDIL！)
- 新增用於事件處理常式流失修正的測試 (#10768)
- 新增 Get-ChildItem 測試 (#10507) (感謝 @iSazonov！)
- 針對要切換到參數的測試，取代模擬兩可的語言，以確保正確性 (#10666) (感謝 @romero126！)
- 將實驗性檢查新增至 ForEach-Object -Parallel 測試 (#10354) (感謝 @KirkMunro！)
- 更新 Alpine 驗證的測試 (#10428)

### <a name="build-and-package-improvements"></a>組建和套件的改善

- 修正協調套件組建的 Nuget 套件簽署 (#11316)
- 更新 PowerShell 資源庫和 NuGet 的相依性 (#11323)
- 將 Microsoft.ApplicationInsights 從 2.11.0 改成 2.12.0 (#11305)
- 將 Microsoft.CodeAnalysis.CSharp 從 3.3.1 改成 3.4.0 (#11265)
- 更新 Debian 10 和 11 的套件 (#11236)
- 只在 RC 之前啟用實驗性功能 (#11162)
- 更新 macOS 最小版本 (#11163)
- 將 NJsonSchema 從 10.0.27 改成 10.0.28 (#11170)
- 正在針對 Preview.5 更新 README.md 中的連結和 metadata.json (#10854)
- 選取用於進行 PowerShell 所擁有之合規性測試的檔案 (#10837)
- 允許建置 win7x86 msix 套件。 (內部 10515)
- 允許將語意版本傳遞至 NormalizeVersion 函式 (#11087)
- 將 .NET Core Framework 改成 3.1-preview.3 (#11079)
- 在 /src/Modules 中，將 PSReadLine 從 2.0.0-beta5 改成 2.0.0-beta6 (#11078)
- 將 Newtonsoft.Json 從 12.0.2 改成 12.0.3 (#11037) (#11038)
- 新增 Debian 10、11 和 CentOS 8 套件 (#11028)
- 使用 ReleaseDate 欄位上傳 Build-Info Json 檔案 (#10986)
- 將 .NET Core Framework 改成 3.1-preview.2 (#10993)
- 啟用 x86 MSIX 套件的組建 (#10934)
- 更新 build.psm1 中的 dotnet SDK 安裝指令碼 URL (#10927)
- 將 Markdig.Signed 從 0.17.1 改成 0.18.0 (#10887)
- 將 ThreadJob 從 2.0.1 改成 2.0.2 (#10886)
- 更新 AppX 資訊清單和封裝模組以符合 MS Store 需求 (#10878)
- 將 PowerShell SDK 的套件參考更新為 preview.5 (內部 10295)
- 更新 ThirdPartyNotices.txt (#10834)
- 將 Microsoft.PowerShell.Native 改成 7.0.0-preview.3 (#10826)
- 將 Microsoft.ApplicationInsights 從 2.10.0 改成 2.11.0 (#10608)
- 將 NJsonSchema 從 10.0.24 改成 10.0.27 (#10756)
- 將 MacPorts 支援新增至建置系統 (#10736) (感謝 @Lucius-Q-User！)
- 將 PackageManagement 從 1.4.4 改成 1.4.5 (#10728)
- 將 NJsonSchema 從 10.0.23 改成 10.0.24 (#10635)
- 新增環境變數以區別 MSI 中的用戶端/伺服器遙測 (#10612)
- 將 PSDesiredStateConfiguration 從 2.0.3 改成 2.0.4 (#10603)
- 將 Microsoft.CodeAnalysis.CSharp 從 3.2.1 改成 3.3.1 (#10607)
- 更新為 .Net Core 3.0 RTM (#10604) (感謝 @bergmeister！)
- 更新 MSIX 封裝，使版本符合 Windows 市集需求 (#10588)
- 將 PowerShellGet 版本從 2.2 改成 2.2.1 (#10382)
- 將 PackageManagement 版本從 1.4.3 改成 1.4.4 (#10383)
- 針對 7.0.0-preview.4 更新 README.md 和 metadata.json (內部 10011)
- 將 .Net Core 3.0 版從 Preview 9 升級為 RC1 (#10552) (感謝 @bergmeister！)
- 修正 ExperimentalFeature 清單產生 (內部 9996)
- 將 PSReadLine 版本從 2.0.0-beta4 改成 2.0.0-beta5 (#10536)
- 修正發行組建指令碼以設定發行標籤
- 將 Microsoft.PowerShell.Native 的版本更新為 7.0.0-preview.2 (#10519)
- 升級為 Netcoreapp3.0 preview9 (#10484) (感謝 @bergmeister！)
- 確定每日協調組建，了解其為每日組建 (#10464)
- 更新合併的套件組建以發行每日組建 (#10449)
- 移除 AppVeyor 參考 (#10445) (感謝 @RDIL！)
- 將 NJsonSchema 版本從 10.0.22 改成 10.0.23 (#10421)
- 移除 linux-x64 組建資料夾的刪除功能，因為某些適用於 Alpine 的相依性需要該資料夾 (#10407)

### <a name="documentation-and-help-content"></a>文件和說明內容

- 針對每個版本，將變更記錄重構成一個記錄 (#11165)
- 修正適用於 PowerShell 7 線上說明文件的 FWLinks (#11071)
- 更新 CONTRIBUTING.md (#11096) (感謝 @mklement0！)
- 修正 README.md 中的安裝文件連結 (#11083)
- 將範例新增至 install-powershell.ps1 指令碼 (#11024) (感謝 @kilasuit！)
- 修正 CHANGELOG.md 中的 Select-String emphasis 和 Import-DscResource (#10890)
- 從 powershell-beginners-guide.md 移除過時的連結 (#10926)
- 合併穩定和維護變更記錄 (#10527)
- 在組建文件中更新所使用的 .NET 版本 (#10775) (感謝 @Greg-Smulko！)
- 在 powershell-beginners-guide.md 中將 MSDN 的連結取代為 docs.microsoft.com (#10778) (感謝 @iSazonov！)
- 修正中斷的 DSC 概觀連結 (#10702)
- 更新 Support_Question.md，以連結至 Stack Overflow 作為另一個社群資源 (#10638) (感謝 @mklement0！)
- 將處理器架構新增至散發要求範本 (#10661)
- 將新的 PowerShell MoL 書籍新增至了解 PowerShell 文件中 (#10602)
- 針對 v 6.1.6 和 v6.2.3 版本更新 README.md 和中繼資料 (#10523)
- 修正 README.md 中的打字錯誤 (#10465) (感謝 @vedhasp！)
- 將 PSKoans 模組的參考新增至學習資源文件中 (#10369) (感謝 @vexx32！)
- 針對 7.0.0-preview.3 更新 README.md 和 metadata.json (#10393)
