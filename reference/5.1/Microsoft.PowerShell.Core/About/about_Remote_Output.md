---
description: 說明如何解讀遠端命令的輸出並設定其格式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: c5636a301017111adf97b6332237e737b4bf0716
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207924"
---
# <a name="about-remote-output"></a><span data-ttu-id="30df7-104">關於遠端輸出</span><span class="sxs-lookup"><span data-stu-id="30df7-104">About Remote Output</span></span>

## <a name="short-description"></a><span data-ttu-id="30df7-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="30df7-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="30df7-106">說明如何解讀遠端命令的輸出並設定其格式。</span><span class="sxs-lookup"><span data-stu-id="30df7-106">Describes how to interpret and format the output of remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="30df7-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="30df7-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="30df7-108">在遠端電腦上執行之命令的輸出看起來可能像是在本機電腦上執行相同命令的輸出，但是有一些重大差異。</span><span class="sxs-lookup"><span data-stu-id="30df7-108">The output of a command that was run on a remote computer might look like output of the same command run on a local computer, but there are some significant differences.</span></span>

<span data-ttu-id="30df7-109">本主題說明如何解讀、格式化和顯示在遠端電腦上執行之命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="30df7-109">This topic explains how to interpret, format, and display the output of commands that are run on remote computers.</span></span>

## <a name="displaying-the-computer-name"></a><span data-ttu-id="30df7-110">顯示電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="30df7-110">DISPLAYING THE COMPUTER NAME</span></span>

<span data-ttu-id="30df7-111">當您使用 Invoke-Command Cmdlet 在遠端電腦上執行命令時，此命令會傳回物件，其中包含產生資料的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="30df7-111">When you use the Invoke-Command cmdlet to run a command on a remote computer, the command returns an object that includes the name of the computer that generated the data.</span></span> <span data-ttu-id="30df7-112">遠端電腦名稱稱會儲存在 PSComputerName 屬性中。</span><span class="sxs-lookup"><span data-stu-id="30df7-112">The remote computer name is stored in the PSComputerName property.</span></span>

<span data-ttu-id="30df7-113">針對許多命令，預設會顯示 PSComputerName。</span><span class="sxs-lookup"><span data-stu-id="30df7-113">For many commands, the PSComputerName is displayed by default.</span></span> <span data-ttu-id="30df7-114">例如，下列命令會在兩部遠端電腦（Server01 和 Server02）上執行 Get-Culture 命令。</span><span class="sxs-lookup"><span data-stu-id="30df7-114">For example, the following command runs a Get-Culture command on two remote computers, Server01 and Server02.</span></span> <span data-ttu-id="30df7-115">輸出（如下所示）包含命令執行所在的遠端電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="30df7-115">The output, which appears below, includes the names of the remote computers on which the command ran.</span></span>

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

<span data-ttu-id="30df7-116">您可以使用 Invoke-Command 的 HideComputerName 參數來隱藏 PSComputerName 屬性。</span><span class="sxs-lookup"><span data-stu-id="30df7-116">You can use the HideComputerName parameter of Invoke-Command to hide the PSComputerName property.</span></span> <span data-ttu-id="30df7-117">此參數是針對只從一部遠端電腦收集資料的命令所設計。</span><span class="sxs-lookup"><span data-stu-id="30df7-117">This parameter is designed for commands that collect data from only one remote computer.</span></span>

<span data-ttu-id="30df7-118">下列命令會在 Server01 遠端電腦上執行 Get-Culture 命令。</span><span class="sxs-lookup"><span data-stu-id="30df7-118">The following command runs a Get-Culture command on the Server01 remote computer.</span></span> <span data-ttu-id="30df7-119">它會使用 HideComputerName 參數來隱藏 PSComputerName 屬性和相關屬性。</span><span class="sxs-lookup"><span data-stu-id="30df7-119">It uses the HideComputerName parameter to hide the PSComputerName property and related properties.</span></span>

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="30df7-120">您也可以顯示 [PSComputerName] 屬性（如果預設未顯示）。</span><span class="sxs-lookup"><span data-stu-id="30df7-120">You can also display the PSComputerName property if it is not displayed by default.</span></span>

<span data-ttu-id="30df7-121">例如，下列命令會使用 Format-Table Cmdlet，將 PSComputerName 屬性新增至遠端 Get-Date 命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="30df7-121">For example, the following commands use the Format-Table cmdlet to add the PSComputerName property to the output of a remote Get-Date command.</span></span>

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a><span data-ttu-id="30df7-122">顯示 MACHINENAME 屬性</span><span class="sxs-lookup"><span data-stu-id="30df7-122">DISPLAYING THE MACHINENAME PROPERTY</span></span>

<span data-ttu-id="30df7-123">數個指令程式（包括 Get 進程、Get-help 和 Get-help）都有 ComputerName 參數，可取得遠端電腦上的物件。</span><span class="sxs-lookup"><span data-stu-id="30df7-123">Several cmdlets, including Get-Process, Get-Service, and Get-EventLog, have a ComputerName parameter that gets the objects on a remote computer.</span></span>
<span data-ttu-id="30df7-124">這些 Cmdlet 不會使用 Windows PowerShell 遠端功能，因此您甚至可以在未設定為在 Windows PowerShell 中進行遠端處理的電腦上使用它們。</span><span class="sxs-lookup"><span data-stu-id="30df7-124">These cmdlets do not use Windows PowerShell remoting, so you can use them even on computers that are not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="30df7-125">這些 Cmdlet 傳回的物件會將遠端電腦的名稱儲存在 MachineName 屬性中。</span><span class="sxs-lookup"><span data-stu-id="30df7-125">The objects that these cmdlets return store the name of the remote computer in the MachineName property.</span></span> <span data-ttu-id="30df7-126"> (這些物件沒有 PSComputerName 屬性。 ) </span><span class="sxs-lookup"><span data-stu-id="30df7-126">(These objects do not have a PSComputerName property.)</span></span>

<span data-ttu-id="30df7-127">例如，此命令會取得 Server01 和 Server02 遠端電腦上的 PowerShell 處理常式。</span><span class="sxs-lookup"><span data-stu-id="30df7-127">For example, this command gets the PowerShell process on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="30df7-128">預設顯示不包含 MachineName 屬性。</span><span class="sxs-lookup"><span data-stu-id="30df7-128">The default display does not include the MachineName property.</span></span>

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

<span data-ttu-id="30df7-129">您可以使用 Format-Table Cmdlet 顯示處理常式物件的 MachineName 屬性。</span><span class="sxs-lookup"><span data-stu-id="30df7-129">You can use the Format-Table cmdlet to display the MachineName property of the process objects.</span></span>

<span data-ttu-id="30df7-130">例如，下列命令會將處理常式儲存在 $p 變數中，然後使用管線運算子 (|) 將 $p 中的處理常式傳送至 Format-Table 命令。</span><span class="sxs-lookup"><span data-stu-id="30df7-130">For example, the following command saves the processes in the $p variable and then uses a pipeline operator (|) to send the processes in $p to the Format-Table command.</span></span> <span data-ttu-id="30df7-131">命令使用 Format-Table 的 Property 參數將 MachineName 屬性包含在顯示中。</span><span class="sxs-lookup"><span data-stu-id="30df7-131">The command uses the Property parameter of Format-Table to include the MachineName property in the display.</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

<span data-ttu-id="30df7-132">下列更複雜的命令會將 MachineName 屬性新增至預設進程顯示。</span><span class="sxs-lookup"><span data-stu-id="30df7-132">The following more complex command adds the MachineName property to the default process display.</span></span> <span data-ttu-id="30df7-133">它會使用雜湊表來指定計算屬性。</span><span class="sxs-lookup"><span data-stu-id="30df7-133">It uses hash tables to specify calculated properties.</span></span> <span data-ttu-id="30df7-134">幸運的是，您不需要瞭解它的使用方式。</span><span class="sxs-lookup"><span data-stu-id="30df7-134">Fortunately, you do not have to understand it to use it.</span></span>

<span data-ttu-id="30df7-135"> (請注意，倒引號 ['] 是接續字元。 ) </span><span class="sxs-lookup"><span data-stu-id="30df7-135">(Note that the backtick [\`] is the continuation character.)</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a><span data-ttu-id="30df7-136">還原序列化的物件</span><span class="sxs-lookup"><span data-stu-id="30df7-136">DESERIALIZED OBJECTS</span></span>

<span data-ttu-id="30df7-137">當您執行會產生輸出的遠端命令時，命令輸出會在網路上傳輸回本機電腦。</span><span class="sxs-lookup"><span data-stu-id="30df7-137">When you run remote commands that generate output, the command output is transmitted across the network back to the local computer.</span></span>

<span data-ttu-id="30df7-138">因為大部分的即時 Microsoft .NET Framework 物件 (例如 Windows PowerShell Cmdlet 傳回的物件) 無法透過網路傳輸，所以即時物件會「序列化」。</span><span class="sxs-lookup"><span data-stu-id="30df7-138">Because most live Microsoft .NET Framework objects (such as the objects that Windows PowerShell cmdlets return) cannot be transmitted over the network, the live objects are "serialized".</span></span> <span data-ttu-id="30df7-139">換句話說，即時物件會轉換成物件和其屬性的 XML 標記法。</span><span class="sxs-lookup"><span data-stu-id="30df7-139">In other words, the live objects are converted into XML representations of the object and its properties.</span></span> <span data-ttu-id="30df7-140">然後，會在網路上傳輸以 XML 為基礎的序列化物件。</span><span class="sxs-lookup"><span data-stu-id="30df7-140">Then, the XML-based serialized object is transmitted across the network.</span></span>

<span data-ttu-id="30df7-141">在本機電腦上，Windows PowerShell 會接收以 xml 為基礎的序列化物件，並將 XML 型物件轉換成標準的 .NET Framework 物件，以將它「還原序列化」。</span><span class="sxs-lookup"><span data-stu-id="30df7-141">On the local computer, Windows PowerShell receives the XML-based serialized object and "deserializes" it by converting the XML-based object into a standard .NET Framework object.</span></span>

<span data-ttu-id="30df7-142">不過，已還原序列化的物件不是即時物件。</span><span class="sxs-lookup"><span data-stu-id="30df7-142">However, the deserialized object is not a live object.</span></span> <span data-ttu-id="30df7-143">它是物件在序列化時的快照集，而且包含屬性，但不包含任何方法。</span><span class="sxs-lookup"><span data-stu-id="30df7-143">It is a snapshot of the object at the time that it was serialized, and it includes properties but no methods.</span></span> <span data-ttu-id="30df7-144">您可以在 Windows PowerShell 中使用和管理這些物件，包括在管線中傳遞這些物件、顯示選取的屬性，以及將它們格式化。</span><span class="sxs-lookup"><span data-stu-id="30df7-144">You can use and manage these objects in Windows PowerShell, including passing them in pipelines, displaying selected properties, and formatting them.</span></span>

<span data-ttu-id="30df7-145">大部分還原序列化的物件都會自動格式化，以依 Types.ps1xml 或 Format.ps1xml 檔案中的專案顯示。</span><span class="sxs-lookup"><span data-stu-id="30df7-145">Most deserialized objects are automatically formatted for display by entries in the Types.ps1xml or Format.ps1xml files.</span></span> <span data-ttu-id="30df7-146">不過，本機電腦可能沒有在遠端電腦上產生的所有已還原序列化物件的格式檔案。</span><span class="sxs-lookup"><span data-stu-id="30df7-146">However, the local computer might not have formatting files for all of the deserialized objects that were generated on a remote computer.</span></span> <span data-ttu-id="30df7-147">當物件未格式化時，每個物件的所有屬性都會出現在主控台的串流清單中。</span><span class="sxs-lookup"><span data-stu-id="30df7-147">When objects are not formatted, all of the properties of each object appear in the console in a streaming list.</span></span>

<span data-ttu-id="30df7-148">當物件未自動格式化時，您可以使用格式化 Cmdlet （例如 Format-Table 或格式清單）來格式化和顯示選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="30df7-148">When objects are not formatted automatically, you can use the formatting cmdlets, such as Format-Table or Format-List, to format and display selected properties.</span></span> <span data-ttu-id="30df7-149">或者，您可以使用 Out-GridView Cmdlet，在資料表中顯示物件。</span><span class="sxs-lookup"><span data-stu-id="30df7-149">Or, you can use the Out-GridView cmdlet to display the objects in a table.</span></span>

<span data-ttu-id="30df7-150">此外，如果您在使用本機電腦上沒有指令程式的遠端電腦上執行命令，命令傳回的物件可能無法正確格式化，因為您的電腦上沒有這些物件的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="30df7-150">Also, if you run a command on a remote computer that uses cmdlets that you do not have on your local computer, the objects that the command returns might not be formatted properly because you do not have the formatting files for those objects on your computer.</span></span> <span data-ttu-id="30df7-151">若要從另一部電腦取得格式設定資料，請使用 Get-FormatData 和 Export-FormatData Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30df7-151">To get formatting data from another computer, use the Get-FormatData and Export-FormatData cmdlets.</span></span>

<span data-ttu-id="30df7-152">某些物件類型（例如 DirectoryInfo 物件和 Guid）會在收到時轉換回即時物件。</span><span class="sxs-lookup"><span data-stu-id="30df7-152">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="30df7-153">這些物件不需要任何特殊處理或格式化。</span><span class="sxs-lookup"><span data-stu-id="30df7-153">These objects do not need any special handling or formatting.</span></span>

## <a name="ordering-the-results"></a><span data-ttu-id="30df7-154">排序結果</span><span class="sxs-lookup"><span data-stu-id="30df7-154">ORDERING THE RESULTS</span></span>

<span data-ttu-id="30df7-155">指令程式的 ComputerName 參數中電腦名稱稱的順序會決定 Windows PowerShell 連接到遠端電腦的順序。</span><span class="sxs-lookup"><span data-stu-id="30df7-155">The order of the computer names in the ComputerName parameter of cmdlets determines the order in which Windows PowerShell connects to the remote computers.</span></span> <span data-ttu-id="30df7-156">不過，結果會以本機電腦接收的順序顯示，可能是不同的順序。</span><span class="sxs-lookup"><span data-stu-id="30df7-156">However, the results appear in the order in which the local computer receives them, which might be a different order.</span></span>

<span data-ttu-id="30df7-157">若要變更結果的順序，請使用 Sort-Object Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30df7-157">To change the order of the results, use the Sort-Object cmdlet.</span></span> <span data-ttu-id="30df7-158">您可以針對 PSComputerName 或 MachineName 屬性進行排序。</span><span class="sxs-lookup"><span data-stu-id="30df7-158">You can sort on the PSComputerName or MachineName property.</span></span> <span data-ttu-id="30df7-159">您也可以在物件的其他屬性上進行排序，以便讓不同電腦的結果分開。</span><span class="sxs-lookup"><span data-stu-id="30df7-159">You can also sort on another property of the object so that the results from different computers are interspersed.</span></span>

## <a name="see-also"></a><span data-ttu-id="30df7-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30df7-160">SEE ALSO</span></span>

[<span data-ttu-id="30df7-161">about_Remote</span><span class="sxs-lookup"><span data-stu-id="30df7-161">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="30df7-162">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="30df7-162">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="30df7-163">Format-Table</span><span class="sxs-lookup"><span data-stu-id="30df7-163">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="30df7-164">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="30df7-164">Get-EventLog</span></span>](xref:Microsoft.PowerShell.Management.Get-EventLog)

[<span data-ttu-id="30df7-165">Get-Process</span><span class="sxs-lookup"><span data-stu-id="30df7-165">Get-Process</span></span>](xref:Microsoft.PowerShell.Management.Get-Process)

[<span data-ttu-id="30df7-166">Get-Service</span><span class="sxs-lookup"><span data-stu-id="30df7-166">Get-Service</span></span>](xref:Microsoft.PowerShell.Management.Get-Service)

[<span data-ttu-id="30df7-167">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="30df7-167">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="30df7-168">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="30df7-168">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="30df7-169">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="30df7-169">Out-GridView</span></span>](xref:Microsoft.PowerShell.Utility.Out-GridView)

[<span data-ttu-id="30df7-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="30df7-170">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)
