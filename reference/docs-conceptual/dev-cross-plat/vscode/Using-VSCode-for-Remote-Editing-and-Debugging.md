---
title: 使用 Visual Studio Code 來進行遠端編輯與偵錯
description: 使用 Visual Studio Code 來進行遠端編輯與偵錯
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809274"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>使用 Visual Studio Code 來進行遠端編輯與偵錯

對於熟悉使用 ISE 的人，可能還記得可以從整合式主控台執行 `psedit file.ps1`，以直接在 ISE 中開啟檔案 (本機或遠端)。

適用於 VSCode 的 PowerShell 延伸模組中也提供此功能。 此指南將示範如何執行此動作。

## <a name="prerequisites"></a>Prerequisites

此指南假設您有：

- 您有權存取的遠端資源 (例如：VM、容器)
- 在遠端資源和主機電腦中執行的 PowerShell
- VSCode 和適用於 VSCode 的 PowerShell 延伸模組

此功能可在 Windows PowerShell 和 PowerShell Core 上運作。

透過 WinRM、PowerShell Direct 或 SSH 連線至遠端電腦時，也可以使用此功能。 如果想要使用 SSH，但現在使用 Windows，請參閱 [SSH 的 Win32 版本](https://github.com/PowerShell/Win32-OpenSSH) \(英文\)！

> [!IMPORTANT]
> `Open-EditorFile` 和 `psedit` 命令只能在適用於 VSCode 的 PowerShell 延伸模組所建立的 **PowerShell 整合式主控台**中運作。

## <a name="usage-examples"></a>使用範例

這些範例將示範如何從 MacBook Pro，對在 Azure 中執行的 Ubuntu VM 進行遠端編輯和偵錯。 此程序在 Windows 上完全相同。

### <a name="local-file-editing-with-open-editorfile"></a>使用 Open-EditorFile 編輯本機檔案

當適用於 VSCode 的 PowerShell 延伸模組已啟動且 PowerShell 整合式主控台已開啟之後，我們可以輸入 `Open-EditorFile foo.ps1` 或 `psedit foo.ps1`，以直接在編輯器中開啟本機 foo.ps1 檔案。

![Open-EditorFile foo.ps1 可在本機運作](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> `foo.ps1` 檔案必須已經存在。

我們可以從那裡：

- 在巡覽邊新增中斷點

  ![在巡覽邊新增中斷點](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- 按 F5 以針對 PowerShell 指令碼進行偵錯。

  ![針對 PowerShell 本機指令碼進行偵錯](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

偵錯時，可以與偵錯主控台互動，查看左側範圍中和所有其他標準偵錯工具中的變數。

### <a name="remote-file-editing-with-open-editorfile"></a>使用 Open-EditorFile 編輯遠端檔案

現在讓我們進入遠端檔案編輯和偵錯。 步驟幾乎完全相同，只是要先做一件事，那就是在遠端伺服器中啟動我們的 PowerShell 工作階段。

有一個 Cmdlet 可執行此動作。 它稱為 `Enter-PSSession`。

下面提供該 Cmdlet 的說明：

- `Enter-PSSession -ComputerName foo` 會透過 WinRM 啟動一個工作階段
- `Enter-PSSession -ContainerId foo` 和 `Enter-PSSession -VmId foo` 會透過 PowerShell Direct 啟動一個工作階段
- `Enter-PSSession -HostName foo` 會透過 SSH 啟動一個工作階段

如需詳細資訊，請參閱適用於 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) 的文件。

由於我們要從 macOS 前往 Azure 中的 Ubuntu VM，因此會使用 SSH 進行遠端處理。

首先，在整合式主控台中，執行 `Enter-PSSession`。 當 `[<hostname>]` 顯示於您提示字元的最左邊時，表示您已連線到遠端工作階段。

![呼叫 Enter-PSSession](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

現在，我們可以執行與編輯本機指令碼相同的步驟。

1. 執行 `Open-EditorFile test.ps1` 或 `psedit test.ps1` 以開啟遠端 `test.ps1` 檔案

  ![Open-EditorFile test.ps1 檔案](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. 編輯檔案/設定中斷點

   ![編輯並設定中斷點](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. 開始針對遠端檔案進行偵錯 (F5)

   ![針對遠端檔案進行偵錯](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

如果您有任何問題，您可以在 [GitHub 存放庫](https://github.com/powershell/vscode-powershell) \(英文\) 中提出問題。
