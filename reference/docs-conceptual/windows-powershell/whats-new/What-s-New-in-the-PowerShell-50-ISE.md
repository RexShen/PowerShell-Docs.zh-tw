---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: PowerShell 5.0 ISE 的新功能
description: 此文章說明已在 Windows PowerShell 整合式指令碼環境 (ISE) 5.0 版中推出的新功能與更新功能。
ms.openlocfilehash: 75d37d0dafe381c84898ac48343336cd525d2dd1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660820"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Windows PowerShell 5.0 ISE 的新功能

此文章說明已在 Windows PowerShell 整合式指令碼環境 (ISE) 5.0 版中推出的新功能與更新功能。

> [!NOTE]
> 我們將不再為 PowerShell ISE 開發新功能。 因為此功能屬於 Windows 的出貨元件，所以官方仍會繼續支援其安全性與高優先順序的服務修正。
> 目前尚無任何計劃要將 ISE 從 Windows 移除。
>
> PowerShell v6 及更新版本不支援 ISE。 使用者如有需要 ISE 的替代解決方案，可使用 [Visual Studio Code](https://code.visualstudio.com/) 搭配 [PowerShell 延伸模組](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)。

## <a name="feature-description"></a>功能說明

Windows PowerShell ISE 是一個主應用程式，可以讓您在圖形化與直覺式的環境中撰寫、執行及測試指令碼和模組。 語法標色、TAB 鍵自動完成、視覺化偵錯、Unicode 相容性、即時線上說明等主要功能，提供豐富的指令碼撰寫體驗。

如需詳細資訊，請參閱 [Windows PowerShell ISE 簡介](../ise/Introducing-the-Windows-PowerShell-ISE.md)。

下表列出 Windows PowerShell 中這版 Windows PowerShell ISE 的新功能和變更功能。

## <a name="intellisense"></a>IntelliSense

> ISE 3.0 的新功能

IntelliSense 是屬於 Windows PowerShell ISE 的自動完成協助功能。
在您輸入文字時，IntelliSense 會顯示與輸入文字可能相符的 Cmdlet、參數、參數值、檔案或資料夾的可點選功能表。

**這個變更增加了什麼價值？**

透過 IntelliSense，您可以在使用 Windows PowerShell ISE 建立指令碼時更輕鬆地探索 Cmdlet 和語法。 您也可以在建立新指令碼時透過 Windows PowerShell ISE 學習 Windows PowerShell。

**有哪些不同？**

在 Windows PowerShell ISE 中輸入 Cmdlet 時，會顯示可捲動和可點選的功能表，可讓您瀏覽和選取適當的命令。

## <a name="snippets"></a>程式碼片段

> ISE 3.0 的新功能

*程式碼片段* 是可以插入您在 Windows PowerShell ISE 中所建立之指令碼的簡短 Windows PowerShell 程式碼區段。 Windows PowerShell ISE 隨附一組預設程式碼片段。 在 Windows PowerShell ISE 中工作時，您可以使用 `New-Snippet` Cmdlet 來新增程式碼片段。

**這個變更增加了什麼價值？**

使用程式碼片段，您可以快速地組合並建立指令碼，以自動化您的環境。

**有哪些不同？**

若要在 Windows PowerShell 3.0 或更新版本中使用程式碼片段，請按一下 [編輯] 功能表上的 [開始程式碼片段]，或按 <kbd>Ctrl</kbd>+<kbd>J</kbd>。

## <a name="add-on-tools"></a>附加元件工具

> PowerShell 3.0 的新功能

Windows PowerShell ISE 現在支援使用物件模型的附加元件工具。 這些附加元件是在主控台中顯示為垂直或水準窗格的 Windows Presentation Foundation (WPF) 控制項。 窗格中的多個附加元件工具會顯示成一個索引標籤式控制項。 您也可以新增或移除非 Microsoft 合作廠商製作的附加元件工具。 如需詳細資訊，請參閱 [Windows PowerShell ISE 指令碼物件模型的用途](../ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)。

**這個變更增加了什麼價值？**

附加元件可讓您使用可新增功能及可增強指令碼體驗的工具來擴充和自訂 Windows PowerShell ISE。

**有哪些不同？**

Windows PowerShell ISE 3.0 和更新版本隨附 **Commands** 附加元件。 **Commands** 附加元件可讓您瀏覽 Cmdlet，以及使用 指令碼 和 主控台 窗格並列存取 Cmdlet 的說明。

使用 [附加元件] 功能表上的 [開啟附加元件工具網站] 命令，可以找到額外的附加元件。

## <a name="restart-manager-and-auto-save"></a>重新啟動管理員和自動儲存

> PowerShell 3.0 的新功能

Windows PowerShell ISE 現在每兩分鐘會自動在不同的位置儲存您未完成的指令碼。 當 Windows PowerShell ISE 在非預期的當機或重新啟動之後重新開機時，會復原已在上一個工作階段中開啟的指令碼，即使指令碼並未儲存也一樣。

若要變更自動儲存間隔，請在主控台窗格中執行下列命令：`$psise.Options.AutoSaveMinuteInterval`。

**這個變更增加了什麼價值？**

由於已開啟的指令碼會自動儲存，您將能安心地在 Windows PowerShell ISE 內工作。

**有哪些不同？**

Windows PowerShell ISE 2.0 不會自動儲存指令碼。

## <a name="most-recently-used-list"></a>最近使用的清單

> PowerShell 3.0 的新功能

Windows PowerShell ISE 現在具有最近使用之檔案的清單。 當您在 Windows PowerShell ISE 中開啟檔案時，該檔案會被新增至 [檔案] 功能表上的 [最近使用的清單]。

若要變更最近使用清單中預設數目的檔案，請在主控台窗格中執行下列命令：`$psise.Options.MruCount`。

**這個變更增加了什麼價值？**

您現在可以使用最近使用的清單來輕鬆地存取常用檔案。

**有哪些不同？**

Windows PowerShell ISE 2.0 並不具有最近使用的清單。

## <a name="console-pane"></a>主控台窗格

> PowerShell 3.0 的新功能

第一版 Windows PowerShell ISE 中獨立的命令與輸出窗格已結合成單一主控台窗格。 這個主控台窗格在功能與外觀上與典型的 Windows PowerShell 主控台類似，但包含下列增強功能：

- 輸入文字 (非輸出文字) 的語法著色 (包括 XML 語法)
- IntelliSense
- 括號對稱
- 錯誤指示
- 完整 Unicode 支援
- <kbd>F1</kbd> 即時線上說明
- <kbd>Ctrl</kbd>+<kbd>F1</kbd> 即時線上顯示命令 (Show-Command)
- 複雜指令碼與由右至左語言支援
- 字型支援
- Zoom
- 行選取與區塊選取模式
- 按 <kbd>UpArrow</kbd> 以在主控台中檢視歷程記錄時，保留命令列中輸入的內容

**這個變更增加了什麼價值？**

新增這些主控台窗格變更可提供主控台介面更一致的指令碼體驗。

**有哪些不同？**

Windows PowerShell ISE 2.0 具有個別的命令和輸出窗格。

## <a name="command-line-switches"></a>命令列參數

> PowerShell 3.0 的新功能

如果透過命令列啟動 Windows PowerShell ISE (輸入 **Powershell_ise.exe** )，您可以新增下列新的命令列參數。

- `-NoProfile`：在沒有執行 `$profile` 的情況下啟動 Windows PowerShell ISE
- `-Help`：顯示 [說明] 視窗
- `-mta`：以多執行緒 Apartment 模式啟動 Windows PowerShell ISE。 Windows PowerShell ISE 的預設作業模式是單一執行緒 Apartment 模式，或 `-sta`。

**這個變更增加了什麼價值？**

新增這些命令列參數可讓您控制 Windows PowerShell ISE 的執行環境。

**有哪些不同？**

Windows PowerShell ISE 2.0 無法辨識這些命令列參數。

## <a name="new-editor-features"></a>新編輯器功能

> PowerShell 3.0 的新功能

Windows PowerShell ISE 其他的編輯功能包括：

- **XML 語法著色** - Windows PowerShell ISE 現在會以對 Windows PowerShell 語法進行著色的相同方法，對 XML 語法進行著色。
- **括號對稱** - Windows PowerShell ISE 包括括號對稱和醒目顯示，且可以透過下列方式使用：(例如，如果已選取左大括號，則使用 [移至相符項目] 命令或 <kbd>[Ctrl</kbd>+<kbd>]</kbd> 便能找到右大括號)。
- **大綱檢視** 指令碼窗格支援大綱功能，按一下左邊界的加號或減號，即允許摺疊或展開程式碼區段。 您可以使用大括號或 `#region` 和 `#endregion` 標籤來標示可摺疊區段的開頭或結尾。 若要展開或摺疊所有區域，請按 <kbd>Ctrl</kbd>+<kbd>M</kbd>。
- **拖放文字編輯** - Windows PowerShell ISE 現在支援拖放文字編輯。 您可以選取任何文字區塊，並將該文字拖曳到編輯器或主控台中的其他位置來移動文字。 如果您在拖曳選取的文字時按住 <kbd>Ctrl</kbd> 鍵，則放開滑鼠按鈕時，會將文字複製到新位置。 在此版本的 Windows PowerShell ISE 中，當您將檔案拖放到 Windows PowerShell ISE 上時，Windows PowerShell ISE 便會開啟該檔案。
- **剖析錯誤顯示** - 剖析錯誤會以紅色底線表示。 暫留於指示的錯誤時，工具提示文字會顯示在程式碼中發現的問題。
- **縮放** - 您可以使用縮放滑桿 (在 Windows PowerShell ISE 視窗的右下角) 或在主控台窗格中輸入 `$psise.options.Zoom` 命令，來設定主控台內容的縮放百分比。
- **RTF 複製與貼上** - 複製到 Windows PowerShell ISE 中的剪貼簿將會保留原始選取項目的字型、大小及色彩資訊。
- **區塊選取** - 在使用滑鼠選取指令碼窗格中的文字時按住 <kbd>ALT</kbd> 鍵或按 <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>方向鍵</kbd>，就可以選取一個區塊的文字。

**這個變更增加了什麼價值？**

其他編輯功能提供更一致且功能強大的編輯環境。

**有哪些不同？**

Windows PowerShell ISE 2.0 沒有這些編輯增強功能。

## <a name="new-help-viewer-window"></a>新的說明檢視器視窗

> PowerShell 3.0 的新功能

當您的游標在 Cmdlet 中或當您反白顯示 Cmdlet 的一部分時，如果按 <kbd>F1</kbd>，新的說明檢視器就會開啟有關反白顯示 Cmdlet 的即時線上說明。 若要顯示「關於 Windows PowerShell」說明，請在主控台窗格中輸入 `operators`，然後按 <kbd>F1</kbd>。

使用這項功能之前，請先從 Microsoft 網站下載最新版本的 Windows PowerShell 說明主題。 下載說明主題的最簡單方法是以系統管理員身分執行 Windows PowerShell ISE，並於主控台窗格中執行 `Update-Help` Cmdlet。

您可以變更 <kbd>F1</kbd> 鍵尋找說明的位置。 您在 [工具]/[選項] 功能表中，於 [一般設定] 索引標籤的 [其他設定] 下，可以設定或清除 [使用本機說明內容而非線上內容] 核取方塊。 選取時，用戶端會在模組資料夾中發現的已下載說明中尋找 Cmdlet 說明。 如果清除此核取方塊，用戶端就會在線上尋找說明。

**這個變更增加了什麼價值？**

不需要離開目前 Cmdlet 或指令碼的即時線上說明，即可提供整合的學習體驗。

**有哪些不同？**

在舊版 Windows PowerShell ISE 中按 <kbd>F1</kbd>，會開啟本機電腦上的說明檔。 在 Windows PowerShell ISE 3.0 和更新版本中，則會開啟內含可搜尋和可設定之 Cmdlet 說明的視窗。 此說明體驗為 Windows PowerShell ISE 3.0 的新功能，而可更新說明則是 Windows PowerShell 3.0 的新功能。

## <a name="show-command-cmdlet"></a>Show-Command

> PowerShell 3.0 的新功能

`Show-Command` Cmdlet 可讓您填入圖形表單來撰寫或執行 Cmdlet 或函式。 此表單可讓使用者在圖形化環境中使用 Windows PowerShell。
`Show-Command` 也可以啟用進階 Scripter 來建立快速的 Windows PowerShell 式 GUI。

**這個變更增加了什麼價值？**

透過在 Windows PowerShell 指令碼中使用 `Show-Command`，您可以提供使用者其所熟悉的圖形化環境。 `Show-Command` 也可以協助入門使用者了解 Windows PowerShell。

**有哪些不同？**

`Show-Command` 是 Windows PowerShell ISE 3.0 的新功能。

## <a name="see-also"></a>另請參閱

如需使用 Windows PowerShell ISE 的詳細資訊，請參閱[探索 Windows PowerShell 整合式指令碼環境](../ise/exploring-the-windows-powershell-ise.md)。
