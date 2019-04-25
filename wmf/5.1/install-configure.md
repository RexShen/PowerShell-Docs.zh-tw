---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
contributor: keithb
title: 安裝與設定 WMF 5.1
ms.openlocfilehash: c439d0851189a89a81fa38194632dc54475a001d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084992"
---
# <a name="install-and-configure-wmf-51"></a>安裝與設定 WMF 5.1

## <a name="download-and-install-the-wmf-51-package"></a>下載並安裝 WMF 5.1 套件

為適用於其安裝所在的作業系統和架構下載 WMF 5.1 封裝︰

| 作業系統       | 必要條件           | 封裝連結                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:**[Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:**[Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:**[Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:**[Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>安裝適用於 Windows Server 2008 R2 和 Windows 7 的 WMF 5.1

> [!NOTE]
> Windows Server 2008 R2 和 Windows 7 的安裝指示已變更，且與其他套件的指示不同。 適用於 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的安裝指示如下。

**在 Windows Server 2008 R2 和 Windows 7 上安裝 WMF 5.1**

1. 瀏覽至您用來下載 ZIP 檔案的資料夾。

2. 以滑鼠右鍵按一下 ZIP 檔案，並選取 [解壓縮全部...]。 ZIP 包含 2 個檔案︰MSU 和 Install-WMF5.1.PS1 指令碼檔案。
一旦您解壓縮 ZIP 檔案，您可以將內容複製到執行 Windows 7 或 Windows Server 2008 R2 的任何電腦。

3. 將 ZIP 檔案內容解壓縮之後，以系統管理員身分開啟 PowerShell，然後瀏覽至包含 ZIP 檔案的資料夾。

4. 在該資料夾中執行 Install-Wmf5.1.ps1 指令碼，並遵循指示。 此指令碼會檢查本機電腦上的必要條件，並安裝 WMF 5.1 (如果符合必要條件)。 以下列出必要條件。

Install-WMF5.1.ps1 會採用下列參數以簡化針對 Windows Server 2008 R2 和 Windows 7 上安裝的自動化：

- AcceptEula：當包含此參數時，會自動接受 EULA 且不會顯示。
- AllowRestart：此參數只能在指定 AcceptEula 時使用。 如果包含此參數，且安裝 WMF 5.1 之後需要重新啟動，則在完成安裝之後會立即重新啟動而不提示。

**Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 必要條件**

在 Windows Server 2008 R2 SP1 或 Windows 7 SP1 上安裝 WMF 5.1 需要下列各項：
- 必須安裝最新的 Service Pack。
- 「不可以」安裝 WMF 3.0。 在具有 WMF 3.0 的情況下安裝 WMF 5.1 會導致 PSModulePath 遺失，這可能造成其他應用程式失敗。 在安裝 WMF 5.1 之前，您必須將 WMF 3.0 解除安裝，或是儲存 PSModulePath，並在完成 WMF 5.1 安裝之後，將它手動還原。
- WMF 5.1 需要至少[.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642)。
您可以遵循下載位置的指示來安裝 Microsoft.NET Framework 4.5.2。

**WinRM 相依性**

Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。
在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。
若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 `Set-WSManQuickConfig`。

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>安裝適用於 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的 WMF 5.1

**從 Windows 檔案總管 (或 Windows Server 2012 R2 或 Windows 8.1 中的檔案總管) 安裝**

1. 瀏覽至您用來下載 MSU 檔案的資料夾。
2. 按兩下 MSU 以執行。

**從命令提示字元安裝**

1. 下載您電腦架構的正確封裝之後，以提高的使用者權限 (以系統管理員身分執行) 開啟 [命令提示字元] 視窗。 在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的 Server Core 安裝選項上，預設會以提高的使用者權限開啟 [命令提示字元]。
2. 將目錄變更為您已下載或複製 WMF 5.1 安裝封裝的資料夾。
3. 執行下列其中一個命令：
   - 在執行 Windows Server 2012 R2 或 Windows 8.1 x64 的電腦上執行 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`。
   - 在執行 Windows Server 2012 的電腦上執行 `W2K12-KB3191565-x64.msu /quiet`。
   - 在執行 Windows 8.1 x86 的電腦上執行 `Win8.1-KB3191564-x86.msu /quiet`。

> [!NOTE]
> 安裝 WMF 5.1 需要重新開機。 使用 `/quiet` 選項會將系統重新開機，而不發出警告。
> 使用 `/norestart` 選項可避免重新開機。 不過，在重新開機之前都不會安裝 WMF 5.1。
