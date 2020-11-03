---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: 2fe48f90b020d0566364f4f24554cb3442880ab5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203220"
---
# <span data-ttu-id="4a20e-103">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="4a20e-103">Import-PSSession</span></span>

## <span data-ttu-id="4a20e-104">概要</span><span class="sxs-lookup"><span data-stu-id="4a20e-104">SYNOPSIS</span></span>
<span data-ttu-id="4a20e-105">將另一個工作階段的命令匯入目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="4a20e-105">Imports commands from another session into the current session.</span></span>

## <span data-ttu-id="4a20e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4a20e-106">SYNTAX</span></span>

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## <span data-ttu-id="4a20e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4a20e-107">DESCRIPTION</span></span>
<span data-ttu-id="4a20e-108">**Import-module** Cmdlet 會從本機或遠端電腦上的 PSSession 將命令匯入至目前的會話，例如 Cmdlet、函式和別名。</span><span class="sxs-lookup"><span data-stu-id="4a20e-108">The **Import-PSSession** cmdlet imports commands , such as cmdlets, functions, and aliases, from a PSSession on a local or remote computer into the current session.</span></span>
<span data-ttu-id="4a20e-109">您可以匯入 Get-Command Cmdlet 可在 PSSession 中找到的任何命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-109">You can import any command that the Get-Command cmdlet can find in the PSSession.</span></span>

<span data-ttu-id="4a20e-110">使用 **Import-PSSession** 命令可從自訂殼層 (例如 Microsoft Exchange Server 殼層)，或從包含 Windows PowerShell 模組和嵌入式管理單元或不在目前工作階段的其他元素的工作階段匯入命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-110">Use an **Import-PSSession** command to import commands from a customized shell, such as a Microsoft Exchange Server shell, or from a session that includes Windows PowerShell modules and snap-ins or other elements that are not in the current session.</span></span>

<span data-ttu-id="4a20e-111">若要匯入命令，請先使用 New-PSSession Cmdlet 來建立 PSSession。</span><span class="sxs-lookup"><span data-stu-id="4a20e-111">To import commands, first use the New-PSSession cmdlet to create a PSSession.</span></span>
<span data-ttu-id="4a20e-112">然後，使用 **Import-PSSession** Cmdlet 匯入命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-112">Then, use the **Import-PSSession** cmdlet to import the commands.</span></span>
<span data-ttu-id="4a20e-113">根據預設， **Import-PSSession** 會匯入除了與目前工作階段中具有相同命令名稱以外的所有命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-113">By default, **Import-PSSession** imports all commands except for commands that have the same names as commands in the current session.</span></span>
<span data-ttu-id="4a20e-114">若要匯入所有命令，請使用 *AllowClobber* 參數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-114">To import all the commands, use the *AllowClobber* parameter.</span></span>

<span data-ttu-id="4a20e-115">您可以使用匯入的命令，就像您使用工作階段中的任何命令一樣。</span><span class="sxs-lookup"><span data-stu-id="4a20e-115">You can use imported commands just as you would use any command in the session.</span></span>
<span data-ttu-id="4a20e-116">當您使用匯入的命令時，匯入的命令部份會隱含地在從匯入的工作階段中執行。</span><span class="sxs-lookup"><span data-stu-id="4a20e-116">When you use an imported command, the imported part of the command runs implicitly in the session from which it was imported.</span></span>
<span data-ttu-id="4a20e-117">不過，遠端操作則會完全由 Windows PowerShell 處理。</span><span class="sxs-lookup"><span data-stu-id="4a20e-117">However, the remote operations are handled entirely by Windows PowerShell.</span></span>
<span data-ttu-id="4a20e-118">您甚至不需要知道這些操作，不過必須讓其他工作階段 (PSSession) 的連線保持開啟。</span><span class="sxs-lookup"><span data-stu-id="4a20e-118">You need not even be aware of them, except that you must keep the connection to the other session (PSSession) open.</span></span>
<span data-ttu-id="4a20e-119">如果您關閉它，匯入的命令就不再可用。</span><span class="sxs-lookup"><span data-stu-id="4a20e-119">If you close it, the imported commands are no longer available.</span></span>

<span data-ttu-id="4a20e-120">因為匯入的命令可能會比本機命令需要花費較長的時間，所以 **Import-PSSession** 會對每個匯入的命令加入 *AsJob* 參數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-120">Because imported commands might take longer to run than local commands, **Import-PSSession** adds an *AsJob* parameter to every imported command.</span></span>
<span data-ttu-id="4a20e-121">此參數可讓您以 Windows PowerShell 背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-121">This parameter allows you to run the command as a Windows PowerShell background job.</span></span>
<span data-ttu-id="4a20e-122">如需詳細資訊，請參閱 about_Jobs。</span><span class="sxs-lookup"><span data-stu-id="4a20e-122">For more information, see about_Jobs.</span></span>

<span data-ttu-id="4a20e-123">當您使用 **Import-PSSession** 時，Windows PowerShell 會將匯入的命令加入只存在於您工作階段中的暫存模組，並且傳回代表該模組的物件。</span><span class="sxs-lookup"><span data-stu-id="4a20e-123">When you use **Import-PSSession** , Windows PowerShell adds the imported commands to a temporary module that exists only in your session and returns an object that represents the module.</span></span>
<span data-ttu-id="4a20e-124">若要建立可在未來的會話中使用的持續性模組，請使用 Export-PSSession Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-124">To create a persistent module that you can use in future sessions, use the Export-PSSession cmdlet.</span></span>

<span data-ttu-id="4a20e-125">**Import-PSSession** Cmdlet 會使用 Windows PowerShell 的隱含遠端執行功能。</span><span class="sxs-lookup"><span data-stu-id="4a20e-125">The **Import-PSSession** cmdlet uses the implicit remoting feature of Windows PowerShell.</span></span>
<span data-ttu-id="4a20e-126">當您將命令匯入目前的會話時，它們會以隱含方式在原始會話中或在來源電腦上類似的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="4a20e-126">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

<span data-ttu-id="4a20e-127">從 Windows PowerShell 3.0 開始，您可以使用 Import-Module Cmdlet 將遠端會話的模組匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="4a20e-127">Beginning in Windows PowerShell 3.0, you can use the Import-Module cmdlet to import modules from a remote session into the current session.</span></span>
<span data-ttu-id="4a20e-128">這項功能使用隱含的遠端執行功能。</span><span class="sxs-lookup"><span data-stu-id="4a20e-128">This feature uses implicit remoting.</span></span>
<span data-ttu-id="4a20e-129">它等同於使用 **Import-PSSession** 將遠端工作階段中選取的模組匯入目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="4a20e-129">It is equivalent to using **Import-PSSession** to import selected modules from a remote session into the current session.</span></span>

## <span data-ttu-id="4a20e-130">範例</span><span class="sxs-lookup"><span data-stu-id="4a20e-130">EXAMPLES</span></span>

### <span data-ttu-id="4a20e-131">範例1：從 PSSession 匯入所有命令</span><span class="sxs-lookup"><span data-stu-id="4a20e-131">Example 1: Import all commands from a PSSession</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

<span data-ttu-id="4a20e-132">此命令將 Server01 電腦上 PSSession 的所有命令 (除了與目前工作階段中具有相同命令名稱的命令) 匯入目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="4a20e-132">This command imports all commands from a PSSession on the Server01 computer into the current session, except for commands that have the same names as commands in the current session.</span></span>

<span data-ttu-id="4a20e-133">因為此命令沒有使用 *CommandName* 參數，所以它也會將匯入命令所需的所有格式化資料匯入。</span><span class="sxs-lookup"><span data-stu-id="4a20e-133">Because this command does not use the *CommandName* parameter, it also imports all of the formatting data required for the imported commands.</span></span>

### <span data-ttu-id="4a20e-134">範例2：匯入以特定字串結尾的命令</span><span class="sxs-lookup"><span data-stu-id="4a20e-134">Example 2: Import commands that end with a specific string</span></span>

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

<span data-ttu-id="4a20e-135">這些命令會從 PSSession 將名稱結尾為 "-test" 的命令匯入本機工作階段，然後顯示如何使用匯入的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-135">These commands import the commands with names that end in "-test" from a PSSession into the local session, and then they show how to use an imported cmdlet.</span></span>

<span data-ttu-id="4a20e-136">第一個命令會使用 New-PSSession Cmdlet 來建立 PSSession。</span><span class="sxs-lookup"><span data-stu-id="4a20e-136">The first command uses the New-PSSession cmdlet to create a PSSession.</span></span>
<span data-ttu-id="4a20e-137">它會將 PSSession 儲存在 $S 變數中。</span><span class="sxs-lookup"><span data-stu-id="4a20e-137">It saves the PSSession in the $S variable.</span></span>

<span data-ttu-id="4a20e-138">第二個命令使用 **import-module** Cmdlet 從 $S 中的 PSSession 將命令匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="4a20e-138">The second command uses the **Import-PSSession** cmdlet to import commands from the PSSession in $S into the current session.</span></span>
<span data-ttu-id="4a20e-139">它使用 *CommandName* 參數指定具有 Test 名詞的命令，以及使用 *FormatTypeName* 參數匯入各種 Test 命令的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="4a20e-139">It uses the *CommandName* parameter to specify commands with the Test noun and the *FormatTypeName* parameter to import the formatting data for the Test commands.</span></span>

<span data-ttu-id="4a20e-140">第三個和第四個命令在目前的工作階段中使用匯入的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-140">The third and fourth commands use the imported commands in the current session.</span></span>
<span data-ttu-id="4a20e-141">因為匯入的命令已經實際新增到目前的工作階段中，所以您要使用本機語法執行它們。</span><span class="sxs-lookup"><span data-stu-id="4a20e-141">Because imported commands are actually added to the current session, you use the local syntax to run them.</span></span>
<span data-ttu-id="4a20e-142">您不需要使用 Invoke-Command Cmdlet 來執行匯入的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-142">You do not need to use the Invoke-Command cmdlet to run an imported command.</span></span>

### <span data-ttu-id="4a20e-143">範例3：從 PSSession 匯入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4a20e-143">Example 3: Import cmdlets from a PSSession</span></span>

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

<span data-ttu-id="4a20e-144">此範例示範使用匯入的 Cmdlet 就如同使用本機 Cmdlet 一樣。</span><span class="sxs-lookup"><span data-stu-id="4a20e-144">This example shows that you can use imported cmdlets just as you would use local cmdlets.</span></span>

<span data-ttu-id="4a20e-145">這些命令從 Server01 電腦的 PSSession 匯入 New-Test 和 Get-Test Cmdlet，以及從 Server02 電腦的 PSSession 匯入 Set-Test Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-145">These commands import the New-Test and Get-Test cmdlets from a PSSession on the Server01 computer and the Set-Test cmdlet from a PSSession on the Server02 computer.</span></span>

<span data-ttu-id="4a20e-146">即使是從不同的 PSSession 匯入 Cmdlet，您還是可以使用管線將物件從一個 Cmdlet 傳送到另一個 Cmdlet 而不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a20e-146">Even though the cmdlets were imported from different PSSessions, you can pipe an object from one cmdlet to another without error.</span></span>

### <span data-ttu-id="4a20e-147">範例4：以背景工作的形式執行匯入的命令</span><span class="sxs-lookup"><span data-stu-id="4a20e-147">Example 4: Run an imported command as a background job</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

<span data-ttu-id="4a20e-148">此範例示範如何以背景工作的方式執行匯入的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-148">This example shows how to run an imported command as a background job.</span></span>

<span data-ttu-id="4a20e-149">因為匯入的命令可能會比本機命令需要花費較長的時間，所以 **Import-PSSession** 會對每個匯入的命令加入 *AsJob* 參數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-149">Because imported commands might take longer to run than local commands, **Import-PSSession** adds an *AsJob* parameter to every imported command.</span></span>
<span data-ttu-id="4a20e-150">*AsJob* 參數可讓您以背景工作的方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-150">The *AsJob* parameter lets you run the command as a background job.</span></span>

<span data-ttu-id="4a20e-151">第一個命令在 Server01 電腦上建立 PSSession，並將 PSSession 物件儲存在 $S 變數中。</span><span class="sxs-lookup"><span data-stu-id="4a20e-151">The first command creates a PSSession on the Server01 computer and saves the PSSession object in the $S variable.</span></span>

<span data-ttu-id="4a20e-152">第二個命令會使用 **import-module** 將 $S 中 PSSession 的測試 Cmdlet 匯入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="4a20e-152">The second command uses **Import-PSSession** to import the Test cmdlets from the PSSession in $S into the current session.</span></span>

<span data-ttu-id="4a20e-153">第三個命令使用匯入的 New-Test Cmdlet 的 *AsJob* 參數，以背景工作的方式執行 New-Test 命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-153">The third command uses the *AsJob* parameter of the imported New-Test cmdlet to run a New-Test command as a background job.</span></span>
<span data-ttu-id="4a20e-154">命令會將 New-Test 傳回的工作物件儲存在 $batch 變數中。</span><span class="sxs-lookup"><span data-stu-id="4a20e-154">The command saves the job object that New-Test returns in the $batch variable.</span></span>

<span data-ttu-id="4a20e-155">第四個命令使用 Receive-Job Cmdlet 取得 $batch 變數中工作的結果。</span><span class="sxs-lookup"><span data-stu-id="4a20e-155">The fourth command uses the Receive-Job cmdlet to get the results of the job in the $batch variable.</span></span>

### <span data-ttu-id="4a20e-156">範例5：從 Windows PowerShell 模組匯入 Cmdlet 和函數</span><span class="sxs-lookup"><span data-stu-id="4a20e-156">Example 5: Import cmdlets and functions from a Windows PowerShell module</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

<span data-ttu-id="4a20e-157">此範例示範如何從遠端電腦的 Windows PowerShell 模組將 Cmdlet 和函式匯入目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="4a20e-157">This example shows how to import the cmdlets and functions from a Windows PowerShell module on a remote computer into the current session.</span></span>

<span data-ttu-id="4a20e-158">第一個命令在 Server01 電腦上建立 PSSession，並將它儲存在 $S 變數中。</span><span class="sxs-lookup"><span data-stu-id="4a20e-158">The first command creates a PSSession on the Server01 computer and saves it in the $S variable.</span></span>

<span data-ttu-id="4a20e-159">第二個命令使用 **Invoke 命令** Cmdlet，在 $S 中的 PSSession 中執行 Import-Module 命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-159">The second command uses the **Invoke-Command** cmdlet to run an Import-Module command in the PSSession in $S.</span></span>

<span data-ttu-id="4a20e-160">**Import-Module** 命令通常會將 Windows PowerShell 設定檔中的模組新增到所有工作階段，但是並不會在 PSSession 中執行設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a20e-160">Typically, the module would be added to all sessions by an **Import-Module** command in a Windows PowerShell profile, but profiles are not run in PSSessions.</span></span>

<span data-ttu-id="4a20e-161">第三個命令使用 Import-module 的 *module*  參數將模組中的 Cmdlet 和函 **式** 匯入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="4a20e-161">The third command uses the *Module*  parameter of **Import-PSSession** to import the cmdlets and functions in the module into the current session.</span></span>

### <span data-ttu-id="4a20e-162">範例6：在暫存檔案中建立模組</span><span class="sxs-lookup"><span data-stu-id="4a20e-162">Example 6: Create a module in a temporary file</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="4a20e-163">此範例顯示 **Import-PSSession** 在磁碟上的暫存檔案中建立模組。</span><span class="sxs-lookup"><span data-stu-id="4a20e-163">This example shows that **Import-PSSession** creates a module in a temporary file on disk.</span></span>
<span data-ttu-id="4a20e-164">它也會顯示所有命令在匯入目前工作階段之前，都已轉換成函式。</span><span class="sxs-lookup"><span data-stu-id="4a20e-164">It also shows that all commands are converted into functions before they are imported into the current session.</span></span>

<span data-ttu-id="4a20e-165">此命令會使用 **import-module** Cmdlet 將 Get-Date Cmdlet 和 SearchHelp 函式匯入目前的會話中。</span><span class="sxs-lookup"><span data-stu-id="4a20e-165">The command uses the **Import-PSSession** cmdlet to import a Get-Date cmdlet and a SearchHelp function into the current session.</span></span>

<span data-ttu-id="4a20e-166">**Import-PSSession** Cmdlet 傳回代表暫存模組的 **PSModuleInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="4a20e-166">The **Import-PSSession** cmdlet returns a **PSModuleInfo** object that represents the temporary module.</span></span>
<span data-ttu-id="4a20e-167">**Path** 屬性的值顯示 **Import-PSSession** 在暫存位置中建立了指令碼模組 (.psm1) 檔案。</span><span class="sxs-lookup"><span data-stu-id="4a20e-167">The value of the **Path** property shows that **Import-PSSession** created a script module (.psm1) file in a temporary location.</span></span>
<span data-ttu-id="4a20e-168">**ExportedFunctions** 屬性顯示 **Get-Date** Cmdlet 與 SearchHelp 函式兩者都已匯入成為函式。</span><span class="sxs-lookup"><span data-stu-id="4a20e-168">The **ExportedFunctions** property shows that the **Get-Date** cmdlet and the SearchHelp function were both imported as functions.</span></span>

### <span data-ttu-id="4a20e-169">範例7：執行匯入的命令所隱藏的命令</span><span class="sxs-lookup"><span data-stu-id="4a20e-169">Example 7: Run a command that is hidden by an imported command</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

<span data-ttu-id="4a20e-170">此範例示範如何執行被匯入的命令隱藏的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-170">This example shows how to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="4a20e-171">第一個命令會從 $S 變數中的 PSSession 匯入 Get-Date Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-171">The first command imports a Get-Date cmdlet from the PSSession in the $S variable.</span></span>
<span data-ttu-id="4a20e-172">因為目前的工作階段包含 **Get-Date** Cmdlet，所以命令中必須要有 *AllowClobber* 參數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-172">Because the current session includes a **Get-Date** cmdlet, the *AllowClobber* parameter is required in the command.</span></span>

<span data-ttu-id="4a20e-173">第二個命令使用 Get-Command Cmdlet 的 **all** 參數，取得目前會話中的所有 **取得日期** 命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-173">The second command uses the **All** parameter of the Get-Command cmdlet to get all **Get-Date** commands in the current session.</span></span>
<span data-ttu-id="4a20e-174">輸出顯示工作階段包含原始的 **Get-Date** Cmdlet 和 **Get-Date** 函式。</span><span class="sxs-lookup"><span data-stu-id="4a20e-174">The output shows that the session includes the original **Get-Date** cmdlet and a **Get-Date** function.</span></span>
<span data-ttu-id="4a20e-175">**取得日期函式** 會在 $S 中的 PSSession 中執行匯入的 **取得日期** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-175">The **Get-Date** function runs the imported **Get-Date** cmdlet in the PSSession in $S.</span></span>

<span data-ttu-id="4a20e-176">第三個命令執行 **Get-Date** 命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-176">The third command runs a **Get-Date** command.</span></span>
<span data-ttu-id="4a20e-177">因為函式優先於 Cmdlet，所以 Windows PowerShell 會執行匯入的 **Get-Date** 函式並傳回凱薩曆日期。</span><span class="sxs-lookup"><span data-stu-id="4a20e-177">Because functions take precedence over cmdlets, Windows PowerShell runs the imported **Get-Date** function, which returns a Julian date.</span></span>

<span data-ttu-id="4a20e-178">第四個和第五個命令示範如何使用限定的名稱執行被匯入的命令隱藏的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-178">The fourth and fifth commands show how to use a qualified name to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="4a20e-179">第四個命令取得已將原始 **Get-Date** Cmdlet 加入目前工作階段的 Windows PowerShell 嵌入式管理單元名稱。</span><span class="sxs-lookup"><span data-stu-id="4a20e-179">The fourth command gets the name of the Windows PowerShell snap-in that added the original **Get-Date** cmdlet to the current session.</span></span>

<span data-ttu-id="4a20e-180">第五個命令使用 **Get-Date** Cmdlet 的嵌入式管理單元限定名稱執行 **Get-Date** 命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-180">The fifth command uses the snap-in-qualified name of the **Get-Date** cmdlet to run a **Get-Date** command.</span></span>

<span data-ttu-id="4a20e-181">如需有關命令優先順序和隱藏命令的詳細資訊，請參閱 about_Command_Precedence。</span><span class="sxs-lookup"><span data-stu-id="4a20e-181">For more information about command precedence and hidden commands, see about_Command_Precedence.</span></span>

### <span data-ttu-id="4a20e-182">範例8：匯入名稱中有特定字串的命令</span><span class="sxs-lookup"><span data-stu-id="4a20e-182">Example 8: Import commands that have a specific string in their names</span></span>

```
PS C:\> Import-PSSession -Session $S -CommandName *Item* -AllowClobber
```

<span data-ttu-id="4a20e-183">此命令會匯入名稱包含 $S 中 PSSession 之專案的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-183">This command imports commands whose names include Item from the PSSession in $S.</span></span>
<span data-ttu-id="4a20e-184">因為此命令包含 *CommandName* 參數，而不是 *FormatTypeData* 參數，所以只會匯入命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-184">Because the command includes the *CommandName* parameter but not the *FormatTypeData* parameter, only the command is imported.</span></span>

<span data-ttu-id="4a20e-185">當您使用 **Import-PSSession** 在遠端電腦上執行命令，且在目前工作階段中已經有命令的格式化資料時，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-185">Use this command when you are using **Import-PSSession** to run a command on a remote computer and you already have the formatting data for the command in the current session.</span></span>

### <span data-ttu-id="4a20e-186">範例9：使用 Module 參數來探索哪些命令已匯入至會話</span><span class="sxs-lookup"><span data-stu-id="4a20e-186">Example 9: Use the Module parameter to discover which commands were imported into the session</span></span>

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

<span data-ttu-id="4a20e-187">此命令示範如何使用 **get-help** 的 *Module* 參數，找出由 **import-module** 命令匯入會話的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-187">This command shows how to use the *Module* parameter of **Get-Command** to find out which commands were imported into the session by an **Import-PSSession** command.</span></span>

<span data-ttu-id="4a20e-188">第一個命令會使用 **import-module** Cmdlet 從 $S 變數中的 PSSession 匯入名稱包含 "bits" 的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-188">The first command uses the **Import-PSSession** cmdlet to import commands whose names include "bits" from the PSSession in the $S variable.</span></span>
<span data-ttu-id="4a20e-189">**Import-PSSession** 命令傳回一個暫存模組，而且命令將模組儲存在 $m 變數中。</span><span class="sxs-lookup"><span data-stu-id="4a20e-189">The **Import-PSSession** command returns a temporary module, and the command saves the module in the $m variable.</span></span>

<span data-ttu-id="4a20e-190">第二個命令使用 Get-Command Cmdlet 來取得 $M 變數中的模組所匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-190">The second command uses the Get-Command cmdlet to get the commands that are exported by the module in the $M variable.</span></span>

<span data-ttu-id="4a20e-191">*Module* 參數會使用設計來做為模組名稱的字串值。</span><span class="sxs-lookup"><span data-stu-id="4a20e-191">The *Module* parameter takes a string value, which is designed for the module name.</span></span>
<span data-ttu-id="4a20e-192">不過，當您送出模組物件時，Windows PowerShell 會對模組物件使用 **ToString** 方法，傳回模組名稱。</span><span class="sxs-lookup"><span data-stu-id="4a20e-192">However, when you submit a module object, Windows PowerShell uses the **ToString** method on the module object, which returns the module name.</span></span>

<span data-ttu-id="4a20e-193">**Get 命令** 命令相當於 `Get-Command $M.Name` "。</span><span class="sxs-lookup"><span data-stu-id="4a20e-193">The **Get-Command** command is the equivalent of `Get-Command $M.Name`".</span></span>

## <span data-ttu-id="4a20e-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4a20e-194">PARAMETERS</span></span>

### <span data-ttu-id="4a20e-195">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="4a20e-195">-AllowClobber</span></span>
<span data-ttu-id="4a20e-196">指出此 Cmdlet 會匯入指定的命令，即使它們的名稱與目前會話中的命令相同。</span><span class="sxs-lookup"><span data-stu-id="4a20e-196">Indicates that this cmdlet imports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="4a20e-197">如果您匯入與目前工作階段中的命令同名的命令，匯入的命令將會隱藏或取代原始命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-197">If you import a command with the same name as a command in the current session, the imported command hides or replaces the original commands.</span></span>
<span data-ttu-id="4a20e-198">如需詳細資訊，請參閱 about_Command_Precedence。</span><span class="sxs-lookup"><span data-stu-id="4a20e-198">For more information, see about_Command_Precedence.</span></span>

<span data-ttu-id="4a20e-199">根據預設， **Import-PSSession** 不會匯入與目前工作階段中的命令具有相同名稱的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-199">By default, **Import-PSSession** does not import commands that have the same name as commands in the current session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-200">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="4a20e-200">-ArgumentList</span></span>
<span data-ttu-id="4a20e-201">指定使用指定的引數 (參數值) 所產生的命令陣列。</span><span class="sxs-lookup"><span data-stu-id="4a20e-201">Specifies an array of commands that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="4a20e-202">例如，若要將 Get-Item 命令的變異數匯入 $S 中 PSSession 的憑證 (Cert： ) 磁片磁碟機，請輸入 `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 。</span><span class="sxs-lookup"><span data-stu-id="4a20e-202">For instance, to import the variant of the Get-Item command in the certificate (Cert:) drive in the PSSession in $S, type `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-203">-Certificate</span><span class="sxs-lookup"><span data-stu-id="4a20e-203">-Certificate</span></span>
<span data-ttu-id="4a20e-204">指定用來簽署格式檔案 (\*.Format.ps1xml)，或是簽署由 **Import-PSSession** 建立之暫存模組中的指令碼模組檔案 (.psm1) 的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="4a20e-204">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the temporary module that **Import-PSSession** creates.</span></span>

<span data-ttu-id="4a20e-205">輸入包含憑證的變數，或可取得憑證的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="4a20e-205">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="4a20e-206">若要尋找憑證，請使用 Get-PfxCertificate Cmdlet，或在憑證 (Cert： ) 磁片磁碟機中使用 Get-ChildItem Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-206">To find a certificate, use the Get-PfxCertificate cmdlet or use the Get-ChildItem cmdlet in the Certificate (Cert:) drive.</span></span>
<span data-ttu-id="4a20e-207">若憑證無效或權限不足，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="4a20e-207">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-208">-CommandName</span><span class="sxs-lookup"><span data-stu-id="4a20e-208">-CommandName</span></span>
<span data-ttu-id="4a20e-209">指定具有指定名稱或名稱模式的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-209">Specifies commands with the specified names or name patterns.</span></span>
<span data-ttu-id="4a20e-210">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4a20e-210">Wildcards are permitted.</span></span>
<span data-ttu-id="4a20e-211">使用 *CommandName* 或其別名 *Name* 。</span><span class="sxs-lookup"><span data-stu-id="4a20e-211">Use *CommandName* or its alias, *Name* .</span></span>

<span data-ttu-id="4a20e-212">根據預設， **Import-PSSession** 會從工作階段中匯入除了與目前工作階段中具有相同命令名稱以外的所有命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-212">By default, **Import-PSSession** imports all commands from the session, except for commands that have the same names as commands in the current session.</span></span>
<span data-ttu-id="4a20e-213">這可防止匯入的命令隱藏或取代工作階段中的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-213">This prevents imported commands from hiding or replacing commands in the session.</span></span>
<span data-ttu-id="4a20e-214">若要匯入所有命令，包含那些會隱藏或取代其他命令的命令，請使用 *AllowClobber* 參數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-214">To import all commands, even those that hide or replace other commands, use the *AllowClobber* parameter.</span></span>

<span data-ttu-id="4a20e-215">您使用 *CommandName* 參數時，除非您使用 *FormatTypeName* 參數，否則不會匯入命令的格式設定檔案。</span><span class="sxs-lookup"><span data-stu-id="4a20e-215">If you use the *CommandName* parameter, the formatting files for the commands are not imported unless you use the *FormatTypeName* parameter.</span></span>
<span data-ttu-id="4a20e-216">同樣地，使用 *FormatTypeName* 參數時，除非您使用 *CommandName* 參數，否則不會匯入任何命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-216">Similarly, if you use the *FormatTypeName* parameter, no commands are imported unless you use the *CommandName* parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-217">-CommandType</span><span class="sxs-lookup"><span data-stu-id="4a20e-217">-CommandType</span></span>
<span data-ttu-id="4a20e-218">指定命令物件的類型。</span><span class="sxs-lookup"><span data-stu-id="4a20e-218">Specifies the type of command objects.</span></span>
<span data-ttu-id="4a20e-219">預設值為 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-219">The default value is Cmdlet.</span></span>
<span data-ttu-id="4a20e-220">使用 *CommandType* 或它的別名 *Type* 。</span><span class="sxs-lookup"><span data-stu-id="4a20e-220">Use *CommandType* or its alias, *Type* .</span></span>
<span data-ttu-id="4a20e-221">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="4a20e-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4a20e-222">別名。</span><span class="sxs-lookup"><span data-stu-id="4a20e-222">Alias.</span></span>
<span data-ttu-id="4a20e-223">遠端工作階段中的 Windows PowerShell 別名。</span><span class="sxs-lookup"><span data-stu-id="4a20e-223">The Windows PowerShell aliases in the remote session.</span></span>
- <span data-ttu-id="4a20e-224">全部。</span><span class="sxs-lookup"><span data-stu-id="4a20e-224">All.</span></span>
<span data-ttu-id="4a20e-225">遠端工作階段中的 Cmdlet 與函式。</span><span class="sxs-lookup"><span data-stu-id="4a20e-225">The cmdlets and functions in the remote session.</span></span>
- <span data-ttu-id="4a20e-226">應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a20e-226">Application.</span></span>
<span data-ttu-id="4a20e-227">除了在遠端工作階段中，Path 環境變數 ($env:path) 所列出路徑裡的 Windows PowerShell 檔案以外的所有檔案，包括 .txt、.exe 和 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="4a20e-227">All the files other than Windows-PowerShell files in the paths that are listed in the Path environment variable ($env:path) in the remote session, including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="4a20e-228">Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-228">Cmdlet.</span></span>
<span data-ttu-id="4a20e-229">遠端工作階段中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-229">The cmdlets in the remote session.</span></span>
<span data-ttu-id="4a20e-230">"Cmdlet" 為預設值。</span><span class="sxs-lookup"><span data-stu-id="4a20e-230">"Cmdlet" is the default.</span></span>
- <span data-ttu-id="4a20e-231">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="4a20e-231">ExternalScript.</span></span>
<span data-ttu-id="4a20e-232">在遠端工作階段中，Path 環境變數 ($env:path) 所列出路徑裡的 .ps1 檔案。</span><span class="sxs-lookup"><span data-stu-id="4a20e-232">The .ps1 files in the paths listed in the Path environment variable ($env:path) in the remote session.</span></span>
- <span data-ttu-id="4a20e-233">篩選和函數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-233">Filter and Function.</span></span>
<span data-ttu-id="4a20e-234">遠端工作階段中的 Windows PowerShell 函式。</span><span class="sxs-lookup"><span data-stu-id="4a20e-234">The Windows PowerShell functions in the remote session.</span></span>
- <span data-ttu-id="4a20e-235">指令碼：</span><span class="sxs-lookup"><span data-stu-id="4a20e-235">Script.</span></span>
<span data-ttu-id="4a20e-236">遠端工作階段中的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="4a20e-236">The script blocks in the remote session.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-237">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="4a20e-237">-DisableNameChecking</span></span>
<span data-ttu-id="4a20e-238">指出當您匯入的 Cmdlet 或函式的名稱包含未核准的動詞或禁止的字元時，此 Cmdlet 會隱藏警告您的訊息。</span><span class="sxs-lookup"><span data-stu-id="4a20e-238">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="4a20e-239">依預設，當您匯入的模組會匯出其名稱中具有未核准動詞的 Cmdlet 或函式時，Windows PowerShell 會顯示下列警告訊息：</span><span class="sxs-lookup"><span data-stu-id="4a20e-239">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, the Windows PowerShell displays the following warning message:</span></span>

<span data-ttu-id="4a20e-240">「警告：某些匯入的命令名稱包含未核准的動詞命令，可能會讓它們更不容易探索。</span><span class="sxs-lookup"><span data-stu-id="4a20e-240">"WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span>
<span data-ttu-id="4a20e-241">請使用 Verbose 參數取得詳細資訊，或輸入 Get-Verb 查看核准的動詞清單。」</span><span class="sxs-lookup"><span data-stu-id="4a20e-241">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs."</span></span>

<span data-ttu-id="4a20e-242">這則訊息只是一個警告。</span><span class="sxs-lookup"><span data-stu-id="4a20e-242">This message is only a warning.</span></span>
<span data-ttu-id="4a20e-243">模組仍然完整匯入，包括不合格的命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-243">The complete module is still imported, including the non-conforming commands.</span></span>
<span data-ttu-id="4a20e-244">雖然訊息是顯示給模組的使用者，但命名的問題應該由模組作者修正。</span><span class="sxs-lookup"><span data-stu-id="4a20e-244">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-245">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="4a20e-245">-FormatTypeName</span></span>
<span data-ttu-id="4a20e-246">指定指定之 Microsoft .NET Framework 類型的格式設定指示。</span><span class="sxs-lookup"><span data-stu-id="4a20e-246">Specifies formatting instructions for the specified Microsoft .NET Framework types.</span></span>
<span data-ttu-id="4a20e-247">輸入類型名稱。</span><span class="sxs-lookup"><span data-stu-id="4a20e-247">Enter the type names.</span></span>
<span data-ttu-id="4a20e-248">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4a20e-248">Wildcards are permitted.</span></span>

<span data-ttu-id="4a20e-249">這個參數的值必須是從中匯入命令之來源工作階段中的 Get-FormatData 命令所傳回之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a20e-249">The value of this parameter must be the name of a type that is returned by a Get-FormatData command in the session from which the commands are being imported.</span></span>
<span data-ttu-id="4a20e-250">若要取得遠端工作階段中的所有格式設定資料，請輸入 \*。</span><span class="sxs-lookup"><span data-stu-id="4a20e-250">To get all of the formatting data in the remote session, type \*.</span></span>

<span data-ttu-id="4a20e-251">如果命令未包含 *CommandName* 或 *FormatTypeName* 參數，則在遠端會話中， **import-module** 會匯入 **FormatData** 命令所傳回之所有 .NET Framework 類型的格式設定指示。</span><span class="sxs-lookup"><span data-stu-id="4a20e-251">If the command does not include either the *CommandName* or *FormatTypeName* parameter, **Import-PSSession** imports formatting instructions for all .NET Framework types returned by a **Get-FormatData** command in the remote session.</span></span>

<span data-ttu-id="4a20e-252">如果您使用 *FormatTypeName* 參數，除非使用 *CommandName* 參數，否則不會匯入任何命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-252">If you use the *FormatTypeName* parameter, no commands are imported unless you use the *CommandName* parameter.</span></span>

<span data-ttu-id="4a20e-253">同樣地，如果您使用 *CommandName* 參數，除非使用 *FormatTypeName* 參數，否則不會匯入命令的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="4a20e-253">Similarly, if you use the *CommandName* parameter, the formatting files for the commands are not imported unless you use the *FormatTypeName* parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-254">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="4a20e-254">-FullyQualifiedModule</span></span>
<span data-ttu-id="4a20e-255">以 **ModuleSpecification** 物件的形式指定具有名稱的模組， (MSDN library 中的 [ModuleSpecification (表)](https://msdn.microsoft.com/library/jj136290) 的 [備註] 區段中所述) 。</span><span class="sxs-lookup"><span data-stu-id="4a20e-255">Specifies modules with names that are specified in the form of **ModuleSpecification** objects (described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library).</span></span>
<span data-ttu-id="4a20e-256">例如， *FullyQualifiedModule* 參數會接受以 @ {ModuleName = "modulename" 格式指定的模組名稱;ModuleVersion = "version_number"} 或 @ {ModuleName = "modulename";ModuleVersion = "version_number";Guid = "GUID"}。</span><span class="sxs-lookup"><span data-stu-id="4a20e-256">For example, the *FullyQualifiedModule* parameter accepts a module name that is specified in the format @{ModuleName = "modulename"; ModuleVersion = "version_number"} or @{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.</span></span>
<span data-ttu-id="4a20e-257">**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-257">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="4a20e-258">您無法在與 *模組* 參數相同的命令中指定 *FullyQualifiedModule* 參數;這兩個參數是互斥的。</span><span class="sxs-lookup"><span data-stu-id="4a20e-258">You cannot specify the *FullyQualifiedModule* parameter in the same command as a *Module* parameter; the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-259">-Module</span><span class="sxs-lookup"><span data-stu-id="4a20e-259">-Module</span></span>
<span data-ttu-id="4a20e-260">指定 Windows PowerShell 嵌入式管理單元和模組中的命令陣列。</span><span class="sxs-lookup"><span data-stu-id="4a20e-260">Specifies and array of commands in the Windows PowerShell snap-ins and modules.</span></span>
<span data-ttu-id="4a20e-261">請輸入嵌入式管理單元和模組名稱。</span><span class="sxs-lookup"><span data-stu-id="4a20e-261">Enter the snap-in and module names.</span></span>
<span data-ttu-id="4a20e-262">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4a20e-262">Wildcards are not permitted.</span></span>

<span data-ttu-id="4a20e-263">匯 **入-PSSession** 無法從嵌入式管理單元匯入提供者。</span><span class="sxs-lookup"><span data-stu-id="4a20e-263">**Import-PSSession** cannot import providers from a snap-in.</span></span>

<span data-ttu-id="4a20e-264">如需詳細資訊，請參閱 about_PSSnapins和 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="4a20e-264">For more information, see about_PSSnapins and [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-265">-前置詞</span><span class="sxs-lookup"><span data-stu-id="4a20e-265">-Prefix</span></span>
<span data-ttu-id="4a20e-266">在匯入的命令名稱中指定名詞的前置詞。</span><span class="sxs-lookup"><span data-stu-id="4a20e-266">Specifies a prefix to the nouns in the names of imported commands.</span></span>

<span data-ttu-id="4a20e-267">使用此參數來避免工作階段中不同命令具有相同名稱時可能會發生的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="4a20e-267">Use this parameter to avoid name conflicts that might occur when different commands in the session have the same name.</span></span>

<span data-ttu-id="4a20e-268">比方說，如果您指定首碼 Remote，然後匯入 Get-Date Cmdlet，則在會話中會將此 Cmdlet 視為成為 get-remotedate，而且不會與原始的 **Get Date** Cmdlet 混淆。</span><span class="sxs-lookup"><span data-stu-id="4a20e-268">For instance, if you specify the prefix Remote and then import a Get-Date cmdlet, the cmdlet is known in the session as Get-RemoteDate, and it is not confused with the original **Get-Date** cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-269">-Session</span><span class="sxs-lookup"><span data-stu-id="4a20e-269">-Session</span></span>
<span data-ttu-id="4a20e-270">指定要從中匯入 Cmdlet 的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="4a20e-270">Specifies the **PSSession** from which the cmdlets are imported.</span></span>
<span data-ttu-id="4a20e-271">輸入包含會話物件的變數，或輸入可取得會話物件的命令，例如 New-PSSession 或 Get-PSSession 命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-271">Enter a variable that contains a session object or a command that gets a session object, such as a New-PSSession or Get-PSSession command.</span></span>
<span data-ttu-id="4a20e-272">您只能指定一個工作階段。</span><span class="sxs-lookup"><span data-stu-id="4a20e-272">You can specify only one session.</span></span>
<span data-ttu-id="4a20e-273">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-273">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a20e-274">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4a20e-274">CommonParameters</span></span>
<span data-ttu-id="4a20e-275">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4a20e-275">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4a20e-276">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4a20e-276">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4a20e-277">輸入</span><span class="sxs-lookup"><span data-stu-id="4a20e-277">INPUTS</span></span>

### <span data-ttu-id="4a20e-278">無</span><span class="sxs-lookup"><span data-stu-id="4a20e-278">None</span></span>
<span data-ttu-id="4a20e-279">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-279">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="4a20e-280">輸出</span><span class="sxs-lookup"><span data-stu-id="4a20e-280">OUTPUTS</span></span>

### <span data-ttu-id="4a20e-281">System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="4a20e-281">System.Management.Automation.PSModuleInfo</span></span>
<span data-ttu-id="4a20e-282">**Import-module** 會傳回 New-Module 和 Get-Module Cmdlet 傳回的相同模組物件。</span><span class="sxs-lookup"><span data-stu-id="4a20e-282">**Import-PSSession** returns the same module object that New-Module and Get-Module cmdlets return.</span></span>
<span data-ttu-id="4a20e-283">不過，匯入的模組是暫時性的，而且只存在於目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="4a20e-283">However, the imported module is temporary and exists only in the current session.</span></span>
<span data-ttu-id="4a20e-284">若要在磁片上建立永久模組，請使用 Export-PSSession Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-284">To create a permanent module on disk, use the Export-PSSession cmdlet.</span></span>

## <span data-ttu-id="4a20e-285">注意</span><span class="sxs-lookup"><span data-stu-id="4a20e-285">NOTES</span></span>

* <span data-ttu-id="4a20e-286">匯 **入-PSSession** 依賴 Windows PowerShell 遠端基礎結構。</span><span class="sxs-lookup"><span data-stu-id="4a20e-286">**Import-PSSession** relies on the Windows PowerShell remoting infrastructure.</span></span> <span data-ttu-id="4a20e-287">若要使用此 Cmdlet，電腦必須設定 WS-Management 遠端執行功能。</span><span class="sxs-lookup"><span data-stu-id="4a20e-287">To use this cmdlet, the computer must be configured for WS-Management remoting.</span></span> <span data-ttu-id="4a20e-288">如需詳細資訊，請參閱 about_Remote 和 about_Remote_Requirements。</span><span class="sxs-lookup"><span data-stu-id="4a20e-288">For more information, see about_Remote and about_Remote_Requirements.</span></span>
* <span data-ttu-id="4a20e-289">匯 **入-PSSession** 不會匯入變數或 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="4a20e-289">**Import-PSSession** does not import variables or Windows PowerShell providers.</span></span>
* <span data-ttu-id="4a20e-290">當您匯入與目前工作階段中具有相同命令名稱的命令時，匯入的命令可以隱藏工作階段中的別名、函式和 Cmdlet，而且可以取代工作階段中的函式和變數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-290">When you import commands that have the same names as commands in the current session, the imported commands can hide aliases, functions, and cmdlets in the session and they can replace functions and variables in the session.</span></span> <span data-ttu-id="4a20e-291">若要避免名稱衝突，請使用 *Prefix* 參數。</span><span class="sxs-lookup"><span data-stu-id="4a20e-291">To prevent name conflicts, use the *Prefix* parameter.</span></span> <span data-ttu-id="4a20e-292">如需詳細資訊，請參閱 about_Command_Precedence。</span><span class="sxs-lookup"><span data-stu-id="4a20e-292">For more information, see about_Command_Precedence.</span></span>
* <span data-ttu-id="4a20e-293">**Import-module** 會先將所有命令轉換成函式，然後再將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="4a20e-293">**Import-PSSession** converts all commands into functions before it imports them.</span></span> <span data-ttu-id="4a20e-294">如此一來，匯入的命令行為會變得與保持其原始命令類型時有點不同。</span><span class="sxs-lookup"><span data-stu-id="4a20e-294">As a result, imported commands behave a bit differently than they would if they retained their original command type.</span></span> <span data-ttu-id="4a20e-295">例如，如果您從 PSSession 匯入 Cmdlet，然後從模組或嵌入式管理單元匯入具有相同名稱的 Cmdlet，則從 PSSession 匯入的命令預設一律都會執行，因為函式優先於 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-295">For example, if you import a cmdlet from a PSSession and then import a cmdlet with the same name from a module or snap-in, the cmdlet that is imported from the PSSession always runs by default because functions take precedence over cmdlets.</span></span> <span data-ttu-id="4a20e-296">相反地，如果您將某個別名匯入具有相同別名名稱的工作階段，則會一律使用原始的別名，因為別名優先於函式。</span><span class="sxs-lookup"><span data-stu-id="4a20e-296">Conversely, if you import an alias into a session that has an alias with the same name, the original alias is always used, because aliases take precedence over functions.</span></span> <span data-ttu-id="4a20e-297">如需詳細資訊，請參閱 about_Command_Precedence。</span><span class="sxs-lookup"><span data-stu-id="4a20e-297">For more information, see about_Command_Precedence.</span></span>
* <span data-ttu-id="4a20e-298">匯 **入-PSSession** 使用 Write-Progress Cmdlet 來顯示命令的進度。</span><span class="sxs-lookup"><span data-stu-id="4a20e-298">**Import-PSSession** uses the Write-Progress cmdlet to display the progress of the command.</span></span> <span data-ttu-id="4a20e-299">當命令執行時，您可以看到進度列。</span><span class="sxs-lookup"><span data-stu-id="4a20e-299">You might see the progress bar while the command is running.</span></span>
* <span data-ttu-id="4a20e-300">若要尋找要匯入的命令， **import-module** 會使用 Invoke-Command Cmdlet 在 PSSession 中執行 Get-Command 命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-300">To find the commands to import, **Import-PSSession** uses the Invoke-Command cmdlet to run a Get-Command command in the PSSession.</span></span> <span data-ttu-id="4a20e-301">為了取得命令的格式設定資料，它會使用 Get-FormatData Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a20e-301">To get formatting data for the commands, it uses the Get-FormatData cmdlet.</span></span> <span data-ttu-id="4a20e-302">當您執行「匯 **入-PSSession** 」命令時，您可能會看到來自這些 Cmdlet 的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4a20e-302">You might see error messages from these cmdlets when you run an **Import-PSSession** command.</span></span> <span data-ttu-id="4a20e-303">此外， **import-module** 無法從不包含 Get 命令、FormatData、Select 物件和 Get-Help Cmdlet 的 PSSession 匯入命令。</span><span class="sxs-lookup"><span data-stu-id="4a20e-303">Also, **Import-PSSession** cannot import commands from a PSSession that does not include the Get-Command, Get-FormatData, Select-Object, and Get-Help cmdlets.</span></span>
* <span data-ttu-id="4a20e-304">匯入的命令與其他遠端命令具有相同的限制，包括無法以使用者介面啟動程式，例如「記事本」。</span><span class="sxs-lookup"><span data-stu-id="4a20e-304">Imported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>
* <span data-ttu-id="4a20e-305">由於 Windows PowerShell 設定檔不是在 PSSession 中執行，因此設定檔新增到工作階段中的命令並無法供 **Import-PSSession** 使用。</span><span class="sxs-lookup"><span data-stu-id="4a20e-305">Because Windows PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to **Import-PSSession** .</span></span> <span data-ttu-id="4a20e-306">若要從設定檔匯入命令，請在匯入命令之前，使用 Invoke-Command 命令在 PSSession 中手動執行設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a20e-306">To import commands from a profile, use an Invoke-Command command to run the profile in the PSSession manually before importing commands.</span></span>
* <span data-ttu-id="4a20e-307">**Import-PSSession** 建立的暫存模組可能會包含格式化檔案，即使命令沒有匯入格式化資料。</span><span class="sxs-lookup"><span data-stu-id="4a20e-307">The temporary module that **Import-PSSession** creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="4a20e-308">如果命令不會匯入格式設定資料，所建立的任何格式檔案都將不會包含格式設定資料。</span><span class="sxs-lookup"><span data-stu-id="4a20e-308">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>
* <span data-ttu-id="4a20e-309">若要使用 **Import-PSSession** ，目前工作階段中的執行原則不能是 Restricted 或 AllSigned，因為 **Import-PSSession** 建立的暫存模組會包含這些原則所禁止的未簽署指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="4a20e-309">To use **Import-PSSession** , the execution policy in the current session cannot be Restricted or AllSigned, because the temporary module that **Import-PSSession** creates contains unsigned script files that are prohibited by these policies.</span></span> <span data-ttu-id="4a20e-310">若要使用匯 **入-PSSession** 而不變更本機電腦的執行原則，請使用 Set-ExecutionPolicy 的 *Scope* 參數，為單一進程設定較不嚴格的執行原則。</span><span class="sxs-lookup"><span data-stu-id="4a20e-310">To use **Import-PSSession** without changing the execution policy for the local computer, use the *Scope* parameter of Set-ExecutionPolicy to set a less restrictive execution policy for a single process.</span></span>
* <span data-ttu-id="4a20e-311">在 Windows PowerShell 2.0 中，從另一個工作階段匯入命令的說明主題不包含您使用 *Prefix* 參數指派的首碼。</span><span class="sxs-lookup"><span data-stu-id="4a20e-311">In Windows PowerShell 2.0, help topics for commands that are imported from another session do not include the prefix that you assign by using the *Prefix* parameter.</span></span> <span data-ttu-id="4a20e-312">若要取得在 Windows PowerShell 2.0 中匯入命令的說明，請使用原始 (未加上首碼) 的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="4a20e-312">To get help for an imported command in Windows PowerShell 2.0, use the original (non-prefixed) command name.</span></span>

## <span data-ttu-id="4a20e-313">相關連結</span><span class="sxs-lookup"><span data-stu-id="4a20e-313">RELATED LINKS</span></span>

[<span data-ttu-id="4a20e-314">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="4a20e-314">Export-PSSession</span></span>](Export-PSSession.md)
