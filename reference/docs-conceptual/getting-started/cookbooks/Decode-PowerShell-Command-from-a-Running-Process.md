---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: 從正在執行的處理序解碼 PowerShell 命令
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619194"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="c2d8f-103">從正在執行的處理序解碼 PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="c2d8f-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="c2d8f-104">有時候，您可能必須執行的處理序佔用大量資源的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="c2d8f-105">無法在內容中執行此程序[工作排程器][]工作或有[SQL Server Agent][]作業。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="c2d8f-106">有多個 PowerShell 處理程序執行，很難知道哪個處理程序表示問題。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="c2d8f-107">這篇文章會示範如何解碼 PowerShell 處理程序目前正在執行的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="c2d8f-108">建立長時間執行的處理程序</span><span class="sxs-lookup"><span data-stu-id="c2d8f-108">Create a long running process</span></span>

<span data-ttu-id="c2d8f-109">為了示範此案例中，開啟新的 PowerShell 視窗並執行下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="c2d8f-110">它會執行的 PowerShell 命令會輸出每分鐘 10 分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="c2d8f-111">檢視處理程序</span><span class="sxs-lookup"><span data-stu-id="c2d8f-111">View the process</span></span>

<span data-ttu-id="c2d8f-112">執行 PowerShell 命令的主體會儲存在**CommandLine**屬性[Win32_Process][]類別。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="c2d8f-113">如果命令[編碼命令][]，則**CommandLine**屬性包含字串"EncodedCommand 」。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="c2d8f-114">使用這項資訊，編碼的命令可以釐清透過下列程序。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="c2d8f-115">以系統管理員身分啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="c2d8f-116">很重要，以系統管理員身分執行 PowerShell，否則會不傳回任何結果時查詢執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="c2d8f-117">執行下列命令來取得所有已編碼的命令的 PowerShell 處理程序：</span><span class="sxs-lookup"><span data-stu-id="c2d8f-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="c2d8f-118">下列命令會建立自訂的 PowerShell 物件，其中包含的處理序識別碼和編碼的命令。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="c2d8f-119">現在可以解碼已編碼的命令。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="c2d8f-120">下列程式碼片段會逐一查看命令的詳細資料物件、 解碼已編碼的命令，和將解碼的命令新增回物件，以便進一步調查。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="c2d8f-121">選取已解碼的 command 屬性現在可以檢閱已解碼的命令。</span><span class="sxs-lookup"><span data-stu-id="c2d8f-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[工作排程器]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[編碼命令]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
