---
title: "WMF 5.1 (預覽) 的新案例和功能"
ms.date: 2016-07-06
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: dcccf6880873c3f5c1b58fb1a8c546901b173879
ms.openlocfilehash: 9341b7fc3feea20cc2434065c3e512d1a8dd2b54

---

# WMF 5.1 (預覽) 的新案例和功能 #

> 注意：本資訊尚屬初始版本，後續有可能變更。

## PowerShell 版本 ##
從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。

- **Desktop Edition︰**建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行之 PowerShell 版本的指令碼和模組相容。
- **Core Edition︰**建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行之 PowerShell 版本的指令碼和模組相容。

**深入了解使用 PowerShell 版本**
- [判斷執行的 PowerShell 版本]()
- [宣告特定 PowerShell 版本的模組相容性]()
- [依據 CompatiblePSEditions 篩選 Get-Module 結果]()
- [只有在相容的 PowerShell 版本上執行才會執行指令碼]()

## 模組分析快取 ##
從 WMF 5.1 開始，PowerShell 可以控制快取模組資料所用的檔案，例如匯出的命令。

此快取預設儲存在 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案中。
快取一般在啟動同時搜尋命令時讀取，並在模組匯入一段時間後寫入背景執行緒。

若要變更快取的預設位置，請先設定環境變數 PSModuleAnalysisCachePath 再啟動 PowerShell。 此環境變數的變更只會影響子處理程序。
該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。
若要停用檔案快取，請將此值設定於無效的位置，例如︰

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

這會將路徑設定到無效的裝置。 如果 PowerShell 無法寫入該路徑，就不會傳回任何錯誤，但您可以透過追蹤查看錯誤報告︰

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

寫出快取時，PowerShell 會檢查確認模組已不存在，避免不必要的大型快取。
有時候不需要這些檢查，在此情況下，您可以透過設定下列項目關閉這些檢查：

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此環境變數設定會立即在目前的程序中生效。

##指定模組版本

在 WMF 5.1 中，`using module` 與 PowerShell 中其他模組相關的語法結構表現一致。 以往，您無法指定特定的模組版本；如果有多個版本存在，這會導致錯誤。


在 WMF 5.1 中：

* 您可以使用 `ModuleSpecification` [雜湊表](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx)。 此雜湊表與 `Get-Module -FullyQualifiedName` 有相同的格式。

**範例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* 如果模組有多個版本，PowerShell 會使用與 `Import-Module` **相同的解析邏輯**，不傳回錯誤，和 `Import-Module` 及 `Import-DscResource` 的行為一樣。

## PowerShell 主控台改善

WMF 5.1 的 Powershell.exe 已進行下列變更，以改善主控台體驗︰

###VT100 支援

Windows 10 新增了對 [VT100 逸出序列](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx)的支援。
PowerShell 在計算表格寬度時，會忽略某些 VT100 格式逸出序列。

PowerShell 也新增了可用於將程式碼格式化的新 API，以判斷是否支援 VT100。 例如：

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
以下是可用來反白 Select-String 相符項目的完整[範例](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7)。
將範例儲存在名為 `MatchInfo.format.ps1xml` 的檔案中，然後在您的設定檔或其他位置執行 `Update-FormatData -Prepend MatchInfo.format.ps1xml` 以便加以使用。

請注意，從 Windows 10 年度更新版開始才支援 VT100 逸出序列，舊版系統不支援。   

### PSReadline 的 Vi 模式支援

[PSReadline](https://github.com/lzybkr/PSReadLine) 加入了對 vi 模式的支援。 若要使用 vi 模式，請執行 `Set-PSReadline -EditMode vi`。

### 以互動輸入重新導向的 stdin 

在舊版中，重新導向 stdin 且要以互動方式輸入命令時，需要使用 `powershell -File -` 啟動 PowerShell。

有了 WMF 5.1，即不再需要這個難以探索的選項，您可以不用任何選項啟動 PowerShell，例如 `powershell`。

請注意，PSReadline 目前不支援重新導向的 stdin，而附重新導向的 stdin 的內建命令列編輯經驗極受限制，例如方向鍵無法運作。  新版的 PSReadline 應該會解決這個問題。   

##PowerShell 引擎改善

WMF 5.1 已實作核心 PowerShell 引擎的下列改善︰


## 效能 ##

某些重要區域的效能已改善︰

- 啟動
- 管線到 ForEach-Object 和 Where-Object 等 Cmdlet 大約快了 50% 

一些改善範例 (結果隨硬體而有不同)： 

| 案例 | 5.0 的時間 (毫秒) | 5.1 的時間 (毫秒) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| PowerShell 首次執行︰ `powershell -command "Unknown-Command"` | 30000 | 13000 |
| 命令分析快取組建︰ `powershell -command "Unknown-Command"` | 7000 | 520 |
| `1..1000000 | % { }` | 1400 | 750 |
  
> [!NOTE]  
> 與啟動相關的一項變更，可能影響到某些不受支援的案例。 PowerShell 不再讀取 `$pshome\*.ps1xml` 檔案，這些檔案已轉換成 C#，以避免處理 XML 檔案的一些檔案和 CPU 負荷。 這些檔案對 V2 的支援仍然不變，因此，若變更檔案內容，對 V5 沒有任何效果，只對 V2 有效果。 請注意，變更這些檔案內容向來是不受支援的案例。

另一個明顯的變更，是 PowerShell 如何快取匯出的命令和安裝在系統上的模組其他資訊。 以往，此快取儲存於 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 目錄。 在 WMF 5.1，快取是單一的 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案。
如需詳細資訊，請參閱 [analysis_cache.md]()。



## Bug 修正 ##

已修正下列重大 Bug︰

### 完全接受模組自動探索 `$env:PSModulePath` ###

WMF 3 中引進了模組自動探索 (呼叫命令時自動載入模組，不需要明確的 Import-Module)。 當初引入後，PowerShell 會先檢查 `$PSHome\Modules` 中有沒有命令，再使用 `$env:PSModulePath`。

WMF 5.1 將此行為變更為完全接受 `$env:PSModulePath`。 這讓使用者撰寫之定義 PowerShell 所提供命令的模組 (例如 `Get-ChildItem`) 自動載入並正確覆寫內建的命令。

### 檔案重新導向不再需要硬式編碼 `-Encoding Unicode` ###

所有舊版的 PowerShell 都不可能控制檔案重新導向運算子所使用的檔案編碼，例如 `get-childitem > out.txt`，因為 PowerShell 新增了 `-Encoding Unicode`。

但從 WMF 5.1 開始，您可以設定 `$PSDefaultParameterValues` 來變更重新導向的檔案編碼方式，例如︰

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### 修正存取下列項目成員時的迴歸問題： `System.Reflection.TypeInfo` ###

WMF 5.0 引入的迴歸會中斷存取 `System.Reflection.RuntimeType` 成員的程序，例如 `[int].ImplementedInterfaces`。
WMF5.1 已修正這個 Bug。


### 修正 COM 物件的一些問題 ###

WMF 5.0 引入新的 COM 繫結器，可對 COM 物件叫用方法以及存取 COM 物件的屬性。
此新的繫結器大幅改善了效能，卻也造成了一些 Bug，WMF5.1 已加以修正。

#### 不一定會正確執行引數轉換 ####

在下例中︰

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

SendKeys 方法預期的是字串，但 PowerShell 並未將字元轉換成字串，將轉換延後至 IDispatch::Invoke，使用 VariantChangeType 進行轉換，以致本例傳送了 '1'、'7' 和 '3' 機碼，而不是預期的 Volume.Mute 機碼。

#### 不一定會正確處理可列舉的 COM 物件 ####

PowerShell 通常會列舉大部分可列舉的物件，但 WMF 5.0 引入的迴歸卻阻擋了列舉實作 IEnumerable 的 COM 物件。  例如：

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

上例中，WMF 5.0 在管線中錯誤寫入 Scripting.Dictionary，卻未列舉機碼值組。


### `[ordered]` 在類別中不允許 ###

WMF5 引入了類別，其具有類別所用的類型常值驗證。  `[ordered]` 看起來像類型常值，卻不是真正的 .Net 類型。  WMF5 誤報類別內發生 `[ordered]` 錯誤︰

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### 多版本的說明主題無法運作 ###

在 WMF 5.1 以前，如果安裝了多個版本的模組，而它們都共用一個說明主題，例如，about_PSReadline，則 `help about_PSReadline` 會傳回多個主題，但沒有明確的方法可以檢視實際的說明。

WMF 5.1 藉由傳回最新版本的說明主題，以修正此問題。

Get-Help 不提供指定所需說明版本的方法。 若要解決這個問題，請瀏覽到模組目錄，直接使用您偏好的編輯器等工具檢視說明。 

## OneGet 改善
WMF 5.1 包含數個修正和改善，以解決 WMF 5.0 版本中的某些使用者體驗落差。 

###已移除版本別名

**案例**︰如果您已在系統上安裝了 1.0 及 2.0 版的封裝 P1，而您想要將 1.0 版解除安裝，您可以執行 "uninstall-package -name P1 -version 1.0"，預期執行 Cmdlet 之後就會將 1.0 版解除安裝。 不過，結果卻是將 2.0 版解除安裝。 
    
這是因為 "-version" 參數是 "-minimumversion" 參數的別名。 當 OneGet 在尋找至少 1.0 版的完整封裝時，會傳回最新的版本。 正常情況下會發生此行為，因為尋找最新版本通常是我們想要的結果。 只不過，不應該套用到將封裝解除安裝的情況上。
    
**解決方案**︰WMF 5.1 完全移除 OneGet 和 PowerShellGet 中的 -version 別名。 

###多次提示啟動載入 NuGet 提供者

**案例**：當您第一次在電腦上執行 Find-Module 或 Install-module 或其他 OneGet Cmdlet 時，OneGet 嘗試啟動載入 NuGet 提供者。 它之所以如此做，是因為 PowerShellGet 提供者也使用 NuGet 提供者下載 PowerShell 模組。 接著，OneGet 會提示使用者提供安裝 NuGet 提供者的權限。 在使用者選取 [是] 啟動載入之後，就會安裝最新版的 NuGet 提供者。 
    
不過在某些情況下，當電腦上安裝了較舊版本的 NuGet 提供者時，有時 PowerShell 工作階段會先載入舊版的 NuGet (亦即 OneGet 中的競爭條件)。 不過，PowerShellGet 需要較新版本的 NuGet 提供者工作，因此 PowerShellGet 會要求 OneGet 再次啟動載入 NuGet 提供者。 以致多次提示啟動載入 NuGet 提供者。

**解決方案**︰在 WMF 5.1 中，OneGet 會載入最新版的 NuGet 提供者，避免多次提示啟動載入 NuGet 提供者。

如果 $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies 有舊版的 NuGet 提供者，您也可以手動刪除舊版 (NuGet Anycpu.exe) 解決這個問題。


###只有內部網路存取權電腦的 OneGet 支援

**案例**︰以前在 WMF 5.0 中，OneGet 不支援只能存取內部網路 (不能存取網際網路) 的電腦。

**解決方案**︰在 WMF 5.1，您可以依照這些步驟允許內部網路電腦使用 OneGet：

1. 使用 Install-PackageProvider NuGet，用具有網際網路連線的其他電腦下載 NuGet 提供者。

2. 在 $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget 或 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget 下尋找 NuGet 提供者。 

3. 將二進位檔複製到內部網路電腦可以存取的資料夾或網路共用位置，然後以 "Install-PackageProvider NuGet -Source <Path to folder>" 安裝 NuGet 提供者。


###事件記錄的改善

安裝封裝即是變更電腦的狀態。 在 WMF 5.1 中，OneGet 會將安裝、解除安裝和儲存封裝活動等事件記錄在 Windows 事件記錄檔。 事件通道和 PowerShell 的一樣，亦即 Microsoft-Windows-PowerShell、Operational。

###支援基本驗證

在 WMF 5.1 中，OneGet 支援從需要基本驗證的儲存機制尋找和安裝封裝。 您可以向 Find-Package 和 Install-Package Cmdlet 提供您的認證。 例如：

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
###支援在 Proxy 後方使用 OneGet

在 WMF 5.1 中，OneGet 現在採用新的 Proxy 參數：-ProxyCredential 和 -Proxy。 您可以使用這些參數，在 OneGet Cmdlet 指定 Proxy URL 和認證。 預設使用系統 Proxy 設定。 例如：

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO1-->


