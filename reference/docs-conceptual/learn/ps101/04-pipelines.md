---
title: 單行式與管線
description: PowerShell 單行程式碼是包含多個命令的一個連續管線，用來完成單一工作。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fd45e5e5dc408754ebac015757ef4241428978
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633340"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a><span data-ttu-id="3e1d1-103">第 4 章 - 單行程式碼與管線</span><span class="sxs-lookup"><span data-stu-id="3e1d1-103">Chapter 4 - One-liners and the pipeline</span></span>

<span data-ttu-id="3e1d1-104">當我初次開始學習 PowerShell 時，如果我無法使用 PowerShell 單行程式碼來完成某個工作，我就會回到 GUI。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-104">When I first started learning PowerShell, if I couldn't accomplish a task with a PowerShell one-liner, I went back to the GUI.</span></span> <span data-ttu-id="3e1d1-105">一段時間後，我加強了我撰寫指令碼、函式和模組的技能。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-105">Over time, I built my skills up to writing scripts, functions, and modules.</span></span> <span data-ttu-id="3e1d1-106">不要讓您自己被可能會在網際網路上看到的一些更進階範例擊敗了。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-106">Don't allow yourself to become overwhelmed by some of the more advanced examples you may see on the internet.</span></span> <span data-ttu-id="3e1d1-107">沒有人是使用 PowerShell 的自然專家。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-107">No one is a natural expert with PowerShell.</span></span> <span data-ttu-id="3e1d1-108">我們都曾經是新手。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-108">We were all beginners at one time.</span></span>

<span data-ttu-id="3e1d1-109">我有個建議可以給仍在使用 GUI 進行管理的您：在系統管理工作站上安裝管理工具，並從遠端系統管理您的伺服器。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-109">I have a bit of advice to offer those of you who are still using the GUI for administration: install the management tools on your admin workstation and manage your servers remotely.</span></span> <span data-ttu-id="3e1d1-110">這麼一來，伺服器是否執行作業系統的 GUI 或 Server Core 安裝並不重要。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-110">This way it won't matter if the server is running a GUI or Server Core installation of the operating system.</span></span>
<span data-ttu-id="3e1d1-111">它將協助您為使用 PowerShell 從遠端管理伺服器進行準備。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-111">It's going to help prepare you for managing servers remotely with PowerShell.</span></span>

<span data-ttu-id="3e1d1-112">如同前幾章，請務必在您的 Windows 10 實驗室環境電腦上按照步驟執行。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-112">As with previous chapters, be sure to follow along on your Windows 10 lab environment computer.</span></span>

## <a name="one-liners"></a><span data-ttu-id="3e1d1-113">單行程式碼</span><span class="sxs-lookup"><span data-stu-id="3e1d1-113">One-Liners</span></span>

<span data-ttu-id="3e1d1-114">PowerShell 單行程式碼是一個連續管線，但不一定是在一個實體行上的命令。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-114">A PowerShell one-liner is one continuous pipeline and not necessarily a command that’s on one physical line.</span></span> <span data-ttu-id="3e1d1-115">並非在單一實體行上的所有命令都是單行程式碼。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-115">Not all commands that are on one physical line are one-liners.</span></span>

<span data-ttu-id="3e1d1-116">即使下列命令在多個實體行上，但它是 PowerShell 單行程式碼，因為它是一個連續的管線。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-116">Even though the following command is on multiple physical lines, it's a PowerShell one-liner because it's one continuous pipeline.</span></span> <span data-ttu-id="3e1d1-117">我可以在一個實體行上撰寫這些命令，但是我選擇在管線符號處換行。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-117">It could be written on one physical line, but I've chosen to line break at the pipe symbol.</span></span> <span data-ttu-id="3e1d1-118">管線符號是在 PowerShell 中所允許自然換行符號的其中一個字元。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-118">The pipe symbol is one of the characters where a natural line break is allowed in PowerShell.</span></span>

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

<span data-ttu-id="3e1d1-119">自然換行符號可能發生在常用的字元，包括逗號 (`,`) 和左括弧 (`[`)、大括弧 (`{`) 和括弧 (`(`)。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-119">Natural line breaks can occur at commonly used characters including comma (`,`) and opening brackets (`[`), braces (`{`), and parenthesis (`(`).</span></span> <span data-ttu-id="3e1d1-120">其他不常用的項目包括分號 (`;`)、等號 (`=`)，以及開頭的左單引號和雙引號 (`'`、`"`)。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-120">Others that aren't so common include the semicolon (`;`), equals sign (`=`), and both opening single and double quotes (`'`,`"`).</span></span>

<span data-ttu-id="3e1d1-121">使用反引號 (`` ` ``) 或抑音符號字元作為行接續字元，是具爭議的主題。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-121">Using the backtick (`` ` ``) or grave accent character as a line continuation character is a controversial topic.</span></span> <span data-ttu-id="3e1d1-122">我的建議是儘量試著避免這種情況。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-122">My recommendation is to try to avoid it if at all possible.</span></span> <span data-ttu-id="3e1d1-123">我經常看到在自然換行符號字元之後緊接著使用反引號撰寫的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-123">I often see PowerShell commands written using a backtick immediately after a natural line break character.</span></span>
<span data-ttu-id="3e1d1-124">沒有任何原因應該在那裡使用該符號。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-124">There's no reason for it to be there.</span></span>

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="3e1d1-125">以上兩個範例中所顯示的命令可在 PowerShell 主控台中正常執行。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-125">The commands shown in the previous two examples work fine in the PowerShell console.</span></span> <span data-ttu-id="3e1d1-126">但是，如果您嘗試在 PowerShell ISE 的主控台窗格中執行它們，就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-126">But if you try to run them in the console pane of the PowerShell ISE, they'll generate an error.</span></span> <span data-ttu-id="3e1d1-127">PowerShell ISE 的主控台窗格不會如同 PowerShell 主控台般，等候在下一行輸入命令的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-127">The console pane of the PowerShell ISE doesn't wait for the rest of the command to be entered on the next line like the PowerShell console does.</span></span> <span data-ttu-id="3e1d1-128">若要在 PowerShell ISE 的主控台窗格中避免此問題，請使用 <kbd>Shift</kbd>+<kbd>Enter</kbd>，而不只是在另一行繼續命令時按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-128">To avoid this problem in the console pane of the PowerShell ISE, use <kbd>Shift</kbd>+<kbd>Enter</kbd> instead of just pressing <kbd>Enter</kbd> when continuing a command on another line.</span></span>

<span data-ttu-id="3e1d1-129">下一個範例不是 PowerShell 單行程式碼，因為它不是連續管線。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-129">This next example isn't a PowerShell one-liner because it's not one continuous pipeline.</span></span> <span data-ttu-id="3e1d1-130">這是在一行上的兩個不同命令，以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-130">It's two separate commands on one line, separated by a semicolon.</span></span>

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="3e1d1-131">許多程式設計和指令碼語言要求在每一行的結尾都需要分號。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-131">Many programming and scripting languages require a semicolon at the end of each line.</span></span> <span data-ttu-id="3e1d1-132">雖然可以在 PowerShell 中使用該方式，但不建議您這樣做，因為這是不必要的。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-132">While they can be used that way in PowerShell, it's not recommended because they're not needed.</span></span>

## <a name="filtering-left"></a><span data-ttu-id="3e1d1-133">篩選左側</span><span class="sxs-lookup"><span data-stu-id="3e1d1-133">Filtering Left</span></span>

<span data-ttu-id="3e1d1-134">本章所示的命令結果已篩選至子集。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-134">The results of the commands shown in this chapter have been filtered down to a subset.</span></span> <span data-ttu-id="3e1d1-135">例如，`Get-Service` 與 **Name** 參數搭配使用，以篩選只傳回至 Windows 時間服務的服務清單。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-135">For example, `Get-Service` was used with the **Name** parameter to filter the list of services that were returned to only the Windows Time service.</span></span>

<span data-ttu-id="3e1d1-136">在管線中，您一定會想要儘快將結果篩選到您要尋找的內容。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-136">In the pipeline, you always want to filter the results down to what you're looking for as early as possible.</span></span> <span data-ttu-id="3e1d1-137">這是在第一個 (或最左邊的) 命令上使用參數來完成。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-137">This is accomplished using parameters on the first command or, the one to the far left.</span></span>
<span data-ttu-id="3e1d1-138">這有時稱為_篩選左側_。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-138">This is sometimes called _filtering left_.</span></span>

<span data-ttu-id="3e1d1-139">下列範例使用 `Get-Service` 的 **Name** 參數，立即將結果篩選為僅 Windows 時間服務。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-139">The following example uses the **Name** parameter of `Get-Service` to immediately filter the results to the Windows Time service only.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="3e1d1-140">要看到將命令以管線傳送至 `Where-Object` 以執行篩選的範例並不常見。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-140">It's not uncommon to see examples where the command is piped to `Where-Object` to perform the filtering.</span></span>

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

<span data-ttu-id="3e1d1-141">第一個範例會在來源篩選，並僅傳回 Windows 時間服務的結果。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-141">The first example filters at the source and only returns the results for the Windows Time service.</span></span>
<span data-ttu-id="3e1d1-142">第二個範例會傳回所有服務，然後將它們傳送至另一個命令，以執行篩選。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-142">The second example returns all the services then pipes them to another command to perform the filtering.</span></span> <span data-ttu-id="3e1d1-143">雖然此動作在此範例中看起來問題不重要，但請想像一下，如果是要查詢 Active Directory 使用者的清單。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-143">While this may not seem like a big deal in this example, imagine if you were querying a list of Active Directory users.</span></span> <span data-ttu-id="3e1d1-144">您是否真的想要從 Active Directory 傳回數千個使用者帳戶的資訊，只是為了將該資訊以管線傳送至可將它們篩選成較小子集的另一個命令？</span><span class="sxs-lookup"><span data-stu-id="3e1d1-144">Do you really want to return the information for many thousands of user accounts from Active Directory only to pipe them to another command that filters them down to a tiny subset?</span></span> <span data-ttu-id="3e1d1-145">我的建議是，即使看起來似乎不重要，也一律進行篩選左側。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-145">My recommendation is to always filter left even when it doesn't seem to matter.</span></span> <span data-ttu-id="3e1d1-146">這麼做的話，當自動篩選左側真的很重要的時候，您就會習慣它了。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-146">You'll be so use to it that you'll automatically filter left when it really does matter.</span></span>

<span data-ttu-id="3e1d1-147">曾經有人告訴我，指定命令的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-147">I once had someone tell me that the order you specify the commands in doesn't matter.</span></span> <span data-ttu-id="3e1d1-148">那絕不是事實。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-148">That couldn't be further from the truth.</span></span> <span data-ttu-id="3e1d1-149">執行篩選時，指定命令的順序確實很重要。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-149">The order that the commands are specified in does indeed matter when performing filtering.</span></span> <span data-ttu-id="3e1d1-150">例如，假設您使用 `Select-Object` 來僅選取幾個屬性，以及使用 `Where-Object` 來篩選不在選取範圍中的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-150">For example, consider the scenario where you are using `Select-Object` to select only a few properties and `Where-Object` to filter on properties that won't be in the selection.</span></span> <span data-ttu-id="3e1d1-151">在該案例中，必須先進行篩選，否則當嘗試執行篩選時，屬性將不會存在於管線中。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-151">In that scenario, the filtering must occur first, otherwise the property won't exist in the pipeline when try to perform the filtering.</span></span>

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

<span data-ttu-id="3e1d1-152">上一個範例中的命令不會傳回任何結果，因為當 `Select-Object` 的結果以管線傳送至 `Where-Object`時，**CanStopAndContinue** 屬性不存在。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-152">The command in the previous example doesn't return any results because the **CanStopAndContinue** property doesn't exist when the results of `Select-Object` are piped to `Where-Object`.</span></span> <span data-ttu-id="3e1d1-153">該特定屬性未被「選取」。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-153">That particular property wasn't "selected".</span></span> <span data-ttu-id="3e1d1-154">基本上，它已被篩選掉。反轉 `Select-Object` 和 `Where-Object` 的順序會產生所需的結果。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-154">In essence, it was filtered out. Reversing the order of `Select-Object` and `Where-Object` produces the desired results.</span></span>

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a><span data-ttu-id="3e1d1-155">管線</span><span class="sxs-lookup"><span data-stu-id="3e1d1-155">The Pipeline</span></span>

<span data-ttu-id="3e1d1-156">正如您目前在本書中所看到的許多範例，許多時候一個命令的輸出可以作為另一個命令的輸入。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-156">As you've seen in many of the examples shown so far throughout this book, many times the output of one command can be used as input for another command.</span></span> <span data-ttu-id="3e1d1-157">在第 3 章中，`Get-Member` 是用來判斷命令所產生的物件類型。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-157">In Chapter 3, `Get-Member` was used to determine what type of object a command produces.</span></span> <span data-ttu-id="3e1d1-158">第 3 章也示範如何使用 `Get-Command` 的 **ParameterType** 參數來判斷接受該類型輸入的是哪些命令，但不一定是透過管線輸入。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-158">Chapter 3 also showed using the **ParameterType** parameter of `Get-Command` to determine what commands accepted that type of input, although not necessarily by pipeline input.</span></span>

<span data-ttu-id="3e1d1-159">視命令說明的詳盡程度而定，可能會包含 **INPUTS** 和 **OUTPUTS** 區段。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-159">Depending on how thorough a commands help is, it may include an **INPUTS** and **OUTPUTS** section.</span></span>

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

<span data-ttu-id="3e1d1-160">在先前的結果中只顯示說明的相關區段。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-160">Only the relevant section of the help is shown in the previous results.</span></span> <span data-ttu-id="3e1d1-161">如您所見，**INPUTS** 區段指出您可以將 **ServiceController** 或 **String** 物件以管線傳送至 `Stop-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-161">As you can see, the **INPUTS** section states that a **ServiceController** or a **String** object can be piped to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="3e1d1-162">它不會告訴您接受該類型輸入的是哪些參數。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-162">It doesn't tell you which parameters accept that type of input.</span></span> <span data-ttu-id="3e1d1-163">用來判斷該資訊最簡單的方法之一，就是查看 `Stop-Service` Cmdlet 的完整版本說明中的不同參數。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-163">One of the easiest ways to determine that information is to look through the different parameters in the full version of the help for the `Stop-Service` cmdlet.</span></span>

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

<span data-ttu-id="3e1d1-164">重申，我只會在先前的結果集中顯示說明的相關部分。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-164">Once again, I've only shown the relevant portion of the help in the previous set of results.</span></span> <span data-ttu-id="3e1d1-165">請注意，**DisplayName** 參數不會接受管線輸入，**InputObject** 參數會接受管線輸入 **by value** 作為 **ServiceController** 物件，而 **Name** 參數會接受管線輸入 **by value** 作為 **string** 物件。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-165">Notice that the **DisplayName** parameter doesn't accept pipeline input, the **InputObject** parameter accepts pipeline input **by value** for **ServiceController** objects, and the **Name** parameter accepts pipeline input **by value** for **string** objects.</span></span> <span data-ttu-id="3e1d1-166">它也會接受管線輸入 **by property name**。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-166">It also accepts pipeline input **by property name**.</span></span>

<span data-ttu-id="3e1d1-167">當參數同時接受 by property name 和 by value 的管線輸入時，它一律會先嘗試 **by value**。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-167">When a parameter accepts pipeline input by both property name and by value, it always tries **by value** first.</span></span> <span data-ttu-id="3e1d1-168">如果 **by value** 失敗，則會嘗試 **by property name**。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-168">If **by value** fails, then it tries **by property name**.</span></span> <span data-ttu-id="3e1d1-169">**by value** 有點誤導。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-169">**By value** is a little misleading.</span></span> <span data-ttu-id="3e1d1-170">我偏好稱它為 **by type**。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-170">I prefer to call it **by type**.</span></span> <span data-ttu-id="3e1d1-171">這表示如果您將產生 **ServiceController** 物件類型之命令的結果傳送至 `Stop-Service`，它會將該輸入的繫結以管線傳送至 **InputObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-171">This means if you pipe the results of a command that produces a **ServiceController** object type to `Stop-Service`, it binds that input to the **InputObject** parameter.</span></span> <span data-ttu-id="3e1d1-172">但是，如果您將產生 **String** 輸出命令的結果傳送至 `Stop-Service`，它會將它繫結至 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-172">But if you pipe the results of a command that produces **String** output to `Stop-Service`, it binds it to the **Name** parameter.</span></span> <span data-ttu-id="3e1d1-173">如果您將不會產生 **ServiceController** 或 **String** 物件的命令結果以管線傳送至 `Stop-Service`，但它確實產生包含名為 **Name** 屬性的輸出，則會將 **Name** 屬性從輸出繫結至 `Stop-Service` 的 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-173">If you pipe the results of a command that doesn't produce a **ServiceController** or **String** object to `Stop-Service`, but it does produce output containing a property called **Name**, then it binds the **Name** property from the output to the **Name** parameter of `Stop-Service`.</span></span>

<span data-ttu-id="3e1d1-174">判斷 `Get-Service` 命令所產生的輸出類型。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-174">Determine what type of output the `Get-Service` command produces.</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

<span data-ttu-id="3e1d1-175">`Get-Service` 會產生 ServiceController 物件類型。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-175">`Get-Service` produces a ServiceController object type.</span></span>

<span data-ttu-id="3e1d1-176">如先前在說明中所見，`Stop-Service` 的 **InputObject** 參數會透過管線 **by value** (by type) 接受 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-176">As you previously saw in the help, the **InputObject** parameter of `Stop-Service` accepts **ServiceController** objects via the pipeline **by value** (by type).</span></span> <span data-ttu-id="3e1d1-177">這表示當 `Get-Service` Cmdlet 的結果透過管線傳送到 `Stop-Service` 時，它們會繫結至 `Stop-Service` 的 **InputObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-177">This means that when the results of the `Get-Service` cmdlet are piped to `Stop-Service`, they bind to the **InputObject** parameter of `Stop-Service`.</span></span>

```powershell
Get-Service -Name w32time | Stop-Service
```

<span data-ttu-id="3e1d1-178">現在嘗試字串輸入。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-178">Now to try string input.</span></span> <span data-ttu-id="3e1d1-179">將 `w32time` 以管線傳送至 `Get-Member` 只是為了確認它是字串。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-179">Pipe `w32time` to `Get-Member` just to confirm that it's a string.</span></span>

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

<span data-ttu-id="3e1d1-180">如先前在說明中所顯示，將字串以管線傳送至 `Stop-Service`，會將它 **by value** 繫結至 `Stop-Service` 的 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-180">As previously shown in the help, piping a string to `Stop-Service` binds it **by value** to the **Name** parameter of `Stop-Service`.</span></span> <span data-ttu-id="3e1d1-181">藉由將 `w32time` 以管線傳送至 `Stop-Service` 來測試此行為。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-181">Test this by piping `w32time` to `Stop-Service`.</span></span>

```powershell
'w32time' | Stop-Service
```

<span data-ttu-id="3e1d1-182">請注意，在上一個範例中，我使用了單引號來括住字串 `w32time`。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-182">Notice that in the previous example, I used single quotes around the string `w32time`.</span></span> <span data-ttu-id="3e1d1-183">在 PowerShell 中，除非加上引號的字串內容包含需要展開為其實際值的變數，否則您應該一律使用單引號，而不是雙引號。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-183">In PowerShell, you should always use single quotes instead of double quotes unless the contents of the quoted string contains a variable that needs to be expanded to its actual value.</span></span> <span data-ttu-id="3e1d1-184">藉由使用單引號，PowerShell 就不需要剖析引號內包含的內容，因此您的程式碼執行速度會更快。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-184">By using single quotes, PowerShell doesn't have to parse the contents contained within the quotes so your code runs a little faster.</span></span>

<span data-ttu-id="3e1d1-185">建立自訂物件，以依據屬性名稱，針對 `Stop-Service` 的 **Name** 參數來測試管線輸入。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-185">Create a custom object to test pipeline input by property name for the **Name** parameter of `Stop-Service`.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
 Name = 'w32time'
 }
```

<span data-ttu-id="3e1d1-186">**CustomObject** 變數的內容是 **PSCustomObject** 物件類型，而其包含名為 **Name** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-186">The contents of the **CustomObject** variable is a **PSCustomObject** object type and it contains a property named **Name**.</span></span>

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

<span data-ttu-id="3e1d1-187">如果您要以引號括住 `$CustomObject` 變數，您會想要使用雙引號。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-187">If you were to surround the `$CustomObject` variable with quotes, you want to use double quotes.</span></span>
<span data-ttu-id="3e1d1-188">否則，使用單引號，會將常值字串 `$CustomObject` (而非變數所包含的值) 以管線傳送至 `Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-188">Otherwise, using single quotes, the literal string `$CustomObject` is piped to `Get-Member` instead of the value contained by the variable.</span></span>

<span data-ttu-id="3e1d1-189">雖然將 `$CustomObject` 的內容以管線傳送至 `Stop-Service` Cmdlet 會繫結至 **Name** 參數，但這次它會 **by property name** 繫結，而不是 **by value**，因為 `$CustomObject` 的內容是具有名為 **Name** 屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-189">Although piping the contents of `$CustomObject` to `Stop-Service` cmdlet binds to the **Name** parameter, this time it binds **by property name** instead of **by value** because the contents of `$CustomObject` is an object that has a property named **Name**.</span></span>

<span data-ttu-id="3e1d1-190">在此範例中，我使用不同的屬性名稱 (例如 **Service**) 來建立另一個自訂物件。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-190">In this example, I create another custom object using a different property name, such as **Service**.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

<span data-ttu-id="3e1d1-191">嘗試使用管線將 `$CustomObject` 傳送至 `Stop-Service` 時，會產生錯誤，因為它不會產生 **ServiceController** 或 **String** 物件，而且沒有名為 **Name** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-191">An error is generated when trying to pipe `$CustomObject` to `Stop-Service` because it doesn't produce a **ServiceController** or **String** object, and it doesn't have a property named **Name**.</span></span>

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

<span data-ttu-id="3e1d1-192">如果某個命令的輸出未與另一個命令的管線輸入選項對齊，則可以使用 `Select-Object` 來重新命名屬性，使得屬性正確對齊。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-192">If the output of one command doesn't line up with the pipeline input options for another command, `Select-Object` can be used to rename the property so that the properties lineup correctly.</span></span>

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

<span data-ttu-id="3e1d1-193">在此範例中，`Select-Object` 用來將 **Service** 屬性重新命名為 **Name** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-193">In this example, `Select-Object` was used to rename the **Service** property to a property named **Name**.</span></span>

<span data-ttu-id="3e1d1-194">此範例的語法一開始可能有點複雜。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-194">The syntax this example may seem a little complicated at first.</span></span> <span data-ttu-id="3e1d1-195">我所了解到的是，您永遠不需透過複製並貼上程式碼來學習語法。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-195">What I have learned is that you'll never learn the syntax by copy and pasting code.</span></span> <span data-ttu-id="3e1d1-196">花時間輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-196">Take the time to type the code in.</span></span> <span data-ttu-id="3e1d1-197">幾次之後，就會變成您的第二個本質。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-197">After a few times, it becomes second nature.</span></span> <span data-ttu-id="3e1d1-198">有多個監視器是一項很大的優點，因為您可以在一個畫面上顯示範例程式碼，並在另一個螢幕上輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-198">Having multiple monitors is a huge benefit because you can display the example code on one screen and type it in on another one.</span></span>

<span data-ttu-id="3e1d1-199">有時候，您可能會想要使用不接受管線輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-199">Occasionally, you may want to use a parameter that doesn't accept pipeline input.</span></span> <span data-ttu-id="3e1d1-200">下列範例示範如何使用一個命令的輸出作為另一個命令的輸入。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-200">The following example demonstrates using the output of one command as input for another.</span></span> <span data-ttu-id="3e1d1-201">首先，將幾個 Windows 服務的顯示名稱儲存至文字檔中。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-201">First save the display name for a couple of Windows services into a text file.</span></span>

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

<span data-ttu-id="3e1d1-202">您可以執行命令，在括弧中提供所需的輸出，作為需要輸入之命令的參數值。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-202">You can run the command that provides the needed output within parentheses as the value for the parameter of the command requiring the input.</span></span>

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

<span data-ttu-id="3e1d1-203">對於記得其運作方式的您，這就像是代數中的運算順序。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-203">This is just like order of operations in Algebra for those of you who remember how it works.</span></span> <span data-ttu-id="3e1d1-204">括弧內的命令一律在命令的外部部分之前執行。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-204">The command within parentheses always runs prior to the outer portion of the command.</span></span>

## <a name="powershellget"></a><span data-ttu-id="3e1d1-205">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="3e1d1-205">PowerShellGet</span></span>

<span data-ttu-id="3e1d1-206">PowerShellGet 是 PowerShell 模組，其中包含用於往返 NuGet 儲存庫探索、安裝、發佈及更新 PowerShell 模組 (和其他成品) 的命令。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-206">PowerShellGet is a PowerShell module that contains commands for discovering, installing, publishing, and updating PowerShell modules (and other artifacts) to or from a NuGet repository.</span></span> <span data-ttu-id="3e1d1-207">PowerShellGet 隨附 PowerShell 5.0 版和更新版本。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-207">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="3e1d1-208">其以 PowerShell 3.0 版和更新版本的個別下載形式提供。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-208">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="3e1d1-209">Microsoft 會主控名為 [PowerShell 資源庫][]的線上 NuGet 儲存庫。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-209">Microsoft hosts an online NuGet repository called the [PowerShell Gallery][].</span></span> <span data-ttu-id="3e1d1-210">雖然此儲存庫是由 Microsoft 所主控，但儲存庫中包含的大部分模組都不是由 Microsoft 所撰寫。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-210">Although this repository is hosted by Microsoft, the majority of the modules contained within the repository aren't written by Microsoft.</span></span> <span data-ttu-id="3e1d1-211">從 PowerShell 資源庫取得的任何程式碼，都應該在隔離的測試環境中徹底檢閱，然後才將其視為適合在生產環境中使用。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-211">Any code obtain from the PowerShell Gallery should be thoroughly reviewed in an isolated test environment before being considered suitable for use in a production environment.</span></span>

<span data-ttu-id="3e1d1-212">大部分的公司都想要主控自己的內部私人 NuGet 儲存庫，在其中，他們能夠張貼僅限內部使用的模組，以及從其他來源下載的模組 (在將其驗證為非惡意的情況下)。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-212">Most companies will want to host their own internal private NuGet repository where they can post their internal use only modules as well as modules that they've downloaded from other sources once they've validated them as being non-malicious.</span></span>

<span data-ttu-id="3e1d1-213">使用 PowerShellGet 模組中的 `Find-Module` Cmdlet，在 PowerShell 資源庫中尋找我撰寫、名為 MrToolkit 的模組。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-213">Use the `Find-Module` cmdlet that's part of the PowerShellGet module to find a module in the PowerShell Gallery that I wrote named MrToolkit.</span></span>

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

<span data-ttu-id="3e1d1-214">第一次使用 PowerShellGet 模組中的其中一個命令時，系統會提示您安裝 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-214">The first time you use one of the commands from the PowerShellGet module, you'll be prompted to install the NuGet provider.</span></span>

<span data-ttu-id="3e1d1-215">若要安裝 MrToolkit 模組，請將前一個命令以管線傳送至 `Install-Module`。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-215">To install the MrToolkit module, pipe the previous command to `Install-Module`.</span></span>

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

<span data-ttu-id="3e1d1-216">由於 PowerShell 資源庫是未受信任的儲存庫，因此系統會提示您核准安裝模組。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-216">Since the PowerShell Gallery is an untrusted repository, it prompts you to approve the installation of the module.</span></span>

## <a name="finding-pipeline-input-the-easy-way"></a><span data-ttu-id="3e1d1-217">以簡單的方式尋找管線輸入</span><span class="sxs-lookup"><span data-stu-id="3e1d1-217">Finding pipeline input the easy way</span></span>

<span data-ttu-id="3e1d1-218">MrToolkit 模組包含名為 `Get-MrPipelineInput` 的函式。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-218">The MrToolkit module contains a function named `Get-MrPipelineInput`.</span></span> <span data-ttu-id="3e1d1-219">此 Cmdlet 可以用來輕鬆地判斷命令的哪些參數會接受管線輸入、所接受的物件類型，以及它們是否接受管線輸入 **by value** 或 **by property name**。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-219">This cmdlet can be used to easily determine which parameters of a command accept pipeline input, what type of object they accept, and if they accept pipeline input **by value** or **by property name**.</span></span>

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

<span data-ttu-id="3e1d1-220">如您所見，我們先前透過篩檢說明所判斷的資訊，很容易就能使用此函式來判斷。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-220">As you can see, the same information we previously determined by sifting through the help can easily be determined with this function.</span></span>

## <a name="summary"></a><span data-ttu-id="3e1d1-221">摘要</span><span class="sxs-lookup"><span data-stu-id="3e1d1-221">Summary</span></span>

<span data-ttu-id="3e1d1-222">在本章中，您已了解 PowerShell 單行程式碼。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-222">In this chapter, you've learned about PowerShell one-liners.</span></span> <span data-ttu-id="3e1d1-223">您已了解命令所在的實際行數，與它是否為 PowerShell 單行程式碼無關。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-223">You've learned that the number of physical lines that a command is on has nothing to do with whether or not it's a PowerShell one-liner.</span></span> <span data-ttu-id="3e1d1-224">您也已了解有關篩選左側、管線和 PowerShellGet。</span><span class="sxs-lookup"><span data-stu-id="3e1d1-224">You've also learned about filtering left, the pipeline, and PowerShellGet.</span></span>

## <a name="review"></a><span data-ttu-id="3e1d1-225">檢閱</span><span class="sxs-lookup"><span data-stu-id="3e1d1-225">Review</span></span>

1. <span data-ttu-id="3e1d1-226">什麼是 PowerShell 單行程式碼？</span><span class="sxs-lookup"><span data-stu-id="3e1d1-226">What is a PowerShell one-liner?</span></span>
1. <span data-ttu-id="3e1d1-227">PowerShell 中可能會發生自然換行符號的部分字元有哪些？</span><span class="sxs-lookup"><span data-stu-id="3e1d1-227">What are some of the characters where natural line breaks can occur in PowerShell?</span></span>
1. <span data-ttu-id="3e1d1-228">為什麼應使用左側篩選？</span><span class="sxs-lookup"><span data-stu-id="3e1d1-228">Why should you filter left?</span></span>
1. <span data-ttu-id="3e1d1-229">PowerShell 命令可以接受管線輸入的兩個方式為何？</span><span class="sxs-lookup"><span data-stu-id="3e1d1-229">What are the two ways that a PowerShell command can accept pipeline input?</span></span>
1. <span data-ttu-id="3e1d1-230">為什麼您不應該信任在 PowerShell 資源庫中找到的命令？</span><span class="sxs-lookup"><span data-stu-id="3e1d1-230">Why shouldn't you trust commands found in the PowerShell Gallery?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="3e1d1-231">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="3e1d1-231">Recommended Reading</span></span>

- <span data-ttu-id="3e1d1-232">[about_Pipelines][]</span><span class="sxs-lookup"><span data-stu-id="3e1d1-232">[about_Pipelines][]</span></span>
- <span data-ttu-id="3e1d1-233">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="3e1d1-233">[about_Command_Syntax][]</span></span>
- <span data-ttu-id="3e1d1-234">[about_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="3e1d1-234">[about_Parameters][]</span></span>
- <span data-ttu-id="3e1d1-235">[PowerShellGet：探索、安裝和更新 PowerShell 模組的最簡單方式][psget]</span><span class="sxs-lookup"><span data-stu-id="3e1d1-235">[PowerShellGet: The BIG EASY way to discover, install, and update PowerShell modules][psget]</span></span>

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell 資源庫]: https://www.powershellgallery.com/
[PowerShell Gallery]: https://www.powershellgallery.com/
