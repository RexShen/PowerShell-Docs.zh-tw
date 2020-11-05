---
ms.date: 06/12/2017
title: WMF 5.1 的主控台改善
description: WMF 5.1 針對 Windows PowerShell 5.1 的主控台體驗新增了新功能。
ms.openlocfilehash: 9a86a2ed4787554e7255bedf1c2ae6e798fefa45
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660754"
---
# <a name="console-improvements-in-wmf-51"></a>WMF 5.1 的主控台改善

## <a name="powershell-console-improvements"></a>PowerShell 主控台改善

WMF 5.1 的 powershell.exe 已進行下列變更，以改善主控台體驗︰

### <a name="vt100-support"></a>VT100 支援

Windows 10 新增了對 [VT100 逸出序列](/windows/console/console-virtual-terminal-sequences)的支援。
PowerShell 在計算表格寬度時，會忽略某些 VT100 格式逸出序列。

PowerShell 也新增了可用於將程式碼格式化的新 API，以判斷是否支援 VT100。 例如：

```powershell
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

以下是可用來反白 [ 相符項目的完整](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7)範例`Select-String`。 將範例儲存在名為 `MatchInfo.format.ps1xml` 的檔案中，然後在您的設定檔或其他位置執行 `Update-FormatData -Prepend MatchInfo.format.ps1xml` 以便加以使用。

請注意，從 Windows 10 年度更新版開始才支援 VT100 逸出序列。
舊版系統不支援它們。

### <a name="vi-mode-support-in-psreadline"></a>PSReadline 的 Vi 模式支援

[PSReadline](https://github.com/PowerShell/PSReadLine) 加入了對 vi 模式的支援。 若要使用 vi 模式，請執行 `Set-PSReadlineOption -EditMode Vi`。

### <a name="redirected-stdin-with-interactive-input"></a>以互動輸入重新導向的 stdin

在舊版中，重新導向 stdin 且要以互動方式輸入命令時，需要使用 `powershell -File -` 啟動 PowerShell。

有了 WMF 5.1，即不再需要此難以探索的選項。 您不需使用任何選項就能啟動 PowerShell。

請注意，PSReadline 不支援重新導向的 stdin，而具有重新導向之 stdin 的內建命令列編輯體驗極受限制，例如，方向鍵無法運作。 新版的 PSReadline 應該會解決這個問題。
