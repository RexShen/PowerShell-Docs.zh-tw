---
title: "WMF 5.1 (Preview) 的 Bug 修正"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 90d57af0c8b90e709769525455ae39557b9c7176

---

# WMF 5.1 (Preview) 的 Bug 修正#

## Bug 修正 ##

WMF 5.1 已修正下列重大 Bug︰

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

這項變更也會處理 [Connect 上的問題 1752224](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

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



<!--HONumber=Jul16_HO3-->


