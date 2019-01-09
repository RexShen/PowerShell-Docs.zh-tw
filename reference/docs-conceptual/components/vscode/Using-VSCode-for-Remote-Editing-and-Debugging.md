---
title: 使用 Visual Studio Code 來進行遠端編輯與偵錯
description: 使用 Visual Studio Code 來進行遠端編輯與偵錯
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655584"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>使用 Visual Studio Code 來進行遠端編輯與偵錯

對於您已熟悉使用 ISE，您可能還記得，您可以執行`psedit file.ps1`從整合式主控台來開啟檔案-本機或遠端-以滑鼠右鍵在 ISE 中。

其實，這項功能也是用於 VSCode 的 PowerShell 延伸模組。 本指南將示範如何執行此動作。

## <a name="prerequisites"></a>必要條件

本指南假設您有：

- 遠端資源 (例如： VM 時，容器)，您必須擁有存取權
- 它與主機電腦上執行的 PowerShell
- VSCode，VSCode 的 PowerShell 延伸模組

這項功能適用於 Windows PowerShell 和 PowerShell Core。

連接到遠端電腦透過 WinRM、 PowerShell Direct 或 SSH 時，也適用於這項功能。 如果您想要使用 SSH，但使用 Windows，請參閱[SSH Win32 版本](https://github.com/PowerShell/Win32-OpenSSH)！

## <a name="lets-go"></a>開始

在本節中，我將逐步遠端編輯和偵錯從我的 Iphone，以在 Azure 中執行的 Ubuntu VM。 我可能不會使用 Windows，但**程序是相同**。

### <a name="local-file-editing-with-open-editorfile"></a>使用開放 EditorFile 編輯本機檔案

使用 PowerShell 延伸模組啟動 VSCode，並開啟 PowerShell 整合式主控台中，我們可以輸入`Open-EditorFile foo.ps1`或`psedit foo.ps1`在編輯器中開啟本機 foo.ps1 檔案權限。

![在本機開啟 EditorFile foo.ps1 運作方式](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 必須已經存在。

在這裡，我們可以：

將中斷點加入至巡覽邊![加入到邊的中斷點](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

然後按 F5 以偵錯 PowerShell 指令碼。
![PowerShell 的本機指令碼偵錯](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

偵錯時，您可以與偵錯主控台互動，查看在左側，而所有其他標準偵錯工具的範圍中的變數。

### <a name="remote-file-editing-with-open-editorfile"></a>使用開放 EditorFile 編輯遠端檔案

現在讓我們進入遠端檔案編輯和偵錯。 步驟幾乎完全相同，我們需要先進行-我們的 PowerShell 工作階段輸入到遠端伺服器的只是一件事。

若要這樣做沒有一個 cmdlet。 它會呼叫`Enter-PSSession`。

灌了水，向下的說明內容是 cmdlet 的：

- `Enter-PSSession -ComputerName foo` 啟動工作階段透過 WinRM
- `Enter-PSSession -ContainerId foo` 和`Enter-PSSession -VmId foo`開始透過 PowerShell Direct 工作階段
- `Enter-PSSession -HostName foo` 啟動透過 SSH 工作階段

如需詳細資訊`Enter-PSSession`，查看文件[這裡](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6)。

我將使用 SSH 進行遠端處理因為我從 macOS 要在 Azure 中的 Ubuntu VM。

首先，在整合式主控台中，讓我們執行我們 Enter-pssession。 您知道您正在工作階段中，因為`[something]`會顯示您的提示字元的左邊。

![Enter-pssession 呼叫](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

在這裡，我們可以處理的確切步驟，如同我們先前所編輯的本機指令碼。

1. 執行`Open-EditorFile test.ps1`或是`psedit test.ps1`以開啟遠端`test.ps1`檔案![開放 EditorFile test.ps1 檔案](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. 編輯檔案/設定中斷點 ![編輯，並設定中斷點](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. 開始偵錯 (F5) 的遠端檔案

![偵錯遠端檔案](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

這樣就完成了 ！ 我們希望本指南協助清除任何關於遠端偵錯和編輯在 VSCode 中的 PowerShell 的問題。

如果您有任何問題，歡迎提出問題[GitHub 儲存機制](http://github.com/powershell/vscode-powershell)。
