---
title: 探索 Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
---
# 探索 Windows PowerShell ISE
您可以使用 [!INCLUDE[ise_1](../Token/ise_1_md.md)] 建立、執行及偵錯命令和指令碼。 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 是由功能表列、Windows PowerShell 索引標籤、工具列、指令碼索引標籤、指令碼窗格、主控台窗格、狀態列、文字大小滑桿和即時線上說明所組成。

> [!NOTE]
> 從 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 開始，命令窗格和輸出窗格已合併為單一主控台窗格。

## 功能表列
功能表列包含 **[檔案]**、**[編輯]**、**[檢視]**、**[工具]**、**[偵錯]**、**[附加元件]** 和 **[說明]** 功能表。 功能表上的按鈕可讓您在 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 中執行與寫入和執行指令碼，以及執行命令相關的工作。 此外，您可以執行使用 [Windows PowerShell ISE 指令碼物件模型](https://technet.microsoft.com/en-us/library/1737ddb7-c20d-4e6b-a0d3-68cc2650f2a1)的指令碼，將 [[附加元件] 功能表](https://technet.microsoft.com/en-us/library/412dd662-417a-4661-ada2-558802d0f6d2#submenus)放在功能表列上。

> [!NOTE]
> 在 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 中，不提供 **[工具]** 和 **[附加元件]** 功能表。

## Windows PowerShell 索引標籤
Windows PowerShell 索引標籤是 Windows PowerShell 指令碼的執行環境。 您可以在 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 中開啟新的 Windows PowerShell 索引標籤，以在您的本機電腦或遠端電腦上建立個別環境。 您最多可以同時開啟 8 個 PowerShell 索引標籤。

## 工具列
您可以在工具列上找到下列按鈕。

|按鈕|函式|
|----------|------------|
|**新增**|開啟新的指令碼。|
|**開啟**|開啟現有的指令碼或檔案。|
|**儲存**|儲存指令碼或檔案。|
|**剪下**|剪下選取的文字並複製到剪貼簿。|
|**複製**|將選取文字複製到剪貼簿。|
|**貼上**|在游標位置貼上剪貼簿的內容。|
|**清除輸出窗格**|清除輸出窗格中的所有內容。|
|**復原**|回復剛才執行的動作。|
|**取消復原**|執行剛才復原的動作。|
|**執行指令碼**|執行指令碼。|
|**執行選取項目**|執行選取的指令碼部分。|
|**停止執行**|停止執行指令碼。|
|**新增遠端 PowerShell 索引標籤**|建立新的 PowerShell 索引標籤，以在遠端電腦上建立工作階段。 對話方塊隨即出現，並提示您輸入建立遠端連線所需的詳細資料。|
|**啟動 PowerShell.exe**|開啟 PowerShell 主控台。|
|**靠上顯示指令碼窗格**|將指令碼窗格移至顯示畫面上方。|
|**靠右顯示指令碼窗格**|將指令碼窗格移至顯示畫面右側。|
|**顯示最大化的指令碼窗格**|將指令碼窗格最大化。|

## 指令碼索引標籤
顯示您正在編輯的指令碼名稱。 您可以按一下指令碼索引標籤，選取要編輯的指令碼。

當您指向指令碼索引標籤時，指令碼檔案的完整路徑會顯示在工具提示中。

## 指令碼窗格
可讓您建立及執行指令碼。 您可以在指令碼窗格中開啟、編輯及執行現有的指令碼。

## 輸出窗格
顯示已執行的命令和指令碼結果。 您也可以複製並清除輸出窗格中的內容。

## 命令窗格
可讓您撰寫命令。 您可以在命令窗格中執行一或多行命令。 按 SHIFT+ENTER 可輸入多行命令的每一行，而在最後一行後面按 ENTER 鍵可執行多行命令。 出現在命令窗格頂端的提示會顯示目前工作目錄的路徑。

## 狀態列
可讓您查看所執行的命令和指令碼是否已完成。 狀態列位於顯示畫面最底部。 錯誤訊息的選定部分會顯示在狀態列上。

## 文字大小滑桿
增加或減少螢幕上文字的大小。

## [說明]
您可以在 TechNet Library 網站上取得 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 的說明。 開啟 [說明] 的方式是在 **[說明]** 功能表上按一下 **[Windows PowerShell ISE 說明]**，或在在指令碼窗格或主控台窗格的任何位置按下 F1 鍵 (但游標不可以在 Cmdlet 名稱上方)。 您也可以從 **[說明]** 功能表執行 Update-Help Cmdlet，並顯示命令視窗，透過顯示 Cmdlet 的所有參數並讓您在容易使用的表單中填入參數，來協助您建構命令。

## 另請參閱
[使用 Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO2-->


