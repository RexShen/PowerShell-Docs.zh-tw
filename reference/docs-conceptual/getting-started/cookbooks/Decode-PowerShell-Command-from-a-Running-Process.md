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
# <a name="decode-a-powershell-command-from-a-running-process"></a>從正在執行的處理序解碼 PowerShell 命令

有時候，您可能必須執行的處理序佔用大量資源的 PowerShell。
無法在內容中執行此程序[工作排程器][]工作或有[SQL Server Agent][]作業。 有多個 PowerShell 處理程序執行，很難知道哪個處理程序表示問題。 這篇文章會示範如何解碼 PowerShell 處理程序目前正在執行的指令碼區塊。

## <a name="create-a-long-running-process"></a>建立長時間執行的處理程序

為了示範此案例中，開啟新的 PowerShell 視窗並執行下列程式碼。 它會執行的 PowerShell 命令會輸出每分鐘 10 分鐘的時間。

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

## <a name="view-the-process"></a>檢視處理程序

執行 PowerShell 命令的主體會儲存在**CommandLine**屬性[Win32_Process][]類別。 如果命令[編碼命令][]，則**CommandLine**屬性包含字串"EncodedCommand 」。 使用這項資訊，編碼的命令可以釐清透過下列程序。

以系統管理員身分啟動 PowerShell。 很重要，以系統管理員身分執行 PowerShell，否則會不傳回任何結果時查詢執行的處理序。

執行下列命令來取得所有已編碼的命令的 PowerShell 處理程序：

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

下列命令會建立自訂的 PowerShell 物件，其中包含的處理序識別碼和編碼的命令。

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

現在可以解碼已編碼的命令。 下列程式碼片段會逐一查看命令的詳細資料物件、 解碼已編碼的命令，和將解碼的命令新增回物件，以便進一步調查。

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

選取已解碼的 command 屬性現在可以檢閱已解碼的命令。

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
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[編碼命令]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
