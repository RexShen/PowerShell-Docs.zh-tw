---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 簡介
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411577"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell 整合式指令碼環境 (ISE) 是適用於 Windows PowerShell 的主機應用程式。 在 ISE 中，您可以執行命令和撰寫、 測試，並在單一的以 Windows 為基礎的圖形化使用者介面中的指令碼偵錯。 ISE 提供多行編輯、 tab 鍵自動完成、 語法著色、 選擇性執行、 即時線上說明及支援從右至左的語言。 功能表項目與鍵盤快速鍵會對應到您在 Windows PowerShell 主控台中執行的許多相同工作。 比方說，當您偵錯指令碼在 ISE 中的，您可以以滑鼠右鍵按一下編輯窗格來設定中斷點的程式碼行。

## <a name="support"></a>支援

ISE 最初是使用 Windows PowerShell V2 和 PowerShell V3 的重新設計。 ISE 支援所有支援的最高的 Windows PowerShell，包括 Windows PowerShell V5.1 版本。 ISE 中，不過，為 maintennce 模式，而且可能會加入任何新功能。
此外，也沒有 ISE 與 PowerShell v6 及更新版本的支援。 使用者想要的圖形工具，用來管理等 PowerShell scrips，應該考慮[Visual Studio Code](https://code.visualstudio.com/)。

## <a name="key-features"></a>重要功能

在 Windows PowerShell ISE 中的主要功能包括：

- 多行編輯：若要在 [命令] 窗格中在目前的行下插入空行，請按下 SHIFT+ENTER。
- 選擇性執行：若要執行指令碼中的某部分，請選取您要執行的文字，然後按一下 [執行指令碼] 按鈕。 或者，按下 F5。
- 即時線上說明：鍵入 **Invoke-Item**，然後按 F1。 說明檔案隨即開啟，並顯示適用於 **Invoke-Item** Cmdlet 的文章。

Windows PowerShell ISE 可讓您自訂其部分外觀。 它也有自己的 Windows PowerShell 設定檔指令碼。

## <a name="to-start-the-windows-powershell-ise"></a>啟動 Windows PowerShell ISE

按一下 [開始]、選取 [Windows PowerShell]，然後按一下 [Windows PowerShell ISE]。
或者，您可以在任何命令殼層或在 [執行] 方塊中輸入 `powershell_ise.exe`。

## <a name="to-get-help-in-the-windows-powershell-ise"></a>在 Windows PowerShell ISE 中取得說明

在 **[說明]** 功能表上，按一下 **[Windows PowerShell 說明]**。 或者，按下 F1。 開啟的檔案會描述 Windows PowerShell ISE 與 Windows PowerShell，包括可從 Get-Help Cmdlet 取得的所有說明。
