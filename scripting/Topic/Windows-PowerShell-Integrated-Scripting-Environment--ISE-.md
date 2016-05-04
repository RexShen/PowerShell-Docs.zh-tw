---
title: Windows PowerShell 整合式指令碼環境 (ISE)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
---
# Windows PowerShell 整合式指令碼環境 (ISE)
Windows PowerShell 整合式指令碼環境 (ISE) 是 Windows PowerShell 引擎和語言之兩部主機的其中一部。 您可以使用它，透過 Windows PowerShell 主控台中無法使用的方式來撰寫、執行和測試指令碼。 ISE 新增語法著色、Tab 鍵自動完成、IntelliSense、視覺化偵錯和即時線上說明。

ISE 可讓您在主控台窗格中執行命令，但也支援數個窗格，可用來同時檢視您的指令碼和可插入 ISE 之其他工具的原始碼。 您甚至可以同時開啟多個指令碼視窗，這在所偵錯的指令碼使用其他指令碼或模組中所定義的函式時特別有用。

## <a name="BKMK_NEW"></a>新功能
以下是一些已在最新版的 PowerShell ISE 中新增的功能。

### PowerShell 3.0 的新功能 (Windows Server 2012、Windows 8)
在您輸入文字時，**IntelliSense** 透過顯示與輸入文字相符的 Cmdlet、參數、參數值、檔案或資料夾的功能表，來自動完成命令。

**程式碼片段**是可輕鬆地插入所撰寫指令碼的簡短程式碼區段。 有用程式碼片段的集合包含在方塊中，而且使用 **New-Snippet** Cmdlet 可以有更多的程式碼片段。

撰寫與 [Windows PowerShell ISE 指令碼物件模型](assetId:///69b047d0-da79-413e-b948-8e45d05d1f85)互動的程式碼，即可建立將功能新增至 ISE 的**附加元件工具**。 這些工具可以在索引標籤式窗格中顯示控制項，或在背景無形地工作。 **命令**附加元件是不錯的範例，並包含 3.0 版和更新版本，以顯示可用命令的清單和其說明。

**[重新啟動管理員和自動儲存]** 每兩分鐘會自動儲存您的指令碼，協助您避免在當機或意外重新啟動時遺失工作。

**[最近使用的清單]** 現在是 [開啟舊檔] 功能表的一部分，讓您更輕鬆地取得您最常使用的檔案。

**合併的主控台窗格**。 在舊版的 ISE 中，具有個別的 [命令] 和 [輸出] 窗格。 它們現在合併成單一窗格，更直接與您在 Windows Powershell 主控台中看到的內容相似。

**命令列參數**。 數個新的命令列參數可讓您更充分掌控 ISE 的運作方式。 –NoProfile 會啟動 ISE，但不執行設定檔指令碼。 –Help 會開啟含 ISE 的說明視窗。 –mta 會使用「多執行緒 Apartment 模式」來啟動 ISE。 預設值是單一執行緒。

**新編輯器功能**可輕鬆地建立和讀取您的程式碼︰

-   **XML 語法著色**。 ISE 編輯器現在將 XML 語法著色，方法與將 Windows PowerShell 程式碼語法著色相同。

-   **括號對稱**。 ISE[!INCLUDE[ise_2](../Token/ise_2_md.md)] 會反白顯示對稱的括號，協助您確保左右括號數目相符。 使用 CTRL- [ 找出與游標所在左括號對稱的右括號。

-   **大綱檢視**。 您可以按一下左邊界的加號和減號，來摺疊或展開程式碼區段。 這可讓您更輕鬆地找到您要在長指令碼中尋找的程式碼。

-   **拖放文字編輯**。 您可以選取某區塊的文字，並將它拖曳至另一個位置來移動它。 如果您在按住 Ctrl 鍵時拖曳選取的文字，則會進行複製，而不是移動。

-   **剖析錯誤顯示**。 當您輸入時，Windows PowerShell 會檢查您的指令碼。 如果它偵測到錯誤，則會在違規程式碼下顯示紅色曲線。 暫留於指示的錯誤時，工具提示會顯示發現的問題。

-   **縮放**。 您可以使用 ISE 視窗右下角的滑桿來放大文字，以輕鬆地讀取或縮小來查看較大的圖片。

-   **RTF 複製與貼上**。 從 ISE 複製到剪貼簿時，會包括所選取文字的字型、大小和色彩資訊。

-   **區塊選擇**。 在使用滑鼠選取指令碼窗格中的文字時按住 ALT 鍵或按 **Alt+Shift+方向鍵**，就可以選取一個區塊形狀的文字區塊。

### PowerShell 2.0 的新功能 (Windows Server 2008 R2、Windows 7)
ISE 是在 PowerShell 2.0 版引進。

## Windows PowerShell ISE 的執行需求
ISE 可以在任何可執行 Windows PowerShell 2.0 版或更新版本的電腦上使用。 每個版本的 Windows 和 Windows Server 都包括某個版本的 Windows PowerShell 和 ISE，但您可以安裝 Windows Management Framework 來升級到最新可用版本。 執行這項搜尋來尋找可用的最新版本︰[下載試用](http://www.microsoft.com/en-us/search/DownloadResults.aspx?q=%22windows%20management%20framework%22%20PowerShell&sortby=Relevancy~Descending)。 請注意，任何標示 "Preview" 的項目都是搶鮮版程式碼，而不是完整功能。

> [!NOTE]
> 因為 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 需要圖形化使用者介面，所以無法在 Windows Server 的 Server Core 選項上執行它。

## <a name="BKMK_LINKS"></a>另請參閱
[使用 Windows PowerShell 整合式指令碼環境](http://technet.microsoft.com/library/cc732148.aspx)



<!--HONumber=Apr16_HO1-->


