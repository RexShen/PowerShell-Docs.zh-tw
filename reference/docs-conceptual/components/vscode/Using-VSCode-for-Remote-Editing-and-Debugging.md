---
title: 使用 Visual Studio Code 來進行遠端編輯與偵錯
description: 使用 Visual Studio Code 來進行遠端編輯與偵錯
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086660"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>使用 Visual Studio Code 來進行遠端編輯與偵錯

對於已經熟悉使用 ISE 的人，可能還記得可以從整合式主控台執行 `psedit file.ps1` 以直接在 ISE 中開啟檔案 (本機或遠端)。

其實適用於 VSCode 的 PowerShell 延伸模組中也提供此功能。 此指南將示範如何執行此動作。

## <a name="prerequisites"></a>必要條件

此指南假設您有：

- 您擁有存取權的遠端資源 (例如：VM、容器)
- 在遠端資源和主機電腦中執行的 PowerShell
- VSCode 和適用於 VSCode 的 PowerShell 延伸模組

此功能可在 Windows PowerShell 和 PowerShell Core 上運作。

透過 WinRM、PowerShell Direct 或 SSH 連線至遠端電腦時，也可以使用此功能。 如果想要使用 SSH，但現在使用 Windows，請參閱 [SSH 的 Win32 版本](https://github.com/PowerShell/Win32-OpenSSH) \(英文\)！

## <a name="lets-go"></a>開始

在此節中，我將透過 MacBook Pro 逐步示範並說明對 Azure 中執行的 Ubuntu VM 進行遠端編輯和偵錯。 我可能不會再使用 Windows 示範一次，不過**程序完全相同**。

### <a name="local-file-editing-with-open-editorfile"></a>使用 Open-EditorFile 編輯本機檔案

當適用於 VSCode 的 PowerShell 延伸模組已啟動且 PowerShell 整合式主控台已開啟之後，我們可以輸入 `Open-EditorFile foo.ps1` 或 `psedit foo.ps1`，以直接在編輯器中開啟本機 foo.ps1 檔案。

![Open-EditorFile foo.ps1 可在本機運作](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 必須已經存在。

我們可以從那裡：

將中斷點新增至巡覽邊![將中斷點新增至巡覽邊](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png) \(英文\)，

然後按 F5 以針對 PowerShell 指令碼進行偵錯。
![針對 PowerShell 本機指令碼進行偵錯](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png) \(英文\)

偵錯時，可以與偵錯主控台互動，查看左側範圍中和所有其他標準偵錯工具中的變數。

### <a name="remote-file-editing-with-open-editorfile"></a>使用 Open-EditorFile 編輯遠端檔案

現在讓我們進入遠端檔案編輯和偵錯。 步驟幾乎完全相同，只是要先做一件事，那就是在遠端伺服器中啟動我們的 PowerShell 工作階段。

有一個 Cmdlet 可執行此動作。 它稱為 `Enter-PSSession`。

下面提供該 Cmdlet 的說明：

- `Enter-PSSession -ComputerName foo` 會透過 WinRM 啟動一個工作階段
- `Enter-PSSession -ContainerId foo` 和 `Enter-PSSession -VmId foo` 會透過 PowerShell Direct 啟動一個工作階段
- `Enter-PSSession -HostName foo` 會透過 SSH 啟動一個工作階段

如需 `Enter-PSSession` 的詳細資訊，請參閱[這裡](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6) \(英文\) 的文件。

我將使用 SSH 進行遠端處理，因為我要從 macOS 前往 Azure 中的 Ubuntu VM。

首先，在整合式主控台中執行我們的 Enter-PSSession。 您將會知道您正在工作階段中，因為 `[something]` 會顯示在您系統提示的左邊。

![呼叫 Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

我們可以從這裡依據之前編輯好的本機指令碼，確切地執行每個步驟。

1. 執行 `Open-EditorFile test.ps1` 或 `psedit test.ps1` 以開啟遠端 `test.ps1` 檔案 ![Open-EditorFile the test.ps1 檔案](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. 編輯檔案/設定中斷點 ![編輯並設定中斷點](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. 開始針對遠端檔案進行偵錯 (F5)

![針對遠端檔案進行偵錯](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

這樣就完成了！ 我們希望此指南能協助您解決和在 VSCode 中進行遠端偵錯和編輯 PowerShell 有關的問題。

如果您有任何問題，歡迎前往 [GitHub 存放庫](http://github.com/powershell/vscode-powershell) \(英文\) 提出問題。
