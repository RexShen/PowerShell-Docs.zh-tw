---
title: 開始使用 PowerShell
description: 在哪裡可以找到 PowerShell，以及如何為新使用者啟動 PowerShell。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 0f72fb5baf5b829142b18ed774261e9b3b66291b
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438019"
---
# <a name="chapter-1---getting-started-with-powershell"></a><span data-ttu-id="0ec36-103">第 1 章 - PowerShell 使用者入門</span><span class="sxs-lookup"><span data-stu-id="0ec36-103">Chapter 1 - Getting Started with PowerShell</span></span>

<span data-ttu-id="0ec36-104">在會議和使用者群組會議上，我經常發現一些入門級新手使用 PowerShell 進行簡報。</span><span class="sxs-lookup"><span data-stu-id="0ec36-104">I often find that presenters at conferences and user group meetings already have PowerShell running when they start entry-level presentations.</span></span> <span data-ttu-id="0ec36-105">本書一開始會回答上述會議中未使用過 PowerShell 的與會者詢問的問題。</span><span class="sxs-lookup"><span data-stu-id="0ec36-105">This book begins by answering the questions I've heard attendees who haven't previously used PowerShell ask in those sessions.</span></span>

<span data-ttu-id="0ec36-106">具體而言，本章重點在於尋找和啟動 PowerShell，並解決新使用者在開始使用 PowerShell 時會遇到的難題。</span><span class="sxs-lookup"><span data-stu-id="0ec36-106">Specifically, this chapter focuses on finding and launching PowerShell, and solving some of the initial pain points that new users experience with PowerShell.</span></span> <span data-ttu-id="0ec36-107">請務必在您的 Windows 10 實驗室環境電腦上依照本章所示範例逐步操作。</span><span class="sxs-lookup"><span data-stu-id="0ec36-107">Be sure to follow along and walk through the examples shown in this chapter on your Windows 10 lab environment computer.</span></span>

## <a name="what-do-i-need-to-get-started-with-powershell"></a><span data-ttu-id="0ec36-108">開始使用 PowerShell 時需要什麼？</span><span class="sxs-lookup"><span data-stu-id="0ec36-108">What do I need to get started with PowerShell?</span></span>

<span data-ttu-id="0ec36-109">所有新式版本 Windows 作業系統均已隨附安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0ec36-109">All modern versions of Windows operating systems ship with PowerShell installed.</span></span> <span data-ttu-id="0ec36-110">如果您執行的版本低於 5.1，請務必安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="0ec36-110">If you're running a version older than 5.1, you should install the latest version.</span></span>

- <span data-ttu-id="0ec36-111">如需升級到 Windows PowerShell 5.1，請參閱[升級現有的 Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="0ec36-111">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][]</span></span>
- <span data-ttu-id="0ec36-112">如需安裝最新版的 PowerShell，請參閱[安裝 PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="0ec36-112">To install the latest version of PowerShell, see [Installing PowerShell][]</span></span>

## <a name="where-do-i-find-powershell"></a><span data-ttu-id="0ec36-113">在哪裡可以找到 PowerShell？</span><span class="sxs-lookup"><span data-stu-id="0ec36-113">Where do I find PowerShell?</span></span>

<span data-ttu-id="0ec36-114">在 Windows 10 上尋找 PowerShell 最簡單的方式，就是在搜尋列中輸入 **PowerShell** (如圖1-1 所示)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-114">The easiest way to find PowerShell on Windows 10 is to type **PowerShell** into the search bar as shown in Figure 1-1.</span></span>

![圖 1-1](media/figure1-1.png)

<span data-ttu-id="0ec36-116">請注意，圖 1-1 中顯示 PowerShell 的四個不同捷徑。</span><span class="sxs-lookup"><span data-stu-id="0ec36-116">Notice that four different shortcuts for PowerShell are shown in Figure 1-1.</span></span> <span data-ttu-id="0ec36-117">本書中用來示範的電腦是執行 64 位元版本的 Windows 10，因此如同捷徑上 (x86) 尾碼所示，有 64 位元版本和 32 位元版本的 PowerShell 主控台和 PowerShell ISE (整合式指令碼環境)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-117">The computer used for demonstration purposes in this book is running the 64-bit version of Windows 10 so there's a 64-bit version of the PowerShell console and the PowerShell ISE (Integrated Scripting Environment), and a 32-bit version of each one as denoted by the (x86) suffix on the shortcuts.</span></span> <span data-ttu-id="0ec36-118">如果您執行的是 32 位元版本的 Windows 10，則只會有兩個捷徑。</span><span class="sxs-lookup"><span data-stu-id="0ec36-118">If you happen to be running a 32-bit version of Windows 10, you'll only have two shortcuts.</span></span> <span data-ttu-id="0ec36-119">這些項目沒有 (x86) 尾碼，但為 32 位元版本。</span><span class="sxs-lookup"><span data-stu-id="0ec36-119">Those items don't have the (x86) suffix, but are 32-bit versions.</span></span> <span data-ttu-id="0ec36-120">如果您使用的是 64 位元的作業系統，建議您執行 64 位元版本的 PowerShell (除非有特定原因需要執行 32 位元版本)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-120">If you have a 64-bit operating system, my recommendation is to run the 64-bit version of PowerShell unless you have a specific reason for running the 32-bit version.</span></span>

<span data-ttu-id="0ec36-121">如需在其他版本的 Windows 上啟動 PowerShell 的資訊，請參閱[啟動 Windows PowerShell][]。</span><span class="sxs-lookup"><span data-stu-id="0ec36-121">For information about starting PowerShell on other versions of Windows, see [Starting Windows PowerShell][].</span></span>

## <a name="how-do-i-launch-powershell"></a><span data-ttu-id="0ec36-122">如何啟動 PowerShell？</span><span class="sxs-lookup"><span data-stu-id="0ec36-122">How do I launch PowerShell?</span></span>

<span data-ttu-id="0ec36-123">在支援的生產企業環境中，我使用三個不同的 Active Directory 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0ec36-123">In the production enterprise environments that I support, I use three different Active Directory user accounts.</span></span> <span data-ttu-id="0ec36-124">我已在本書使用的實驗室環境中鏡像這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="0ec36-124">I've mirrored those accounts in the lab environment used in this book.</span></span> <span data-ttu-id="0ec36-125">我以非網域或本機系統管理員的網域使用者身分登入 Windows 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="0ec36-125">I log into the Windows 10 computer as a domain user who is not a domain or local administrator.</span></span>

<span data-ttu-id="0ec36-126">我已透過點選「Windows PowerShell」捷徑，啟動 PowerShell 主控台 (如圖 1-1 所示)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-126">I've launched the PowerShell console by clicking on the "Windows PowerShell" shortcut as shown in Figure 1-1.</span></span>

![圖 1-4](media/figure1-4.png)

<span data-ttu-id="0ec36-128">請注意，PowerShell 主控台的標題列會顯示「Windows PowerShell」 (如圖 1-4 所示)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-128">Notice that the title bar of the PowerShell console says "Windows PowerShell" as shown in Figure 1-4.</span></span> <span data-ttu-id="0ec36-129">有些命令運作順利，但 PowerShell 無法參與使用者存取控制 (UAC)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-129">Some commands run fine, but PowerShell can't participate in User Access Control (UAC).</span></span> <span data-ttu-id="0ec36-130">這表示它無法針對需要系統管理員核准的工作提示提高權限。</span><span class="sxs-lookup"><span data-stu-id="0ec36-130">That means it's unable to prompt for elevation for tasks that require the approval of an administrator.</span></span>
<span data-ttu-id="0ec36-131">系統會產生下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0ec36-131">The following error message is generated:</span></span>

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

<span data-ttu-id="0ec36-132">此問題的解決方法是以本機系統管理員作為網域使用者的身分執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0ec36-132">The solution to this problem is to run PowerShell as a domain user who is a local administrator.</span></span>
<span data-ttu-id="0ec36-133">這是我第二個網域使用者帳戶的設定方式。</span><span class="sxs-lookup"><span data-stu-id="0ec36-133">This is how my second domain user account is configured.</span></span> <span data-ttu-id="0ec36-134">此帳戶使用權限最低的主體，因此不得為網域系統管理員，或是在網域中具有較高權限者。</span><span class="sxs-lookup"><span data-stu-id="0ec36-134">Using the principal of least privilege, this account should NOT be a domain administrator, or have any elevated privileges in the domain.</span></span>

<span data-ttu-id="0ec36-135">關閉 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0ec36-135">Close PowerShell.</span></span> <span data-ttu-id="0ec36-136">重新開機 PowerShell 主控台，但這次請在 [Windows PowerShell] 捷徑上按一下滑鼠右鍵，然後選取 [以系統管理員身分執行] (如圖 1-5 所示)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-136">Relaunch the PowerShell console, except this time right-click on the **Windows PowerShell** shortcut and select **Run as administrator** as shown in Figure 1-5.</span></span>

![圖 1-5](media/figure1-5.png)

<span data-ttu-id="0ec36-138">如果您是以一般使用者的身分登入 Windows，系統會提示您輸入認證。</span><span class="sxs-lookup"><span data-stu-id="0ec36-138">If you're logged into Windows as a normal user, you'll be prompted for credentials.</span></span> <span data-ttu-id="0ec36-139">我會輸入使用者帳戶的認證，其身分為網域使用者和本機系統管理員 (如圖 1-6 所示)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-139">I'll enter the credentials for my user account who is a domain user and local admin as shown in Figure 1-6.</span></span>

![圖 1-6](media/figure1-6.png)

<span data-ttu-id="0ec36-141">以系統管理員身分重新啟動 PowerShell 後，標題列應該會顯示「系統管理員：Windows PowerShell」(如圖 1-7 所示)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-141">Once PowerShell is relaunched as an administrator, the title bar should say "Administrator: Windows PowerShell" as shown in Figure 1-7.</span></span>

![圖 1-7](media/figure1-7.png)

<span data-ttu-id="0ec36-143">現在 PowerShell 是以本機系統管理員提升權限的身分執行，因此，在本機電腦上執行命令而通常需要提示提高權限時，不會再出現 UAC 的問題。</span><span class="sxs-lookup"><span data-stu-id="0ec36-143">Now that PowerShell is being run elevated as a local administrator, UAC will no longer be a problem when a command is run on the local computer that would normally require a prompt for elevation.</span></span> <span data-ttu-id="0ec36-144">請記住，從這個已提升權限的 PowerShell 主控台執行個體執行的任何命令，也會以提高權限執行。</span><span class="sxs-lookup"><span data-stu-id="0ec36-144">Keep in mind though that any command run from this elevated instance of the PowerShell console, also runs elevated.</span></span>

<span data-ttu-id="0ec36-145">為了簡化尋找 PowerShell 並以系統管理員的身分啟動，建議您將 PowerShell 釘選到工作列，並將其設定為每次執行時自動以管理員身分啟動。</span><span class="sxs-lookup"><span data-stu-id="0ec36-145">To simplify finding PowerShell and launching it as an administrator, I recommend pinning it to the taskbar and setting it to automatically launch as an admin each time it's run.</span></span>

<span data-ttu-id="0ec36-146">再次搜尋 PowerShell，但這次請在其上按一下滑鼠右鍵，然後選取 [釘選到工作列] (如圖 1-8 所示)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-146">Search for PowerShell again, except this time right-click on it and select "Pin to taskbar" as shown in Figure 1-8.</span></span>

![圖 1-8](media/figure1-8.png)

<span data-ttu-id="0ec36-148">在現在已釘選到工作列的 PowerShell 快捷方式上按一下滑鼠右鍵，然後選取 [屬性]，如圖1-9 所示。</span><span class="sxs-lookup"><span data-stu-id="0ec36-148">Right-click on the PowerShell shortcut that's now pinned to the taskbar and select properties as shown in Figure 1-9.</span></span>

![圖 1-9](media/figure1-9.png)

<span data-ttu-id="0ec36-150">按一下圖 1-10 中 #1 所表示的 [進階]，然後勾選圖 1-10 中 #2 所表示的 [以系統管理員身分執行] 核取方塊，然後按兩下 [確定] 以接受變更並退出兩個對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0ec36-150">Click on "Advanced" as denoted by #1 in Figure 1-10, then check the "Run as administrator" checkbox as denoted by #2 in Figure 1-10, and then click OK twice to accept the changes and exit out of both dialog boxes.</span></span>

![圖 1-10](media/figure1-10.png)

<span data-ttu-id="0ec36-152">您永遠無需再擔心如何尋找 PowerShell，或 PowerShell 是否以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="0ec36-152">You'll never have to worry about finding PowerShell or whether or not it's running as an administrator again.</span></span>

<span data-ttu-id="0ec36-153">以系統管理員身分執行已提高權限的 PowerShell 以避免發生 UAC 問題，這個作法只會影響針對本機電腦執行的命令。</span><span class="sxs-lookup"><span data-stu-id="0ec36-153">Running PowerShell elevated as an administrator to prevent having problems with UAC only impacts commands that are run against the local computer.</span></span> <span data-ttu-id="0ec36-154">而不會影響以遠端電腦為目標的命令。</span><span class="sxs-lookup"><span data-stu-id="0ec36-154">It has no effect on commands that target remote computers.</span></span>

## <a name="what-version-of-powershell-am-i-running"></a><span data-ttu-id="0ec36-155">我正在執行哪個版本的 PowerShell？</span><span class="sxs-lookup"><span data-stu-id="0ec36-155">What version of PowerShell am I running?</span></span>

<span data-ttu-id="0ec36-156">PowerShell 中有數個自動變數可儲存狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="0ec36-156">There are a number of automatic variables in PowerShell that store state information.</span></span> <span data-ttu-id="0ec36-157">其中一個變數是 `$PSVersionTable`，其中包含可用於顯示相關 PowerShell 版本資訊的雜湊表：</span><span class="sxs-lookup"><span data-stu-id="0ec36-157">One of these variables is `$PSVersionTable`, which contains a hashtable that can be used to display the relevant PowerShell version information:</span></span>

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

<span data-ttu-id="0ec36-158">新版 Windows PowerShell 以作為 Windows Management Framework (WMF) 的一部分來發佈。</span><span class="sxs-lookup"><span data-stu-id="0ec36-158">Newer versions of Windows PowerShell are distributed as part of the Windows Management Framework (WMF).</span></span> <span data-ttu-id="0ec36-159">視 WMF 版本決定所需要的特定版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="0ec36-159">A specific version of the .NET Framework is required depending on the WMF version.</span></span> <span data-ttu-id="0ec36-160">如需升級到 Windows PowerShell 5.1，請參閱[升級現有的 Windows PowerShell][]。</span><span class="sxs-lookup"><span data-stu-id="0ec36-160">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][].</span></span>

## <a name="execution-policy"></a><span data-ttu-id="0ec36-161">執行原則</span><span class="sxs-lookup"><span data-stu-id="0ec36-161">Execution Policy</span></span>

<span data-ttu-id="0ec36-162">相對於普遍的看法，PowerShell 中的執行原則並非安全性界限。</span><span class="sxs-lookup"><span data-stu-id="0ec36-162">Contrary to popular belief, the execution policy in PowerShell is not a security boundary.</span></span> <span data-ttu-id="0ec36-163">其設計目的是要防止使用者在不知情的情況之下執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="0ec36-163">It's designed to prevent a user from unknowingly running a script.</span></span> <span data-ttu-id="0ec36-164">已確定的使用者可以輕鬆略過 PowerShell 中的執行原則。</span><span class="sxs-lookup"><span data-stu-id="0ec36-164">A determined user can easily bypass the execution policy in PowerShell.</span></span> <span data-ttu-id="0ec36-165">表 1-2 顯示目前 Windows 作業系統的預設執行原則。</span><span class="sxs-lookup"><span data-stu-id="0ec36-165">Table 1-2 shows the default execution policy for current Windows operating systems.</span></span>

| <span data-ttu-id="0ec36-166">Windows 作業系統版本</span><span class="sxs-lookup"><span data-stu-id="0ec36-166">Windows Operating System Version</span></span> | <span data-ttu-id="0ec36-167">預設執行原則</span><span class="sxs-lookup"><span data-stu-id="0ec36-167">Default Execution Policy</span></span> |
| -------------------------------- | ------------------------ |
| <span data-ttu-id="0ec36-168">Server 2019</span><span class="sxs-lookup"><span data-stu-id="0ec36-168">Server 2019</span></span>                      | <span data-ttu-id="0ec36-169">遠端簽署</span><span class="sxs-lookup"><span data-stu-id="0ec36-169">Remote Signed</span></span>            |
| <span data-ttu-id="0ec36-170">Server 2016</span><span class="sxs-lookup"><span data-stu-id="0ec36-170">Server 2016</span></span>                      | <span data-ttu-id="0ec36-171">遠端簽署</span><span class="sxs-lookup"><span data-stu-id="0ec36-171">Remote Signed</span></span>            |
| <span data-ttu-id="0ec36-172">Windows 10</span><span class="sxs-lookup"><span data-stu-id="0ec36-172">Windows 10</span></span>                       | <span data-ttu-id="0ec36-173">Restricted</span><span class="sxs-lookup"><span data-stu-id="0ec36-173">Restricted</span></span>               |

<span data-ttu-id="0ec36-174">無論執行原則設定為何，PowerShell 命令都可以互動方式執行。</span><span class="sxs-lookup"><span data-stu-id="0ec36-174">Regardless of the execution policy setting, any PowerShell command can be run interactively.</span></span> <span data-ttu-id="0ec36-175">執行原則只會影響在指令碼中執行的命令。</span><span class="sxs-lookup"><span data-stu-id="0ec36-175">The execution policy only affects commands running in a script.</span></span> <span data-ttu-id="0ec36-176">`Get-ExecutionPolicy` Cmdlet 是用來判斷目前的執行原則設定，而 `Set-ExecutionPolicy` Cmdlet 則是用來變更執行原則。</span><span class="sxs-lookup"><span data-stu-id="0ec36-176">The `Get-ExecutionPolicy` cmdlet is used to determine what the current execution policy setting is and the `Set-ExecutionPolicy` cmdlet is used to change the execution policy.</span></span> <span data-ttu-id="0ec36-177">建議使用 **RemoteSigned** 原則，此原則會要求下載的指令碼必須由信任的發行者簽署才能執行。</span><span class="sxs-lookup"><span data-stu-id="0ec36-177">My recommendation is to use the **RemoteSigned** policy, which requires downloaded scripts to be signed by a trusted publisher in order to be run.</span></span>

<span data-ttu-id="0ec36-178">檢查目前的執行原則：</span><span class="sxs-lookup"><span data-stu-id="0ec36-178">Check the current execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

<span data-ttu-id="0ec36-179">當執行原則設定為 **Restricted** 時，就無法執行 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="0ec36-179">PowerShell scripts can't be run at all when the execution policy is set to **Restricted**.</span></span> <span data-ttu-id="0ec36-180">這是所有 Windows 用戶端作業系統上的預設設定。</span><span class="sxs-lookup"><span data-stu-id="0ec36-180">This is the default setting on all Windows client operating systems.</span></span> <span data-ttu-id="0ec36-181">若要示範此問題，請將下列程式碼儲存為名為 `Stop-TimeService.ps1`的 `.ps1` 檔案。</span><span class="sxs-lookup"><span data-stu-id="0ec36-181">To demonstrate the problem, save the following code as a `.ps1` file named `Stop-TimeService.ps1`.</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

<span data-ttu-id="0ec36-182">只要以系統管理員的身分執行提高權限的 PowerShell，該命令就會以互動方式執行而不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0ec36-182">That command runs interactively without error as long as PowerShell is run elevated as an administrator.</span></span> <span data-ttu-id="0ec36-183">但是如果儲存為指令碼檔案並嘗試執行指令碼時，就會產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="0ec36-183">But as soon as it's saved as a script file and you try to execute the script, it generates an error:</span></span>

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

<span data-ttu-id="0ec36-184">請注意，上一組結果所顯示的錯誤會明確告訴您問題為何 (此系統上已停用執行指令碼)。</span><span class="sxs-lookup"><span data-stu-id="0ec36-184">Notice that the error shown in the previous set of results tells you exactly what the problem is (running scripts is disabled on this system).</span></span> <span data-ttu-id="0ec36-185">當您在 PowerShell 中執行命令並產生錯誤訊息時，請務必詳閱錯誤訊息，而不只是重新執行命令，一昧希望這樣就能夠順利執行。</span><span class="sxs-lookup"><span data-stu-id="0ec36-185">When you run a command in PowerShell that generates an error message, be sure to read the error message instead of just rerunning the command and hoping that it runs successfully.</span></span>

<span data-ttu-id="0ec36-186">將 PowerShell 執行原則變更為遠端簽署。</span><span class="sxs-lookup"><span data-stu-id="0ec36-186">Change the PowerShell execution policy to remote signed.</span></span>

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

<span data-ttu-id="0ec36-187">請務必閱讀變更執行原則時所顯示的警告。</span><span class="sxs-lookup"><span data-stu-id="0ec36-187">Be sure to read the warning that's displayed when changing the execution policy.</span></span> <span data-ttu-id="0ec36-188">另外，建議您參閱 [about_Execution_Policies][] 說明主題，以確保您瞭解變更執行原則對安全性的影響。</span><span class="sxs-lookup"><span data-stu-id="0ec36-188">I also recommend taking a look at the [about_Execution_Policies][] help topic to make sure you understand the security implications of changing the execution policy.</span></span>

<span data-ttu-id="0ec36-189">現已將執行原則設定為 **RemoteSigned**，`Stop-TimeService.ps1` 指令碼會正常執行而不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0ec36-189">Now that the execution policy has been set to **RemoteSigned**, the `Stop-TimeService.ps1` script runs error free.</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

<span data-ttu-id="0ec36-190">請務必先啟動 Windows 時間服務，再繼續進行，否則可能會遇到未預期的問題。</span><span class="sxs-lookup"><span data-stu-id="0ec36-190">Be sure to start your Windows Time service before continuing otherwise you may run into unforeseen problems.</span></span>

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a><span data-ttu-id="0ec36-191">摘要</span><span class="sxs-lookup"><span data-stu-id="0ec36-191">Summary</span></span>

<span data-ttu-id="0ec36-192">在本章中，您已瞭解如何尋找和啟動 PowerShell，以及如何建立以系統管理員身分啟動 PowerShell 的捷徑。</span><span class="sxs-lookup"><span data-stu-id="0ec36-192">In this chapter, you've learned how to find and launch PowerShell, and how to create a shortcut that launches PowerShell as an administrator.</span></span> <span data-ttu-id="0ec36-193">您也已瞭解預設執行原則以及如何變更。</span><span class="sxs-lookup"><span data-stu-id="0ec36-193">You've also learned about the default execution policy and how to change it.</span></span>

## <a name="review"></a><span data-ttu-id="0ec36-194">檢閱</span><span class="sxs-lookup"><span data-stu-id="0ec36-194">Review</span></span>

1. <span data-ttu-id="0ec36-195">如何判斷電腦正在執行的 PowerShell 版本？</span><span class="sxs-lookup"><span data-stu-id="0ec36-195">How do you determine what PowerShell version a computer is running?</span></span>
1. <span data-ttu-id="0ec36-196">為什麼以系統管理員身分啟動提高權限的 PowerShell 至關重要？</span><span class="sxs-lookup"><span data-stu-id="0ec36-196">Why is it important to launch PowerShell elevated as an administrator?</span></span>
1. <span data-ttu-id="0ec36-197">如何判斷目前的 PowerShell 執行原則？</span><span class="sxs-lookup"><span data-stu-id="0ec36-197">How do you determine the current PowerShell execution policy?</span></span>
1. <span data-ttu-id="0ec36-198">Windows 用戶端電腦上的預設 PowerShell 執行原則可防止發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="0ec36-198">What does the default PowerShell execution policy on Windows client computers prevent from occurring?</span></span>
1. <span data-ttu-id="0ec36-199">如何變更 PowerShell 執行原則？</span><span class="sxs-lookup"><span data-stu-id="0ec36-199">How do you change the PowerShell execution policy?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="0ec36-200">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="0ec36-200">Recommended Reading</span></span>

<span data-ttu-id="0ec36-201">若需深入瞭解本章所提到的主題，建議閱讀下列 PowerShell 說明主題。</span><span class="sxs-lookup"><span data-stu-id="0ec36-201">For those who want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="0ec36-202">[about_Automatic_Variables][]</span><span class="sxs-lookup"><span data-stu-id="0ec36-202">[about_Automatic_Variables][]</span></span>
- <span data-ttu-id="0ec36-203">[about_Execution_Policies][]</span><span class="sxs-lookup"><span data-stu-id="0ec36-203">[about_Execution_Policies][]</span></span>

<span data-ttu-id="0ec36-204">在下一章中，您將瞭解 PowerShell 中命令的可搜尋性。</span><span class="sxs-lookup"><span data-stu-id="0ec36-204">In the next chapter, you'll learn about the discoverability of commands in PowerShell.</span></span> <span data-ttu-id="0ec36-205">包括如何更新 PowerShell，以便直接從 PowerShell 內查看這些說明主題，而不需要在網際網路上查看。</span><span class="sxs-lookup"><span data-stu-id="0ec36-205">One of the things that will be covered is how to update PowerShell so those help topics can be viewed right from within PowerShell instead of having to view them on the internet.</span></span>

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Execution_Policies]: /powershell//powershell/module/microsoft.powershell.core/about/about_execution_policies
[升級現有的 Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Upgrading existing Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[安裝 PowerShell]: /powershell/scripting/install/installing-powershell
[Installing PowerShell]: /powershell/scripting/install/installing-powershell
[啟動 Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
[Starting Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
