---
ms.date: 06/10/2020
ms.topic: conceptual
keywords: wmf,powershell,設定
contributor: keithb
title: 安裝與設定 WMF 5.1
ms.openlocfilehash: 9e0b4b6ed387b0a0d7fcf62a913677986d70de92
ms.sourcegitcommit: 4a283fe5419f47102e6c1de7060880a934842ee9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84671388"
---
# <a name="install-and-configure-wmf-51"></a>安裝與設定 WMF 5.1

> [!IMPORTANT]
> WMF 5.1 已取代 WMF 5.0。 使用 WMF 5.0 的使用者必須升級至 WMF 5.1 才能獲得支援。
> **WMF 5.1 需要 .NET Framework 4.5.2** (或更新版本)。 雖然安裝會成功，但若未安裝 .NET 4.5.2 (或更新版本)，主要功能將會失敗。

## <a name="download-and-install-the-wmf-51-package"></a>下載並安裝 WMF 5.1 套件

為適用於其安裝所在的作業系統和架構下載 WMF 5.1 封裝︰

| 作業系統       | Prerequisites           | 封裝連結                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- 安裝 WMF 5.1 RTM 之前，必須先解除安裝 WMF 5.1 Preview。
- WMF 5.1 可直接透過 WMF 5.0 或 WMF 4.0 安裝。
- 在 Windows 7 和 Windows Server 2008 R2 上安裝 WMF 5.1 之前，**不需要**先安裝 WMF 4.0。

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>安裝適用於 Windows Server 2008 R2 和 Windows 7 的 WMF 5.1

> [!NOTE]
> Windows Server 2008 R2 和 Windows 7 的安裝指示已變更，且與其他套件的指示不同。 適用於 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的安裝指示如下。

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 必要條件

在 Windows Server 2008 R2 SP1 或 Windows 7 SP1 上安裝 WMF 5.1 需要下列各項：

- 必須安裝最新的 Service Pack。
- 「不可以」安裝 WMF 3.0。 在具有 WMF 3.0 的情況下安裝 WMF 5.1 會導致 **PSModulePath** (`$env:PSModulePath`) 遺失，這可能造成其他應用程式失敗。 在安裝 WMF 5.1 之前，您必須解除安裝 WMF 3.0，或是儲存 **PSModulePath**，並在完成 WMF 5.1 安裝之後手動將其還原。
- WMF 5.1 需要至少[.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642)。 您可以遵循下載位置的指示來安裝 Microsoft.NET Framework 4.5.2。

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>在 Windows Server 2008 R2 和 Windows 7 上安裝 WMF 5.1

1. 瀏覽至您用來下載 ZIP 檔案的資料夾。

1. 以滑鼠右鍵按一下 ZIP 檔案，並選取 [解壓縮全部...]。ZIP 檔案包含兩個檔案：MSU 和 `Install-WMF5.1.ps1` 指令碼檔案。 一旦您解壓縮 ZIP 檔案，您可以將內容複製到執行 Windows 7 或 Windows Server 2008 R2 的任何電腦。

1. 將 ZIP 檔案內容解壓縮之後，以系統管理員身分開啟 PowerShell，然後瀏覽至包含 ZIP 檔案的資料夾。

1. 在該資料夾中執行 `Install-WMF5.1.ps1` 指令碼，並遵循指示。 此指令碼會檢查本機電腦上的必要條件，並安裝 WMF 5.1 (如果符合必要條件)。 以下列出必要條件。

   `Install-WMF5.1.ps1` 會採用下列參數以簡化針對 Windows Server 2008 R2 和 Windows 7 上安裝的自動化：

   - **AcceptEula**：當包含此參數時，會自動接受 EULA 且不會顯示。
   - **AllowRestart**：此參數只能在指定 AcceptEula 時使用。 如果包含此參數，且安裝 WMF 5.1 之後需要重新啟動，則在完成安裝之後會立即重新啟動而不提示。

## <a name="winrm-dependency"></a>WinRM 相依性

Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。 在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。 若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 `Set-WSManQuickConfig`。

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>安裝適用於 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的 WMF 5.1

### <a name="install-from-windows-file-explorer"></a>從 Windows 檔案總管安裝

1. 瀏覽至您用來下載 MSU 檔案的資料夾。
1. 按兩下 MSU 以執行。

### <a name="installing-from-the-command-prompt"></a>從命令提示字元安裝

1. 下載您電腦架構的正確封裝之後，以提高的使用者權限 (以系統管理員身分執行) 開啟 [命令提示字元] 視窗。 在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的 Server Core 安裝選項上，預設會以提高的使用者權限開啟 [命令提示字元]。
1. 將目錄變更為您已下載或複製 WMF 5.1 安裝封裝的資料夾。
1. 執行下列其中一個命令：
   - 在執行 Windows Server 2012 R2 或 Windows 8.1 x64 的電腦上執行 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet /norestart`。
   - 在執行 Windows Server 2012 的電腦上執行 `W2K12-KB3191565-x64.msu /quiet /norestart`。
   - 在執行 Windows 8.1 x86 的電腦上執行 `Win8.1-KB3191564-x86.msu /quiet /norestart`。

   > [!NOTE]
   > 安裝 WMF 5.1 需要重新開機。 單獨使用 `/quiet` 選項將會在沒有警告的情況下重新開機系統。 使用 `/norestart` 選項可避免重新開機。 不過，在重新開機之前都不會安裝 WMF 5.1。
