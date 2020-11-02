---
ms.date: 01/02/2020
title: 如何在 Windows PowerShell ISE 中撰寫和執行指令碼
description: 此文章 說明如何在指令碼窗格中建立、編輯、執行及儲存指令碼。
ms.openlocfilehash: 8e85da1d4eecbb975f2dd799c91512e0081309d2
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663652"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>如何在 Windows PowerShell ISE 中撰寫和執行指令碼

此文章 說明如何在指令碼窗格中建立、編輯、執行及儲存指令碼。

## <a name="how-to-create-and-run-scripts"></a>如何建立和執行指令碼

您可以在指令碼窗格中開啟和編輯 Windows PowerShell 檔案。 Windows PowerShell 中需要注意的特定檔案類型包括指令碼檔案 (`.ps1`)、指令碼資料檔案 (`.psd1`) 和指令碼模組檔案 (`.psm1`)。 這些檔案類型是指令碼窗格編輯器中著色的語法。 其他可在指令碼窗格中開啟的常見檔案類型還包括組態檔 (`.ps1xml`)、XML 檔案和文字檔。

> [!NOTE]
> Windows PowerShell 執行原則會決定您是否可以執行指令碼，以及載入 Windows PowerShell 設定檔和組態檔。 預設執行原則 “Restricted” 可防止所有指令碼執行，並防止載入設定檔。 若要變更執行原則以允許載入及使用設定檔，請參閱 [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) 與 [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)。

### <a name="to-create-a-new-script-file"></a>建立新的指令碼檔案

按一下工具列中的 [新增]  ，或在 [檔案]  功能表上，按一下 [新增]  。 建立的檔案會顯示在目前 PowerShell 索引標籤下新的檔案索引標籤中。請記住，只有在有多個 PowerShell 索引標籤時，才會顯示 PowerShell 索引標籤。 預設會建立指令碼類型的檔案 (`.ps1`)，但您可以使用新名稱和副檔名來儲存這個檔案。 在同一個 PowerShell 索引標籤中，可以建立多個指令碼檔案。

### <a name="to-open-an-existing-script"></a>開啟現有的指令碼

按一下工具列中的 [開啟]  ，或在 [檔案]  功能表上，按一下 [開啟]  。 在 **[開啟]** 對話方塊中，選取您要開啟的檔案。 開啟的檔案會顯示在新的索引標籤中。

### <a name="to-close-a-script-tab"></a>關閉指令碼索引標籤

按一下您要關閉之檔案索引標籤的 **關閉** 圖示 ( **X** )，或選取 [檔案]  功能表，然後按一下 [關閉]  。

如果檔案自上次儲存後已變更，系統會提示您儲存或捨棄該檔案。

### <a name="to-display-the-file-path"></a>顯示檔案路徑

在 [檔案] 索引標籤上，指向檔案名稱。 指令碼檔案的完整路徑會顯示在工具提示中。

### <a name="to-run-a-script"></a>執行指令碼

按一下工具列中的 **[執行指令檔]** ，或在 **[檔案]** 功能表上，按一下 **[執行]** 。

### <a name="to-run-a-portion-of-a-script"></a>執行部分指令碼

1. 在指令碼窗格中，選取部分指令碼。
2. 在 **[檔案]** 功能表上，按一下 **[執行選取項目]** ，或按一下工具列中的 **[執行選取項目]** 。

### <a name="to-stop-a-running-script"></a>停止執行中的指令碼

有數種方式可停止執行中的指令碼。

- 按一下工具列上的 [停止操作] 
- 按 <kbd>CTRL</kbd>+<kbd>BREAK</kbd>
- 選取 [檔案]  功能表，然後按一下 [停止操作]  。

除非目前已選取一些文字，否則按 <kbd>CTRL</kbd>+<kbd>C</kbd> 也適用；如果已選取文字，<kbd>CTRL</kbd>+<kbd>C</kbd> 會對應至選取文字的複製功能。

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>如何在指令碼窗格中撰寫和編輯文字

您可以在指令碼窗格中複製、剪下、貼上、尋找及取代文字。 您也可以復原和取消復原剛才執行的上一個動作。 適用於這些動作的鍵盤快速鍵，與所有 Windows 應用程式所使用的鍵盤快速鍵相同。

### <a name="to-enter-text-in-the-script-pane"></a>在指令碼窗格中輸入文字

1. 將游標移至指令碼窗格，方法是按一下指令碼窗格中的任何位置，或按一下 **[檢視]** 功能表中的 **[移至指令碼窗格]** 。
2. 建立指令碼。 語法顏色設定和 TAB 鍵自動完成，會在 Windows PowerShell ISE 中提供更豐富的編輯體驗。
3. 如需使用 TAB 鍵自動完成功能以協助輸入的詳細資訊，請參閱[如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。

### <a name="to-find-text-in-the-script-pane"></a>在指令碼窗格中尋找文字

1. 若要尋找任何位置的文字，按 <kbd>CTRL</kbd>+<kbd>F</kbd>，或在 [編輯]  功能表上，按一下 [在指令碼中尋找]  。
2. 若要尋找游標後的文字，請按 <kbd>F3</kbd> 鍵，或在 **[編輯]** 功能表上，按一下 **[在指令碼中找下一個]** 。
3. 若要尋找游標之前的文字，按 <kbd>SHIFT</kbd>+<kbd>F3</kbd>，或在 [編輯]  功能表上，按一下 [在指令碼中找上一個]  。

### <a name="to-find-and-replace-text-in-the-script-pane"></a>在指令碼窗格中尋找和取代文字

按 <kbd>CTRL</kbd>+<kbd>H</kbd>，或在 [編輯]  功能表上，按一下 [在指令碼中取代]  。 輸入您要尋找的文字與取代文字，然後按 <kbd>ENTER</kbd>。

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>在指令碼窗格中移至特定文字行

1. 在 [指令碼] 窗格中，按 <kbd>CTRL</kbd>+<kbd>G</kbd>，或在 [編輯]  功能表上，按一下 [移至行]  。

2. 輸入行號。

### <a name="to-copy-text-in-the-script-pane"></a>在指令碼窗格中複製文字

1. 在指令碼窗格中，選取您要複製的文字。

2. 按 <kbd>CTRL</kbd>+<kbd>C</kbd>、按一下工具列上的 **複製** 圖示，或按一下 [編輯]  功能表上的 [複製]  。

### <a name="to-cut-text-in-the-script-pane"></a>在指令碼窗格中剪下文字

1. 在指令碼窗格中，選取您要剪下的文字。
2. 按 <kbd>CTRL</kbd>+<kbd>X</kbd>、按一下工具列上的 **剪下** 圖示，或按一下 [編輯]  功能表上的 [剪下]  。

### <a name="to-paste-text-into-the-script-pane"></a>在指令碼窗格中貼上文字

按 <kbd>CTRL</kbd>+<kbd>V</kbd>、按一下工具列上的 **貼上** 圖示，或按一下 [編輯]  功能表上的 [貼上]  。

### <a name="to-undo-an-action-in-the-script-pane"></a>在指令碼窗格中復原動作

按 <kbd>CTRL</kbd>+<kbd>Z</kbd>、按一下工具列上的 **復原** 圖示，或按一下 [編輯]  功能表上的 [復原]  。

### <a name="to-redo-an-action-in-the-script-pane"></a>在指令碼窗格中取消復原動作

按 <kbd>CTRL</kbd>+<kbd>Y</kbd>、按一下工具列上的 **取消復原** 圖示，或按一下 [編輯]  功能表上的 [取消復原]  。

## <a name="how-to-save-a-script"></a>如何儲存指令碼

指令碼名稱旁若出現星號，表示檔案自變更後尚未儲存。 儲存檔案之後，星號就會消失。

### <a name="to-save-a-script"></a>儲存指令碼

按 <kbd>CTRL</kbd>+<kbd>S</kbd>、按一下工具列上的 **儲存** 圖示，或按一下 [檔案]  功能表上的 [儲存]  。

### <a name="to-save-and-name-a-script"></a>儲存並命名指令碼

1. 在 **[檔案]** 功能表上，按一下 **[另存新檔]** 。 **[另存新檔]** 對話方塊隨即出現。
2. 在 **[檔案名稱]** 方塊中，輸入檔案的名稱。
3. 在 **[檔案類型]** 方塊中，選取檔案類型。 例如，在 [檔案類型]  方塊中，選取 [PowerShell 指令碼 (`*.ps1`)]。
4. 按一下 [檔案]  。

### <a name="to-save-a-script-in-ascii-encoding"></a>以 ASCII 編碼方式儲存指令碼

根據預設，Windows PowerShell ISE 會以 Unicode (BigEndianUnicode) 格式儲存新的指令碼檔案 (`.ps1`)、指令碼資料檔案 (`.psd1`) 和指令碼模組檔案 (`.psm1`)。 若要以 ASCII (ANSI) 等其他編碼方式儲存指令碼，請在 [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) 物件上使用 **Save** 或 **SaveAs** 方法。

下列命令會以 ASCII 編碼方式，將新的指令碼另存為 MyScript.ps1。

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

下列命令會以同名但使用 ASCII 編碼方式的檔案，取代目前的指令碼檔案。

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

下列命令會取得目前檔案的編碼方式。

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE 支援下列編碼選項：ASCII、BigEndianUnicode、Unicode、UTF32、UTF7、UTF8 及 Default。 預設選項的值會因系統而異。

當您使用 [儲存] 或 [另存新檔] 命令時，Windows PowerShell ISE 不會變更指令碼檔案的編碼。

## <a name="see-also"></a>另請參閱

- [探索 Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
