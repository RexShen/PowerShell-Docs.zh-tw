---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell ISE 簡介
ms.openlocfilehash: b09e64d0258d11f1f16f96b319ef232ebdfa0c49
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="introducing-the-windows-powershell-ise"></a>Windows PowerShell ISE 簡介

Windows PowerShell 整合式指令碼環境 (ISE) 是適用於 Windows PowerShell 的主機應用程式。 在 Windows PowerShell ISE 中，您可以在單一 Windows 架構的圖形化使用者介面中執行命令，以及撰寫、測試及偵錯指令碼，此介面支援多行編輯、Tab 鍵自動完成、語法著色、選擇式執行、即時線上說明，以及從右至左的語言支援。 您可以使用功能表項目與鍵盤快速鍵，來執行您在 Windows PowerShell 中執行的許多相同工作。 例如，當您在 Windows PowerShell ISE 中針對指令碼進行偵錯時，若要在指令碼中設定行中斷點，可在程式碼行上按一下滑鼠右鍵，然後按一下 [切換中斷點]。

在 Windows PowerShell ISE 中嘗試使用這些功能

- 多行編輯：若要在 [命令] 窗格中的目前行下插入空行，請按 SHIFT+ENTER。
- 選擇性執行：若要執行指令碼中的某部分，請選取您要執行的文字，然後按一下 **[執行指令碼]** 按鈕。 或者，按下 F5。
- 即時線上說明：輸入 **Invoke-Item**，然後按 F1。 隨即開啟說明檔案，並顯示 **Invoke-Item** Cmdlet 的說明主題。

Windows PowerShell ISE 可讓您自訂其部分外觀。 它也有自己的 Windows PowerShell 設定檔，您可以在其中儲存您在 Windows PowerShell ISE 中使用的函式、別名、變數與命令。

## <a name="to-start-the-windows-powershell-ise"></a>啟動 Windows PowerShell ISE

執行下列其中一個動作：

- 按一下 **[開始]**、指向 **[所有程式]**、指向 **[Windows PowerShell V2]**，然後按一下 **[Windows PowerShell ISE]**。
- 在 Windows PowerShell 主控台 Cmd.exe 或 [執行] 方塊中，輸入 **powershell_ise.exe**。

## <a name="to-get-help-in-the-windows-powershell-ise"></a>在 Windows PowerShell ISE 中取得說明

在 **[說明]** 功能表上，按一下 **[Windows PowerShell 說明]**。 或者，按下 F1。 開啟的檔案會描述 Windows PowerShell ISE 與 Windows PowerShell，包括可從 Get-Help Cmdlet 取得的所有說明。