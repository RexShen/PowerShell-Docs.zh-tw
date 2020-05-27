---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 簡介
ms.openlocfilehash: 3e4471d0982ba4d7ef1a9d59906a9ff297f6f7cb
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808714"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell 整合式指令碼環境 (ISE) 是適用於 Windows PowerShell 的主機應用程式。 在 ISE 中，您可以執行命令，並在以 Windows 為基礎的單一圖形化使用者介面中撰寫、測試及偵錯指令碼。 ISE 提供多行編輯、TAB 鍵自動完成、語法顏色設定、選擇性執行、即時線上說明，以及支援從右至左的語言。 功能表項目與鍵盤快速鍵會對應到您在 Windows PowerShell 主控台中執行的許多相同工作。 例如，當您在 ISE 中偵錯指令碼時，可在編輯窗格中以滑鼠右鍵按一下程式碼行來設定中斷點。

## <a name="support"></a>支援

ISE 最初是透過 Windows PowerShell V2 引進，並透過 PowerShell V3 重新設計。 Windows PowerShell V5.1 (含) 以下的所有 Windows PowerShell 版本均支援 ISE。

> [!NOTE]
> 我們將不再為 PowerShell ISE 開發新功能。 因為此功能屬於 Windows 的出貨元件，所以官方仍會繼續支援其安全性與高優先順序的服務修正。
> 目前尚無任何計劃要將 ISE 從 Windows 移除。
>
> PowerShell v6 及更新版本不支援 ISE。 使用者如有需要 ISE 的替代解決方案，可使用 [Visual Studio Code](https://code.visualstudio.com/) 搭配 [PowerShell 延伸模組](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)。

## <a name="key-features"></a>重要功能

Windows PowerShell ISE 的重要功能包括：

- 多行編輯：若要在 [命令] 窗格中目前的行下方插入空白行，請按 <kbd>SHIFT</kbd>+<kbd>ENTER</kbd>。
- 選擇性執行：若要執行指令碼中的某部分，請選取您要執行的文字，然後按一下 [執行指令碼]  按鈕。 您也可以按 <kbd>F5</kbd>。
- 即時線上說明：鍵入 `Invoke-Item`，然後按 <kbd>F1</kbd>。 說明檔案會隨即開啟，並顯示 `Invoke-Item` Cmdlet 的相關文章。

Windows PowerShell ISE 可讓您自訂其部分外觀。 它也有自己的 Windows PowerShell 設定檔指令碼。

## <a name="to-start-the-windows-powershell-ise"></a>啟動 Windows PowerShell ISE

按一下 [開始]  、選取 [Windows PowerShell]  ，然後按一下 [Windows PowerShell ISE]  。
或者，您可以在任何命令殼層或在 [執行] 方塊中輸入 `powershell_ise.exe`。

## <a name="to-get-help-in-the-windows-powershell-ise"></a>在 Windows PowerShell ISE 中取得說明

在 **[說明]** 功能表上，按一下 **[Windows PowerShell 說明]** 。 您也可以按 <kbd>F1</kbd>。 開啟的檔案將會說明 Windows PowerShell ISE 與 Windows PowerShell，包括 `Get-Help` Cmdlet 所提供的所有說明。
