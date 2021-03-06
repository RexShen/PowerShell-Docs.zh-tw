---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: 什麼是 PowerShell？
description: 本文介紹 PowerShell 指令碼環境及其功能。
ms.openlocfilehash: 91fc580af9a3adf43a24c40b4aaf3f1843882705
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500771"
---
# <a name="what-is-powershell"></a>什麼是 PowerShell？

PowerShell 是跨平台的工作自動化及設定管理架構，由命令列殼層與指令碼語言組成。 不同於大部分的殼層可接受及傳回文字，PowerShell 以 .NET Common Language Runtime (CLR) 為建置基礎，並接受及傳回 .NET 物件。 這種從根本上的變更，打造了全新的自動化工具與方法。

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a>輸出是以物件為基礎的

不同於傳統的命令列介面，PowerShell Cmdlet 是設計來處理物件。
物件是結構化的資訊，而不僅僅是出現在畫面上的字元字串。 命令輸出一律會攜帶您在需要時可以使用的額外資訊。

如果您過去曾使用文字處理工具來處理資料，將會發現它們的行為與在 PowerShell 中使用時不同。 在大部分情況下，您不需要使用文字處理工具來擷取特定資訊。 您可以使用標準的 PowerShell 物件語法，直接存取部分資料。

## <a name="the-command-family-is-extensible"></a>命令系列可進行擴充

`cmd.exe` 之類的介面無法讓您直接擴充內建的命令集。 您可以建立外部命令列工具在 `cmd.exe` 中執行。 但這些外部工具不會提供任何服務，例如說明整合。 `cmd.exe` 自己不會知道這些外部工具是有效的命令。

PowerShell 中的命令稱為 _Cmdlet_ 。 您可以個別使用每個 Cmdlet，但合併使用來執行複雜的工作時，更見其功效。 如同許多殼層，PowerShell 可讓您存取電腦上的檔案系統。 PowerShell「提供者」可讓您像存取檔案系統般容易地存取其他資料存放區 (如登錄及憑證存放區)。

您可以使用經過編譯的程式碼或指令碼，建立自己的 Cmdlet 與函式模組。 模組可將 Cmdlet 與提供者新增到殼層。 PowerShell 也支援類似於 UNIX 殼層指令碼及 `cmd.exe` 批次檔案的指令碼。

## <a name="support-for-command-aliases"></a>支援命令別名

PowerShell 支援別名，以使用替代名稱來參考命令。 別名讓具有其他殼層使用體驗的使用者能夠使用他們已經知道的常見命令名稱，在 PowerShell 中執行類似作業。

別名會將新名稱與另一個命令產生關聯。 例如，PowerShell 具有會清除輸出視窗的內部函式 `Clear-Host`。 您可以在命令提示字元中輸入 `cls` 或 `clear` 別名。 PowerShell 會解譯這些別名並執行 `Clear-Host` 函式。

此功能可協助使用者學習 PowerShell。 首先，大部分的 `cmd.exe` 與 Unix 使用者都具備一大套完整的命令，而且使用者也都知道其名稱。 PowerShell 對應項可能不會產生相同的結果。 不過，結果非常接近，足以讓使用者在不知道 PowerShell 命令名稱的情況下執行動作。 在學習新的命令殼層時，「肌肉記憶」是另一大挫折來源。 若您已使用 `cmd.exe` 多年，可能會反身鍵入 `cls` 命令來清除畫面。 如果沒有 `Clear-Host` 的別名，您就會收到錯誤訊息，而且不知道該怎麼清除輸出。

## <a name="powershell-handles-console-input-and-display"></a>PowerShell 會處理主控台輸入和顯示

當您輸入命令時，PowerShell 一律會直接處理命令列輸入。 PowerShell 也會將您在畫面上看到的輸出格式化。 此差異十分重要，因為它可以減少每個 Cmdlet 所需的工作。 它會確保您一律可以使用與任何 Cmdlet 相同的方式來執行動作。 Cmdlet 開發人員不需要撰寫程式碼來剖析命令列引數，或將輸出格式化。

傳統命令列工具有其專屬方法來要求和顯示說明。 有一些命令列工具會使用 `/?` 觸發說明顯示，另有一些則會使用 `-?`、`/H`，甚至是 `//`。 有一部分會在 GUI 視窗中顯示說明，而不是在主控台顯示中。 如果您使用錯誤的參數，工具可能會忽略您輸入的內容，並開始自動執行工作。
因為 PowerShell 會自動剖析及處理命令列，所以 `-?` 參數一律表示「顯示此命令的說明」。

> [!NOTE]
> 如果您在 PowerShell 中執行圖形應用程式，即會開啟應用程式的視窗。
> 只有在處理您提供的命令列輸入或傳回給主控台視窗的應用程式輸出時，PowerShell 才會介入。 它不會影響應用程式的內部運作方式。

## <a name="powershell-has-a-pipeline"></a>PowerShell 具有管線

管線可說是用於命令列介面中最重要的概念。 若運用得當，管線將能減少使用複雜命令，讓您能夠更清楚地觀察工作的流程。 管線中的每個命令都會將其輸出逐項傳遞給下一個命令。 命令不需要每次處理一個以上的項目。 結果就是減少使用資源，而且立即得到輸出。

用於管線的標記法類似於其他殼層中所使用的標記法。 乍看之下，PowerShell 中的管線差異可能並不明顯。 雖然您會在畫面上看到文字，但 PowerShell 會在命令之間使用管線來傳送物件 (而非文字)。

例如，如果您使用 `Out-Host` Cmdlet 強制逐頁顯示另一個命令的輸出，則輸出看起來就像畫面上所顯示的一般文字 (分成數頁)：

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

分頁還會降低 CPU 使用率，因為處理控制權會在其已準備好要顯示的完成頁面時移轉給 `Out-Host` Cmdlet。 管線中在它前面的 Cmdlet 會暫停執行，直到輸出的下一個分頁可供使用為止。

### <a name="objects-in-the-pipeline"></a>管線中的物件

當您在 PowerShell 中執行 Cmdlet 時，您會看到文字輸出，這是因為在主控台視窗中必須將物件呈現為文字。 文字輸出可能不會顯示要輸出之物件的所有屬性。

例如，請考慮 `Get-Location` Cmdlet。 文字輸出是資訊的摘要，並不是由 `Get-Location` 所傳回之物件的完整呈現。 輸出中的標題是由處理序新增的，它會將資料格式化以便在畫面上顯示。

```powershell
Get-Location
```

```Output
Path
----
C:\
```

使用管線將輸出傳送給 `Get-Member` Cmdlet 時，會顯示 `Get-Location` 所傳回之物件的相關資訊。

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` 會傳回 **PathInfo** 物件，其中包含目前的路徑與其他資訊。

## <a name="built-in-help-system"></a>內建說明系統

一如 Unix `man` 頁面，PowerShell 包含詳細的說明文章，解釋了 PowerShell 概念與命令語法。 您可以在命令提示字元中使用 [Get-Help][] Cmdlet 來顯示這些文章，或在線上的 PowerShell 文件中，檢視這些文章的最新更新版本。

## <a name="next-steps"></a>後續步驟

若要深入了解 PowerShell，請參閱此網站的＜ **了解 PowerShell** ＞一節。

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
