---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 簡介
ms.openlocfilehash: d27a0eb594d7271121cee59f38d096995cc98648
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133075"
---
# <a name="introducing-the-windows-powershell-ise"></a>Windows PowerShell ISE 簡介

Windows PowerShell 整合式指令碼環境 (ISE) 是適用於 Windows PowerShell 的主機應用程式。 在 Windows PowerShell ISE 中，您可以執行命令，並在以 Windows 為基礎的單一圖形化使用者介面中撰寫、測試及偵錯指令碼。 此介面提供多行編輯、TAB 鍵自動完成、語法顏色設定、選擇性執行、即時線上說明，以及支援從右至左的語言。 功能表項目與鍵盤快速鍵會對應到您在 Windows PowerShell 主控台中執行的許多相同工作。 例如，當您在 Windows PowerShell ISE 中針對指令碼進行偵錯時，您可以利用滑鼠右鍵按一下程式碼行以設定中斷點。

在 Windows PowerShell ISE 中嘗試使用這些功能

- 多行編輯：若要在 [命令] 窗格中的目前行下插入空行，請按 SHIFT+ENTER。
- 選擇性執行：若要執行指令碼中的某部分，請選取您要執行的文字，然後按一下 **[執行指令碼]** 按鈕。 或者，按下 F5。
- 即時線上說明：輸入 **Invoke-Item**，然後按 F1。 說明檔案隨即開啟，並顯示適用於 **Invoke-Item** Cmdlet 的文章。

Windows PowerShell ISE 可讓您自訂其部分外觀。 它也有自己的 Windows PowerShell 設定檔指令碼。

## <a name="to-start-the-windows-powershell-ise"></a>啟動 Windows PowerShell ISE

按一下 [開始]、選取 [Windows PowerShell]，然後按一下 [Windows PowerShell ISE]。
或者，您可以在任何命令殼層或在 [執行] 方塊中輸入 `powershell_ise.exe`。

## <a name="to-get-help-in-the-windows-powershell-ise"></a>在 Windows PowerShell ISE 中取得說明

在 [說明] 功能表上，按一下 [Windows PowerShell 說明]。 或者，按下 F1。 開啟的檔案會描述 Windows PowerShell ISE 與 Windows PowerShell，包括可從 Get-Help Cmdlet 取得的所有說明。