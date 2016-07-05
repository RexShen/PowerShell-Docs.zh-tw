---
title: "PowerShell 50 ISE 的新功能"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 7be11016317a65565dd9af2a3f65e8f00b3818f3

---

# Windows PowerShell ISE 的新功能
本主題說明已在 Windows PowerShell® 整合式指令碼環境 (ISE) 版本中引進的新功能和更新功能。

## <a name="overview"></a>功能說明
Windows PowerShell ISE 是一個主應用程式，可以讓您在圖形化與直覺式的環境中撰寫、執行及測試指令碼和模組。 語法著色、TAB 鍵自動完成、視覺化偵錯、Unicode 相容性和即時線上說明這類主要功能提供豐富的指令碼撰寫體驗。

如需 Windows PowerShell ISE 的概觀，請參閱 [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/en-us/library/3c1892c2-bf84-4cb6-af26-1f453be9e671) (Windows PowerShell 整合式指令碼環境 (ISE))。

## <a name="versions"></a>Windows PowerShell ISE 的新功能和變更功能
下表列出 Windows PowerShell 中這版 Windows PowerShell ISE 的新功能和變更功能。

|功能 (feature)\/功能 (functionality)|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[Intellisense](#BKMK_Intellisense)**|X|X||
|**[程式碼片段](#bkmk_snippets)**|X|X||
|**[附加元件工具](#BKMK_AddOnTools)**|X|X||
|**[重新啟動管理員和自動儲存](#BKMK_RestartMgr)**|X|X||
|**[主控台窗格](#BKMK_ConsolePane)**|X|X||
|**[最近使用的清單](#BKMK_MRU)**|X|X||
|**[命令列參數](#BKMK_CommandLine)**|X|X||
|**[新編輯器功能](#BKMK_NewEditorFeatures)**|X|X||
|**[新的說明檢視器視窗](#BKMK_NewHelpViewer)**|X|X||
|**[Show-Command](#BKMK_ShowCommand)**|X|X||

### <a name="BKMK_Intellisense"></a>Intellisense
**ISE 3.0 的新功能**

Intellisense 是屬於 Windows PowerShell ISE 的自動完成協助功能。 在您輸入文字時，Intellisense 會顯示與輸入文字可能相符的 Cmdlet、參數、參數值、檔案或資料夾的可點選功能表。

**這個變更增加了什麼價值？**

透過 Intellisense，您可以在使用 Windows PowerShell ISE 建立指令碼時更輕鬆地探索 Cmdlet 和語法。 您也可以在建立新指令碼時透過 Windows PowerShell ISE 學習 Windows PowerShell。

**有哪些不同？**

在 Windows PowerShell ISE 3.0 或更新版本中輸入 Cmdlet 時，會顯示可捲動和可點選的功能表，可讓您瀏覽和選取適當的命令。

### <a name="BKMK_Snippets"></a>程式碼片段
**ISE 3.0 的新功能**

*程式碼片段*是可以插入您在 Windows PowerShell ISE 中所建立之指令碼的簡短 Windows PowerShell 程式碼區段。 Windows PowerShell ISE 隨附一組預設程式碼片段。 在 Windows PowerShell ISE 中工作時，您可以使用 **New\-Snippet** Cmdlet 來新增程式碼片段。

**這個變更增加了什麼價值？**

使用程式碼片段，您可以快速地組合並建立指令碼，以自動化您的環境。

**有哪些不同？**

若要在 Windows PowerShell 3.0 或更新版本中使用程式碼片段，請按一下 **[編輯]** 功能表上的 **[啟動片段]**，或按 **Ctrl\-J**。

### <a name="BKMK_AddOnTools"></a>附加元件工具
**PowerShell 3.0 的新功能**

Windows PowerShell ISE 現在支援附加元件工具，這些工具是使用物件模型所新增的 Windows Presentation Foundation (WPF) 控制項。 附加元件工具在主控台中可以顯示為垂直或水平窗格。 窗格中的多個附加元件工具會顯示成一個索引標籤式控制項。 您也可以新增或移除非 Microsoft 集團成員製作的附加元件工具。 如需如何匯入或移除附加元件工具的詳細資訊，請參閱 [Windows PowerShell ISE 作業](http://technet.microsoft.com/library/cc732148.aspx)。

**這個變更增加了什麼價值？**

附加元件可讓您使用可加強指令碼體驗或為 Windows PowerShell ISE 新增功能的工具來擴充和自訂 Windows PowerShell ISE。

**有哪些不同？**

Windows PowerShell ISE 3.0 和更新版本隨附 **Commands** 附加元件。 **Commands** 附加元件可讓您瀏覽 Cmdlet，以及使用 **[指令碼]** 和 **[主控台]** 窗格並列存取 Cmdlet 的說明。

使用 **[附加元件]** 功能表上的 **[開啟附加元件工具網站]** 命令，可以找到額外的附加元件。

### <a name="BKMK_RestartMgr"></a>重新啟動管理員與自動儲存
**PowerShell 3.0 的新功能**

Windows PowerShell ISE 現在每兩分鐘會自動在不同的位置儲存您未完成的指令碼。  如果 Windows PowerShell ISE 停止運作，或是作業系統重新啟動，則 Windows PowerShell ISE 在重新啟動之後，將會復原上一個工作階段中未完成的指令碼，即使該指令碼之前並未儲存也一樣。

若要變更自動儲存間隔，請在主控台窗格中執行下列命令：**$psise.Options.AutoSaveMinuteInterval**。

**這個變更增加了什麼價值？**

由於已開啟的指令碼會在意外重新啟動的情況下自動儲存，您將能安心地在 Windows PowerShell ISE 內工作。

**有哪些不同？**

Windows PowerShell ISE 2.0 不會在重新啟動的情況下自動儲存指令碼。

### <a name="BKMK_MRU"></a>最近使用的清單
**PowerShell 3.0 的新功能**

Windows PowerShell ISE 現在提供最近使用的檔案清單。 當您在 Windows PowerShell ISE 中開啟檔案時，該檔案會被新增至 **[檔案] ** 功能表上最近使用的清單。

若要變更最近使用清單中預設數目的檔案，請在主控台窗格中執行下列命令：**$psise.Options.MruCount**。

**這個變更增加了什麼價值？**

您現在可以使用最近使用的清單來輕鬆地存取常用檔案。

**有哪些不同？**

Windows PowerShell ISE 2.0 沒有最近使用的清單。

### <a name="BKMK_ConsolePane"></a>主控台窗格
**PowerShell 3.0 的新功能**

第一版 Windows PowerShell ISE 中獨立的命令與輸出窗格已結合成單一主控台窗格。 這個主控台窗格在功能和外觀上與典型的 Windows PowerShell 主控台類似，但包含下列增強功能 (大部分已在本主題中描述)。

-   輸入文字 (非輸出文字) 的語法著色 (包括 XML 語法)

-   Intellisense

-   括號對稱

-   錯誤指示

-   完整 Unicode 支援

-   **F1** 即時線上說明

-   **Ctrl\+F1** 線上即時顯示命令

-   複雜指令碼與由右至左語言支援

-   字型支援

-   縮放

-   行選取與區塊選取模式

-   按**向上**鍵以在主控台中檢視歷程記錄時，保留命令列中輸入的內容

**這個變更增加了什麼價值？**

新增這些主控台窗格變更可提供主控台介面的更一致指令碼體驗。

**有哪些不同？**

Windows PowerShell ISE 2.0 具有個別的命令和輸出窗格。

### <a name="BKMK_CommandLine"></a>命令列參數
**PowerShell 3.0 的新功能**

如果透過命令列啟動 Windows PowerShell ISE (輸入 **Powershell\_ise.exe**)，您可以新增下列新的命令列參數。

-   *\-NoProfile*：在沒有執行 **$profile** 的情況下啟動 Windows PowerShell ISE。

-   *\-Help*：顯示 [說明] 視窗

-   *\-mta*：以多執行緒 Apartment 模式啟動 Windows PowerShell ISE。 Windows PowerShell ISE 的預設作業模式是單一執行緒 Apartment 模式，或 *\-sta*。

**這個變更增加了什麼價值？**

新增這些命令列參數可讓您控制 Windows PowerShell ISE 的執行環境。

**有哪些不同？**

Windows PowerShell ISE 2.0 無法辨識這些命令列參數。

### <a name="BKMK_NewEditorFeatures"></a>新編輯器功能
**PowerShell 3.0 的新功能**

Windows PowerShell ISE 其他的編輯功能包括：

-   **XML 語法著色**Windows PowerShell ISE 現在會以對 Windows PowerShell 語法進行著色的相同方法，對 XML 語法進行著色。

-   **括號對稱** Windows PowerShell ISE 包括括號對稱和反白顯示，而且可以透過下列方式使用：(例如，如果已選取左括號，則使用 **[移至相符項目]** 命令或 **Ctrl \+ ]** 便能找到右括號)。

-   **大綱檢視** 指令碼窗格支援大綱功能，按一下左邊界的加號或減號，即允許摺疊或展開程式碼區段。 您可以使用括號或 **\#region** 和 **\#endregion** 標籤，標示可摺疊區段的開頭或結尾。 若要展開或摺疊所有區域，請按 **Ctrl \+ M**。

-   **拖放文字編輯**Windows PowerShell ISE 現在支援拖放文字編輯。 您可以選取任何文字區塊，並將該文字拖曳到編輯器或主控台中的其他位置來移動文字。 如果您在拖曳選取的文字時按住 Ctrl 鍵，則放開滑鼠按鈕時，會將文字複製到新位置。 在此版本及舊版的 Windows PowerShell ISE 中，當您將檔案拖放到 Windows PowerShell ISE 上時，Windows PowerShell ISE 便會開啟該檔案。

-   **剖析錯誤顯示** 剖析錯誤會以紅色底線表示。 暫留於指示的錯誤時，工具提示文字會顯示在程式碼中發現的問題。

-   **縮放** 您可以使用縮放滑桿 (在 Windows PowerShell ISE 視窗的右下角) 或在主控台窗格中輸入 **$psise.options.Zoom** 命令，來設定主控台內容的縮放百分比。

-   **RTF 複製與貼上** 複製到 Windows PowerShell ISE 中的剪貼簿將會保留原始選取項目的字型、大小及色彩資訊。

-   **區塊選擇** 在使用滑鼠選取指令碼窗格中的文字時按住 ALT 鍵或按 **Alt\+Shift\+方向鍵**，就可以選取一個區塊的文字。

**這個變更增加了什麼價值？**

其他編輯功能提供更一致且功能強大的編輯環境。

**有哪些不同？**

Windows PowerShell ISE 2.0 沒有這些編輯增強功能。

### <a name="BKMK_NewHelpViewer"></a>新的說明檢視器視窗
**PowerShell 3.0 的新功能**

當您的游標在 Cmdlet 中或當您反白顯示 Cmdlet 的一部分時，如果按 **F1**，新的說明檢視器就會開啟有關反白顯示 Cmdlet 的即時線上說明。 如果要顯示「關於 Windows PowerShell 」說明，請在主控台窗格中輸入 **operators**，然後按 **F1**。

使用這項功能之前，請先從 Microsoft 網站下載最新版本的 Windows PowerShell 說明主題。 下載說明主題的最簡單方法是以系統管理員身分執行 Windows PowerShell ISE，並於主控台窗格中執行 **Update\-Help** Cmdlet。

您可以變更 **F1** 鍵尋找說明的位置。 您在 [工具]****\/[選項]**** 功能表中，於 [一般設定]**** 索引標籤的 [其他設定]**** 下，可以設定或清除 [使用本機說明內容而非線上內容]**** 核取方塊。 核取時，用戶端會在模組資料夾中發現的已下載說明中尋找 Cmdlet 說明。  如果清除此核取方塊，則用戶端會在 TechNet 文件庫中尋找 Cmdlet 說明。

**這個變更增加了什麼價值？**

不需要離開目前 Cmdlet 或指令碼的即時線上說明，可提供順暢的學習經驗。

**有哪些不同？**

在舊版的 Windows PowerShell ISE 中按 F1，會開啟本機電腦上的說明檔。 在 Windows PowerShell ISE 3.0 和更新版本中，則會開啟內含可搜尋和可設定之 Cmdlet 說明的視窗。 此說明體驗為 Windows PowerShell ISE 3.0 的新功能，而可更新說明則是 Windows PowerShell 3.0 的新功能。

### <a name="BKMK_ShowCommand"></a>Show\-Command Cmdlet
**PowerShell 3.0 的新功能**

**Show\-Command** Cmdlet 可讓您填入圖形表單，來撰寫或執行 Cmdlet 或函數。 此表單可讓使用者在圖形化環境中使用 Windows PowerShell。 **Show\-Command** 也可以啟用進階 Scripter 來建立快速的 Windows PowerShell 式 GUI。

**這個變更增加了什麼價值？**

透過在 Windows PowerShell 指令碼中使用 **Show\-Command**，您可以提供使用者其所熟悉的圖形化環境。 **Show\-Command** 也可以協助入門使用者了解 Windows PowerShell。

**有哪些不同？**

Show\-Command 為 Windows PowerShell ISE 3.0 的新功能。

## <a name="BKMK_LINKS"></a>另請參閱
如需在 Windows PowerShell 中使用 Windows PowerShell ISE 的詳細資訊，請參閱下列連結。

-   [使用 Windows PowerShell 整合式指令碼環境](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

-   [TechNet Wiki 上的 ISE](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)

-   [Script Center](http://technet.microsoft.com/scriptcenter/default)




<!--HONumber=Jun16_HO4-->


