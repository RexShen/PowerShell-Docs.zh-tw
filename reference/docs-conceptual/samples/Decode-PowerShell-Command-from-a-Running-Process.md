---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: 從正在執行的處理序解碼 PowerShell 命令
author: randomnote1
description: 此文章會說明如何將正在執行 PowerShell 處理序的指令碼區塊解碼。
ms.openlocfilehash: 95b4b806665bf8137712ebb183329039bc1e1deb
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500482"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="491f7-104">從正在執行的處理序解碼 PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="491f7-104">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="491f7-105">您有時候可能會執行耗用大量資源的 PowerShell 處理序。</span><span class="sxs-lookup"><span data-stu-id="491f7-105">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="491f7-106">此處理序可在[工作排程器][]作業或 [SQL Server Agent][] 作業的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="491f7-106">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="491f7-107">有多個 PowerShell 處理序執行時，很難知道哪一個處理序發生問題。</span><span class="sxs-lookup"><span data-stu-id="491f7-107">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="491f7-108">此文章會說明如何將正在執行 PowerShell 處理序的指令碼區塊解碼。</span><span class="sxs-lookup"><span data-stu-id="491f7-108">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="491f7-109">建立長時間執行的處理序</span><span class="sxs-lookup"><span data-stu-id="491f7-109">Create a long running process</span></span>

<span data-ttu-id="491f7-110">為了示範此案例，請開啟一個新的 PowerShell 視窗並執行以下程式碼。</span><span class="sxs-lookup"><span data-stu-id="491f7-110">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="491f7-111">它會執行一個每分鐘輸出一個數字的 PowerShell 命令，並執行 10 分鐘。</span><span class="sxs-lookup"><span data-stu-id="491f7-111">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

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

## <a name="view-the-process"></a><span data-ttu-id="491f7-112">檢視處理序</span><span class="sxs-lookup"><span data-stu-id="491f7-112">View the process</span></span>

<span data-ttu-id="491f7-113">正在執行 PowerShell 的命令主體會儲存在 [Win32_Process][] 類別的 **CommandLine** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="491f7-113">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="491f7-114">如果命令是編碼命令， **CommandLine** 屬性就會包含 "EncodedCommand" 字串。</span><span class="sxs-lookup"><span data-stu-id="491f7-114">If the command is an encoded command, the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="491f7-115">只要透過以下程序使用此資訊，就能識別編碼命令。</span><span class="sxs-lookup"><span data-stu-id="491f7-115">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="491f7-116">以系統管理員身分啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="491f7-116">Start PowerShell as Administrator.</span></span> <span data-ttu-id="491f7-117">這很重要，PowerShell 必須以系統管理員身分執行，否則在查詢執行的處理序時不會傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="491f7-117">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="491f7-118">執行以下命令來取得具有編碼命令的所有 PowerShell 處理序：</span><span class="sxs-lookup"><span data-stu-id="491f7-118">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="491f7-119">以下命令會建立包含處理序識別碼和編碼命令的自訂 PowerShell 物件。</span><span class="sxs-lookup"><span data-stu-id="491f7-119">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

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

<span data-ttu-id="491f7-120">現在可以將編碼命令解碼了。</span><span class="sxs-lookup"><span data-stu-id="491f7-120">Now the encoded command can be decoded.</span></span> <span data-ttu-id="491f7-121">以下程式碼片段會逐一查看命令的詳細資料物件、將編碼命令解碼，以及將解碼後的命令新增回物件，以便進一步調查。</span><span class="sxs-lookup"><span data-stu-id="491f7-121">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

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

<span data-ttu-id="491f7-122">現在可以透過選取解碼命令屬性來檢閱解碼後的命令。</span><span class="sxs-lookup"><span data-stu-id="491f7-122">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```Output
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
