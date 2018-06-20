---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: WMF 5.1 的 Bug 修正
ms.openlocfilehash: 1e46d6d0419b3497450e6eaddbaa47456b004691
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222185"
---
# <a name="bug-fixes-in-wmf-51"></a>WMF 5.1 的 Bug 修正#

## <a name="bug-fixes"></a>Bug 修正 ##

WMF 5.1 已修正下列重大 Bug︰

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>完全接受模組自動探索 `$env:PSModulePath` ###

WMF 3 中引進了模組自動探索 (呼叫命令時自動載入模組，不需要明確的 Import-Module)。
當初引入後，PowerShell 會先檢查 `$PSHome\Modules` 中有沒有命令，再使用 `$env:PSModulePath`。

WMF 5.1 將此行為變更為完全接受 `$env:PSModulePath`。
這讓使用者撰寫之定義 PowerShell 所提供命令的模組 (例如 `Get-ChildItem`) 自動載入並正確覆寫內建的命令。

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>檔案重新導向不再需要硬式編碼 `-Encoding Unicode` ###

所有舊版的 PowerShell 都不可能控制檔案重新導向運算子所使用的檔案編碼，例如 `Get-ChildItem > out.txt`，因為 PowerShell 新增了 `-Encoding Unicode`。

但從 WMF 5.1 開始，您可以設定 `$PSDefaultParameterValues` 來變更重新導向的檔案編碼方式︰

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>修正存取 `System.Reflection.TypeInfo` 成員時的迴歸問題 ###

WMF 5.0 引入的迴歸會中斷存取 `System.Reflection.RuntimeType` 成員的程序，例如 `[int].ImplementedInterfaces`。
WMF 5.1 已修正這個 Bug。


### <a name="fixed-some-issues-with-com-objects"></a>修正 COM 物件的一些問題 ###

WMF 5.0 引入新的 COM 繫結器，可對 COM 物件叫用方法以及存取 COM 物件的屬性。
此新的繫結器大幅改善了效能，卻也造成了一些 Bug，WMF5.1 已加以修正。

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>不一定會正確執行引數轉換 ####

在下例中︰

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

SendKeys 方法預期的是字串，但 PowerShell 並未將字元轉換成字串，將轉換延後至 IDispatch::Invoke，使用 VariantChangeType 進行轉換，以致本例傳送了 '1'、'7' 和 '3' 機碼，而不是預期的 Volume.Mute 機碼。

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>不一定會正確處理可列舉的 COM 物件 ####

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

### <a name="ordered-was-not-allowed-inside-classes"></a>在類別中不允許 `[ordered]` ###

WMF 5.0 引入了類別，其具有類別所用的類型常值驗證。
`[ordered]` 看起來像類型常值，卻不是真正的 .NET 類型。
WMF 5.0 誤報類別內發生 `[ordered]` 錯誤︰

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>多版本的說明主題無法運作 ###

在 WMF 5.1 以前，如果安裝了多個版本的模組，而它們都共用一個說明主題，例如，about_PSReadline，則 `help about_PSReadline` 會傳回多個主題，但沒有明確的方法可以檢視實際的說明。

WMF 5.1 藉由傳回最新版本的說明主題，以修正此問題。

`Get-Help` 不提供指定所需說明版本的方法。
若要解決這個問題，請瀏覽到模組目錄，直接使用您偏好的編輯器等工具檢視說明。

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>從 STDIN 讀取的 powershell.exe 停止運作

客戶會使用原生應用程式的 `powershell -command -` 來執行透過 STDIN 在指令碼中傳遞的 PowerShell，不過，這已因為主控台主機的其他變更而無法運作。

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>powershell.exe 在啟動時會造成 CPU 使用量突然增加

PowerShell 會使用 WMI 查詢來檢查它是否透過「群組原則」啟動，以避免造成登入時的延遲。
WMI 查詢最後會將 tzres.mui.dll 插入系統上的每一個處理序，因為 WMI Win32_Process 類別會嘗試擷取本地時區資訊。
這會導致 wmiprvse (WMI 提供者主機) 出現大量的 CPU 使用量。
修正方法是以 Win32 API 呼叫取代 WMI 來取得相同的資訊。
