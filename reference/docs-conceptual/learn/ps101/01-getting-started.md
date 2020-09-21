---
title: 開始使用 PowerShell
description: 在哪裡可以找到 PowerShell，以及如何為新使用者啟動 PowerShell。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8938a5d36cd1c9c5a74eed1c22cd5d0e1a91966
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786742"
---
# <a name="chapter-1---getting-started-with-powershell"></a>第 1 章 - PowerShell 使用者入門

在會議和使用者群組會議上，我經常發現一些入門級新手使用 PowerShell 進行簡報。 本書一開始會回答上述會議中未使用過 PowerShell 的與會者詢問的問題。

具體而言，本章重點在於尋找和啟動 PowerShell，並解決新使用者在開始使用 PowerShell 時會遇到的難題。 請務必在您的 Windows 10 實驗室環境電腦上依照本章所示範例逐步操作。

## <a name="what-do-i-need-to-get-started-with-powershell"></a>開始使用 PowerShell 時需要什麼？

所有新式版本 Windows 作業系統均已隨附安裝 PowerShell。 如果您執行的版本低於 5.1，請務必安裝最新版本。

- 如需升級到 Windows PowerShell 5.1，請參閱[升級現有的 Windows PowerShell][]
- 如需安裝最新版的 PowerShell，請參閱[安裝 PowerShell][]

## <a name="where-do-i-find-powershell"></a>在哪裡可以找到 PowerShell？

在 Windows 10 上尋找 PowerShell 最簡單的方式，就是在搜尋列中輸入 **PowerShell** (如圖1-1 所示)。

![圖 1-1 - 在 [開始] 功能表中搜尋 PowerShell](media/figure1-1.png)

請注意，圖 1-1 中顯示 PowerShell 的四個不同捷徑。 本書中用來示範的電腦是執行 64 位元版本的 Windows 10，因此如同捷徑上 (x86) 尾碼所示，有 64 位元版本和 32 位元版本的 PowerShell 主控台和 PowerShell ISE (整合式指令碼環境)。 如果您執行的是 32 位元版本的 Windows 10，則只會有兩個捷徑。 這些項目沒有 (x86) 尾碼，但為 32 位元版本。 如果您使用的是 64 位元的作業系統，建議您執行 64 位元版本的 PowerShell (除非有特定原因需要執行 32 位元版本)。

如需在其他版本的 Windows 上啟動 PowerShell 的資訊，請參閱[啟動 Windows PowerShell][]。

## <a name="how-do-i-launch-powershell"></a>如何啟動 PowerShell？

在支援的生產企業環境中，我使用三個不同的 Active Directory 使用者帳戶。 我已在本書使用的實驗室環境中鏡像這些帳戶。 我以非網域或本機系統管理員的網域使用者身分登入 Windows 10 電腦。

我已透過點選「Windows PowerShell」捷徑，啟動 PowerShell 主控台 (如圖 1-1 所示)。

![圖 1-4 - PowerShell 視窗的標題列](media/figure1-4.png)

請注意，PowerShell 主控台的標題列會顯示「Windows PowerShell」 (如圖 1-4 所示)。 有些命令運作順利，但 PowerShell 無法參與使用者存取控制 (UAC)。 這表示它無法針對需要系統管理員核准的工作提示提高權限。
系統會產生下列錯誤訊息：

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

此問題的解決方法是以本機系統管理員作為網域使用者的身分執行 PowerShell。
這是我第二個網域使用者帳戶的設定方式。 此帳戶使用權限最低的主體，因此不得為網域系統管理員，或是在網域中具有較高權限者。

關閉 PowerShell。 重新開機 PowerShell 主控台，但這次請在 [Windows PowerShell] 捷徑上按一下滑鼠右鍵，然後選取 [以系統管理員身分執行] (如圖 1-5 所示)。

![圖 1-5 - 操作功能表 - [以系統管理員身分執行]](media/figure1-5.png)

如果您是以一般使用者的身分登入 Windows，系統會提示您輸入認證。 我會輸入使用者帳戶的認證，其身分為網域使用者和本機系統管理員 (如圖 1-6 所示)。

![圖 1-6](media/figure1-6.png)

以系統管理員身分重新啟動 PowerShell 後，標題列應該會顯示「系統管理員：Windows PowerShell」(如圖 1-7 所示)。

![圖 1-7](media/figure1-7.png)

現在 PowerShell 是以本機系統管理員提升權限的身分執行，因此，在本機電腦上執行命令而通常需要提示提高權限時，不會再出現 UAC 的問題。 請記住，從這個已提升權限的 PowerShell 主控台執行個體執行的任何命令，也會以提高權限執行。

為了簡化尋找 PowerShell 並以系統管理員的身分啟動，建議您將 PowerShell 釘選到工作列，並將其設定為每次執行時自動以管理員身分啟動。

再次搜尋 PowerShell，但這次請在其上按一下滑鼠右鍵，然後選取 [釘選到工作列] (如圖 1-8 所示)。

![圖 1-8](media/figure1-8.png)

在現在已釘選到工作列的 PowerShell 快捷方式上按一下滑鼠右鍵，然後選取 [屬性]，如圖1-9 所示。

![圖 1-9 - 使用者帳戶控制 - 輸入認證](media/figure1-9.png)

按一下圖 1-10 中 #1 所表示的 [進階]，然後勾選圖 1-10 中 #2 所表示的 [以系統管理員身分執行] 核取方塊，然後按兩下 [確定] 以接受變更並退出兩個對話方塊。

![圖 1-10 - 顯示「系統管理員」的標題列](media/figure1-10.png)

您永遠無需再擔心如何尋找 PowerShell，或 PowerShell 是否以系統管理員身分執行。

以系統管理員身分執行已提高權限的 PowerShell 以避免發生 UAC 問題，這個作法只會影響針對本機電腦執行的命令。 而不會影響以遠端電腦為目標的命令。

## <a name="what-version-of-powershell-am-i-running"></a>我正在執行哪個版本的 PowerShell？

PowerShell 中有數個自動變數可儲存狀態資訊。 其中一個變數是 `$PSVersionTable`，其中包含可用於顯示相關 PowerShell 版本資訊的雜湊表：

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

新版 Windows PowerShell 以作為 Windows Management Framework (WMF) 的一部分來發佈。 視 WMF 版本決定所需要的特定版本的 .NET Framework。 如需升級到 Windows PowerShell 5.1，請參閱[升級現有的 Windows PowerShell][]。

## <a name="execution-policy"></a>執行原則

相對於普遍的看法，PowerShell 中的執行原則並非安全性界限。 其設計目的是要防止使用者在不知情的情況之下執行指令碼。 已確定的使用者可以輕鬆略過 PowerShell 中的執行原則。 表 1-2 顯示目前 Windows 作業系統的預設執行原則。

| Windows 作業系統版本 | 預設執行原則 |
| -------------------------------- | ------------------------ |
| Server 2019                      | 遠端簽署            |
| Server 2016                      | 遠端簽署            |
| Windows 10                       | Restricted               |

無論執行原則設定為何，PowerShell 命令都可以互動方式執行。 執行原則只會影響在指令碼中執行的命令。 `Get-ExecutionPolicy` Cmdlet 是用來判斷目前的執行原則設定，而 `Set-ExecutionPolicy` Cmdlet 則是用來變更執行原則。 建議使用 **RemoteSigned** 原則，此原則會要求下載的指令碼必須由信任的發行者簽署才能執行。

檢查目前的執行原則：

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

當執行原則設定為 **Restricted** 時，就無法執行 PowerShell 指令碼。 這是所有 Windows 用戶端作業系統上的預設設定。 若要示範此問題，請將下列程式碼儲存為名為 `Stop-TimeService.ps1`的 `.ps1` 檔案。

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

只要以系統管理員的身分執行提高權限的 PowerShell，該命令就會以互動方式執行而不會發生錯誤。 但是如果儲存為指令碼檔案並嘗試執行指令碼時，就會產生錯誤：

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

請注意，上一組結果所顯示的錯誤會明確告訴您問題為何 (此系統上已停用執行指令碼)。 當您在 PowerShell 中執行命令並產生錯誤訊息時，請務必詳閱錯誤訊息，而不只是重新執行命令，一昧希望這樣就能夠順利執行。

將 PowerShell 執行原則變更為遠端簽署。

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

請務必閱讀變更執行原則時所顯示的警告。 另外，建議您參閱 [about_Execution_Policies][] 說明主題，以確保您瞭解變更執行原則對安全性的影響。

現已將執行原則設定為 **RemoteSigned**，`Stop-TimeService.ps1` 指令碼會正常執行而不會發生錯誤。

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

請務必先啟動 Windows 時間服務，再繼續進行，否則可能會遇到未預期的問題。

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a>摘要

在本章中，您已瞭解如何尋找和啟動 PowerShell，以及如何建立以系統管理員身分啟動 PowerShell 的捷徑。 您也已瞭解預設執行原則以及如何變更。

## <a name="review"></a>檢閱

1. 如何判斷電腦正在執行的 PowerShell 版本？
1. 為什麼以系統管理員身分啟動提高權限的 PowerShell 至關重要？
1. 如何判斷目前的 PowerShell 執行原則？
1. Windows 用戶端電腦上的預設 PowerShell 執行原則可防止發生什麼情況？
1. 如何變更 PowerShell 執行原則？

## <a name="recommended-reading"></a>建議閱讀資料

若需深入瞭解本章所提到的主題，建議閱讀下列 PowerShell 說明主題。

- [about_Automatic_Variables][]
- [about_Hash_Tables][]
- [about_Execution_Policies][]

在下一章中，您將瞭解 PowerShell 中命令的可搜尋性。 包括如何更新 PowerShell，以便直接從 PowerShell 內查看這些說明主題，而不需要在網際網路上查看。

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Hash_Tables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[about_Execution_Policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[升級現有的 Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[安裝 PowerShell]: /powershell/scripting/install/installing-powershell
[啟動 Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
