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
# <a name="decode-a-powershell-command-from-a-running-process"></a>從正在執行的處理序解碼 PowerShell 命令

您有時候可能會執行耗用大量資源的 PowerShell 處理序。
此處理序可在[工作排程器][]作業或 [SQL Server Agent][] 作業的內容中執行。 有多個 PowerShell 處理序執行時，很難知道哪一個處理序發生問題。 此文章會說明如何將正在執行 PowerShell 處理序的指令碼區塊解碼。

## <a name="create-a-long-running-process"></a>建立長時間執行的處理序

為了示範此案例，請開啟一個新的 PowerShell 視窗並執行以下程式碼。 它會執行一個每分鐘輸出一個數字的 PowerShell 命令，並執行 10 分鐘。

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

## <a name="view-the-process"></a>檢視處理序

正在執行 PowerShell 的命令主體會儲存在 [Win32_Process][] 類別的 **CommandLine** 屬性中。 如果命令是編碼命令， **CommandLine** 屬性就會包含 "EncodedCommand" 字串。 只要透過以下程序使用此資訊，就能識別編碼命令。

以系統管理員身分啟動 PowerShell。 這很重要，PowerShell 必須以系統管理員身分執行，否則在查詢執行的處理序時不會傳回任何結果。

執行以下命令來取得具有編碼命令的所有 PowerShell 處理序：

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

以下命令會建立包含處理序識別碼和編碼命令的自訂 PowerShell 物件。

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

現在可以將編碼命令解碼了。 以下程式碼片段會逐一查看命令的詳細資料物件、將編碼命令解碼，以及將解碼後的命令新增回物件，以便進一步調查。

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

現在可以透過選取解碼命令屬性來檢閱解碼後的命令。

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
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
