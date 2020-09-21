---
ms.date: 06/11/2020
keywords: powershell,cmdlet
title: PowerShell 字彙
ms.openlocfilehash: 8df76fa3a78e9701c28488db0bde25fa245b1160
ms.sourcegitcommit: 56463fb628a7d83dec4364e89417d83316c3e53b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2020
ms.locfileid: "84722859"
---
# <a name="powershell-glossary"></a>PowerShell 字彙

|            詞彙             | 定義 |
| --------------------------- | ---------- |
| 二進位模組               | 根模組是二進位模組檔 (.dll) 的 PowerShell 模組。 二進位模組不一定包括模組資訊清單。 |
| 一般參數            | 由 PowerShell 引擎新增至所有 Cmdlet、進階功能及工作流程的參數。 |
| 點溯源                  | 在 PowerShell 中，於命令前面輸入點和空格來啟動命令。 為點溯源的命令是在目前範圍內執行，而不是在新範圍內。 命令所建立的任何變數、別名、函式或磁碟機都是在目前範圍內建立，並且在命令完成時可供使用者使用。 |
| 動態模組              | 只存在於記憶體中的模組。 New-Module 和 Import-PSSession Cmdlet 會建立動態模組。 |
| 動態參數           | 在特定情況下新增至 PowerShell Cmdlet、函式或指令碼的參數。 Cmdlet、函式、提供者和指令碼可以新增動態參數。 |
| 格式檔案             | PowerShell XML 檔案，其副檔名為 `.format.ps1xml` 並定義 PowerShell 如何根據 .NET Framework 類型來顯示物件。 |
| 全域工作階段狀態        | 工作階段狀態，內含 PowerShell 工作階段使用者可存取的資料。 |
| 主機                        | PowerShell 引擎用來與使用者通訊的介面。 例如，主機指定如何處理 PowerShell 與使用者之間的提示。 |
| 主應用程式            | 將 PowerShell 引擎載入其處理序中，並用於執行作業的程式。 |
| 輸入處理方法     | Cmdlet 可用來處理接收為輸入之記錄的方法。 輸入處理方法包括 BeginProcessing 方法、ProcessRecord 方法、EndProcessing 方法和 StopProcessing 方法。 |
| 資訊清單模組             | 具有資訊清單且其 RootModule 索引鍵空白的 PowerShell 模組。 |
| name                      | 可重複使用的獨立性單位，其可供分割、組織和擷取 PowerShell 程式碼。 模組可以包含 Cmdlet、提供者、函式、變數以及可匯入為單一單位的其他類型資源。 |
| 模組資訊清單             | 描述模組內容並控制模組處理方式的 PowerShell 資料檔 (`.psd1`)。 |
| 模組工作階段狀態        | 工作階段狀態，內含 PowerShell 模組的公用和私用資料。 PowerShell 工作階段使用者無法使用此工作階段狀態中的私用資料。 |
| 非終止錯誤       | 不會停止 PowerShell 繼續處理命令的錯誤。 |
| 名詞                        | PowerShell Cmdlet 名稱中連字號後面的文字。 名詞描述此 Cmdlet 所處理的資源。 |
| 參數集               | 可在相同命令中用來執行特定動作的一組參數。 |
| 管道                        | 在 PowerShell 中，將上一個命令結果傳送為管線中下一個命令的輸入。 |
| 管線                    | 透過管線運算子 (&#124;) (ASCII 124) 連接的一系列命令。 每一個管線運算子都會將上一個命令的結果傳送為下一個命令的輸入。 |
| PowerShell Cmdlet           | 參與 PowerShell 管線語意的單一命令。 包含二進位 (C#) Cmdlet、進階指令碼函式、CDXML 以及工作流程。 |
| PowerShell 命令          | 管線中導致執行動作的元素。PowerShell 命令是透過鍵盤輸入或透過程式設計方式叫用。 |
| PowerShell 資料檔        | 副檔名為 `.psd1` 的文字檔。 PowerShell 會基於各種用途使用資料檔；例如，儲存模組資訊清單資料，以及儲存進行指令碼國際化的已翻譯字串。 |
| PowerShell 磁碟機            | 直接存取資料存放區的虛擬磁碟機。 這種磁碟機可由 PowerShell 提供者所定義或在命令列中建立。 在命令列建立的磁碟機是工作階段特定磁碟機，並在關閉工作階段時中斷。 |
| provider                    | Microsoft .NET Framework 程式，可讓特殊資料存放區中的資料在 PowerShell 中使用，以供檢視並加以管理。 |
| PSSession                   | 使用者所建立、管理和關閉的 PowerShell 工作階段類型。 |
| 根模組                 | 模組資訊清單中 RootModule 索引鍵所指定的模組。 |
| Runspace                    | 在 PowerShell 中，為管線中每個命令提供執行位置的作業環境。 |
| 指令碼區塊                | 在 PowerShell 程式設計語言中，可用作單一單元的陳述式或運算式集合。 指令碼區塊可以接受引數和傳回值。 |
| 指令碼檔案                 | 副檔名為 `.ps1` 的檔案，並包含使用 PowerShell 語言所撰寫的指令碼。 |
| 指令碼模組               | 其根模組是指令碼模組檔案 (`.psm1`) 的 PowerShell 模組。 指令碼模組不一定包括模組資訊清單。 |
| 指令碼模組檔案          | 包含 PowerShell 指令碼的檔案。 指令碼定義指令碼模組所匯出的成員。 指令碼模組檔案的副檔名為 `.psm1`。 |
| 殼層                       | 用來將命令傳遞給作業系統的命令直譯器。 |
| 切換參數            | 不接受引數的參數。 |
| 終止錯誤           | 會停止 PowerShell 處理命令的錯誤。 |
| 交易                 | 不可部分完成的工作單位。 交易中必須整體完成的工作；如果交易的任何部分失敗，整個交易都會失敗。 |
| 類型檔案                  | PowerShell XML 檔案，其副檔名為 `.ps1xml` ，且其會擴充 PowerShell 中 Microsoft .NET Framework 類型的屬性。 |
| 動詞命令                        | PowerShell Cmdlet 名稱中連字號前面的文字。 動詞描述 Cmdlet 所執行的動作。 |
| Windows PowerShell ISE      | 整合式指令碼環境 - Windows PowerShell 主應用程式，其可供執行命令，以及在易記、語法著色、Unicode 相容的環境中撰寫、測試和偵錯指令碼。 |
| Windows PowerShell 嵌入式管理單元  | 定義可新增至 Windows PowerShell 環境之一組 Cmdlet、提供者和 Microsoft .NET Framework 類型的資源。 |
| Windows PowerShell 工作流程 | 工作流程是一連串的程式化、連接步驟，執行長時間執行的工作，或是需要跨多個裝置或受控節點協調多個步驟。 Windows PowerShell 工作流程可讓 IT 專業人員和開發人員將連續的多重裝置管理活動或工作流程內的單一工作，編寫為工作流程。 Windows PowerShell 工作流程可供調整 PowerShell 指令碼與 XAML 檔案並作為工作流程執行。 |
