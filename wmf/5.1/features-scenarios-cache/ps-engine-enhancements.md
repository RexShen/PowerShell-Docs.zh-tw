---
title: "PowerShell 引擎增強功能"
author: jasonsh
translationtype: Human Translation
ms.sourcegitcommit: 6813902aec214aee9ede27ff79dd291364e9f443
ms.openlocfilehash: f864850128f118704d7545b09110835ab1d51b8e

---

# PowerShell 引擎增強功能 #

PowerShell 5.1 已實作核心 PowerShell 引擎的下列改善︰


## 效能 ##

某些重要區域的效能已改善︰

1. 啟動
2. 管線到 ForEach-Object 和 Where-Object 等 Cmdlet 大約快了 50% 

一些改善範例 (結果隨硬體而有不同)： 

| 案例 | 5.0 的時間 (毫秒) | 5.1 的時間 (毫秒) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| PowerShell 首次執行︰ `powershell -command "Unknown-Command"` | 30000 | 13000 |
| 命令分析快取組建︰ `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
與啟動相關的一項變更，可能影響到某些 (不受支援) 的案例。 PowerShell 不再讀取 `$pshome\*.ps1xml` 檔案，這些檔案已轉換成 C#，以避免處理 XML 檔案的一些檔案和 CPU 負荷。 這些檔案對 V2 的支援仍然不變，因此，若變更檔案內容，對 V5 沒有任何效果，只對 V2 有效果。 請注意，變更這些檔案內容向來是不受支援的案例。

另一個明顯的變更，是 PowerShell 如何快取匯出的命令和安裝在系統上的模組其他資訊。 以往，此快取儲存於 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 目錄。 在 WMF 5.1，快取是單一的 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案。
如需詳細資訊，請參閱 [analysis_cache.md]()。

從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。



## Bug 修正 ##

已修正下列重大 Bug︰

### 完全接受模組自動探索 `$env:PSModulePath` ###

WMF3 中引進了模組自動探索 (呼叫命令時自動載入模組，不需要明確的 Import-Module)。 當初引入後，PowerShell 會先檢查 `$PSHome\Modules` 中有沒有命令，再使用 `$env:PSModulePath`。

WMF 5.1 將此行為變更為完全接受 `$env:PSModulePath`。 這讓使用者撰寫之定義 PowerShell 所提供命令的模組 (例如 `Get-ChildItem`) 自動載入並正確覆寫內建的命令。

### 檔案重新導向不再需要硬式編碼 `-Encoding Unicode` ###

所有舊版的 PowerShell 都不可能控制檔案重新導向運算子所使用的檔案編碼，例如 `get-childitem > out.txt`，因為 PowerShell 新增了 `-Encoding Unicode`。

但從 WMF 5.1 開始，您可以設定 `$PSDefaultParameterValues` 來變更重新導向的檔案編碼方式，例如︰

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### 修正存取下列項目成員時的迴歸問題： `System.Reflection.TypeInfo` ###

WMF5 引入的迴歸會中斷存取 `System.Reflection.RuntimeType` 成員的程序，例如 `[int].ImplementedInterfaces`。
WMF5.1 已修正這個 Bug。


### 修正 COM 物件的一些問題 ###

WMF5 引入新的 COM 繫結器，可對 COM 物件叫用方法以及存取 COM 物件的屬性。
此新的繫結器大幅改善了效能，卻也造成了一些 Bug，WMF5.1 已加以修正。

#### 不一定會正確執行引數轉換 ####

在下例中︰

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

SendKeys 方法預期的是字串，但 PowerShell 並未將字元轉換成字串，將轉換延後至 IDispatch::Invoke，使用 VariantChangeType 進行轉換，以致本例傳送了 '1'、'7' 和 '3' 機碼，而不是預期的 Volume.Mute 機碼。

#### 不一定會正確處理可列舉的 COM 物件 ####

PowerShell 通常會列舉大部分可列舉的物件，但 WMF5 引入的迴歸卻阻擋了列舉實作 IEnumerable 的 COM 物件。  例如：

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

上例中，WMF5 在管線中錯誤寫入 Scripting.Dictionary，卻未列舉機碼值組。


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

WMF 5.1 藉由傳回最新版本的說明主題，修正此問題。

Get-Help 不提供指定所需說明版本的方法，因應措施是瀏覽到模組目錄，直接使用您偏好的編輯器等工具檢視說明。 



<!--HONumber=Jul16_HO2-->


