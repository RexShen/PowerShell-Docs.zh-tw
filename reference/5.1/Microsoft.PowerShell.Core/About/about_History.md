---
description: 描述如何在命令歷程記錄中取得和執行命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: 64a8fac4f25ac60be58aca8549748b9e4dde6c3b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208015"
---
# <a name="about-history"></a>關於歷程記錄

## <a name="short-description"></a>簡短描述
描述如何在命令歷程記錄中取得和執行命令。

## <a name="long-description"></a>完整描述

當您在命令提示字元中輸入命令時，PowerShell 會將命令儲存在命令歷程記錄中。 您可以使用歷程記錄中的命令作為工作的記錄。 而且，您可以從命令歷程記錄中重新叫用和執行命令。

PowerShell 有兩種不同的歷程記錄提供者：內建的歷程記錄，以及由 **PSReadLine** 模組管理的歷程記錄。 歷程記錄是分開管理的，但這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。

## <a name="using-the-psreadline-history"></a>使用 PSReadLine 歷程記錄

PSReadLine 歷程記錄會追蹤所有 PowerShell 會話中使用的命令。
歷程記錄會寫入每個主機的中央檔案。 該記錄檔可供所有會話使用，並包含過去所有的歷程記錄。 當會話結束時，不會刪除歷程記錄。 此外，該歷程記錄無法由 Cmdlet 管理 `*-History` 。 如需詳細資訊，請參閱 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)。

## <a name="using-the-built-in-session-history"></a>使用內建的會話歷程記錄

內建記錄只會追蹤目前會話中使用的命令。 歷程記錄無法供其他會話使用，且會在會話結束時刪除。

### <a name="history-cmdlets"></a>歷程記錄 Cmdlet

PowerShell 有一組 Cmdlet，可管理命令歷程記錄。

| Cmdlet           | Alias  | Description                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | 取得命令歷程記錄。                  |
| `Invoke-History` | `r`    | 在命令歷程記錄中執行命令。     |
| `Add-History`    |        | 將命令加入至命令歷程記錄。     |
| `Clear-History`  | `clhy` | 從命令歷程記錄中刪除命令。 |

### <a name="keyboard-shortcuts-for-managing-history"></a>管理歷程記錄的鍵盤快速鍵

在 PowerShell 主控台中，您可以使用下列快速鍵來管理命令歷程記錄。

- <kbd>UpArrow</kbd> -顯示上一個命令。
- <kbd>Download-downarrow-circled</kbd> -顯示下一個命令。
- <kbd>F7</kbd> -顯示命令歷程記錄。
- <kbd>ESC</kbd> -隱藏曆程記錄。
- <kbd>F8</kbd> -尋找命令。 輸入一或多個字元，然後按 <kbd>F8</kbd>。 再按一次 <kbd>F8</kbd> 下一個實例。
- <kbd>F9</kbd> -依歷程記錄識別碼尋找命令。 輸入歷程記錄識別碼，然後按 <kbd>F9</kbd>。 按 <kbd>F7</kbd> 以尋找識別碼。
- <kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> -搜尋的歷程記錄 `*<string>*` ，並傳回最新的相符項。 如果您重複按下 <kbd>tab</kbd> 鍵，它會迴圈顯示歷程記錄中相符的專案。

> [!NOTE]
> 這些按鍵系結是由主控台主機應用程式所執行。 其他應用程式（例如 Visual Studio Code 或 Windows 終端機）可以有不同的索引鍵系結。 PSReadLine 模組可以覆寫系結。 PSReadLine 會在您啟動 PowerShell 會話時自動載入。
> 載入 PSReadLine 後， <kbd>F7</kbd> 和 <kbd>F9</kbd> 不會系結至任何函數。 PSReadLine 不會提供對等的功能。 如需詳細資訊，請參閱 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)。

### <a name="maximumhistorycount"></a>MaximumHistoryCount

`$MaximumHistoryCount`喜好設定變數會決定 PowerShell 在命令歷程記錄中儲存的命令數目上限。 預設值為
4096.

例如，下列命令會減少 `$MaximumHistoryCount` 到100命令：

```powershell
$MaximumHistoryCount = 100
```

若要套用此設定，請重新開機 PowerShell。

若要為您所有的 PowerShell 會話儲存新的變數值，請將指派語句新增至 PowerShell 設定檔。 如需設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

如需喜好設定變數的詳細資訊 `$MaximumHistoryCount` ，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。

### <a name="order-of-commands-in-the-history"></a>記錄中的命令順序

當命令執行完成時，不會將命令新增至歷程記錄，而不是在輸入命令時。 如果命令需要一些時間才能完成，或命令以嵌套提示執行，命令在歷程記錄中可能看起來不是順序。 只有當您離開提示層級時，才會完成以嵌套提示字元執行的命令。

## <a name="see-also"></a>另請參閱

- [about_Line_Editing](about_Line_Editing.md)
- [about_Preference_Variables](about_Preference_Variables.md)
- [about_Profiles](about_Profiles.md)
- [about_Variables](about_Variables.md)
- [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)
