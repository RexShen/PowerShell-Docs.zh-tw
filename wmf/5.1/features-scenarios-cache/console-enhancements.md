---
title: "主控台體驗的增強功能"
author: jasonsh
translationtype: Human Translation
ms.sourcegitcommit: 9ce218a2807dd7b1c69f81efdbd6132321e6a815
ms.openlocfilehash: e6653a02421e3aec3910a70c64f7cf7cecd696ab

---

>注意︰請提供建議的描述性標題和簡短描述

## PowerShell 主控台的增強功能

powershell.exe 已進行下列變更，以改善主控台體驗︰

1. VT100 支援

Windows 10 新增了對 [VT100 逸出序列](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx)的支援。
PowerShell 在計算表格寬度時，會忽略某些 VT100 格式逸出序列。

PowerShell 也新增了可用於將程式碼格式化的新 API，以判斷是否支援 VT100。  例如：

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
將範例儲存在 `MatchInfo.format.ps1xml` 檔案中，然後用在您的設定檔或其他位置，執行 `Update-FormatData -Prepend MatchInfo.format.ps1xml`。

請注意，從 Windows 10 年度更新版開始才支援 VT100 逸出序列，舊版系統不支援。   

2. PSReadline 的 Vi 模式支援

[PSReadline](https://github.com/lzybkr/PSReadLine) 加入了對 vi 模式的支援。 若要使用 vi 模式，請執行 `Set-PSReadline -EditMode vi`。

3. 以互動輸入重新導向的 stdin 

在舊版中，重新導向 stdin 且要以互動方式輸入命令時，需要使用 `powershell -File -` 啟動 PowerShell。

有了 WMF 5.1，即不再需要這個難以探索的選項，您可以不用任何選項啟動 PowerShell，例如 `powershell`。

請注意，PSReadline 目前不支援重新導向的 stdin，而附重新導向的 stdin 的內建命令列編輯經驗極受限制，例如方向鍵無法運作。  新版的 PSReadline 應該會解決這個問題。   


<!--HONumber=Jul16_HO1-->


