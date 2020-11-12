---
description: 說明如何在遠端電腦上執行工作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 71f59fcb8e656e4ac439028507f15cf36b8402f6
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524921"
---
# <a name="about-remote-jobs"></a>關於遠端作業

## <a name="short-description"></a>簡短描述
說明如何在遠端電腦上執行工作。

## <a name="detailed-description"></a>詳細描述

PowerShell 會透過作業同時執行命令和腳本。 PowerShell 提供三種工作類型來支援平行存取。

- `RemoteJob` -命令和腳本會在遠端會話中執行。
- `BackgroundJob` -命令和腳本會在本機電腦上的個別進程中執行。 如需詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。
- `PSTaskJob` 或 `ThreadJob` -命令和腳本會在本機電腦上相同進程內的個別執行緒中執行。 如需詳細資訊，請參閱 [about_Thread_Jobs](about_Thread_Jobs.md)。

在不同的電腦或個別的進程中遠端執行腳本，可提供絕佳的隔離。 在遠端作業中發生的任何錯誤，都不會影響到其他執行中的作業或啟動作業的父會話。 不過，遠端層會增加額外負荷，包括物件序列化。 所有物件都會進行序列化和還原序列化，因為它們會在父會話和遠端 (作業) 會話之間傳遞。 大型複雜資料物件的序列化可能會耗用大量的計算和記憶體資源，並在網路上傳輸大量資料。

> [!IMPORTANT]
> 建立作業的父會話也會監視作業狀態，並收集管線資料。 當工作達到已完成狀態時，父進程會終止作業子進程。 如果父會話終止，則所有執行中的子工作都會連同其子進程一起終止。

有兩種方法可以解決這種情況：

1. 用 `Invoke-Command` 來建立在已中斷連線的會話中執行的作業。 請參閱本文的卸 [離進程](#how-to-run-as-a-detached-process) 一節。
1. 用 `Start-Process` 來建立新的處理常式，而不是作業。 如需詳細資訊，請參閱 [啟動流程](xref:Microsoft.PowerShell.Management.Start-Process)。

## <a name="remote-jobs"></a>遠端作業

您可以使用三種不同的方法，在遠端電腦上執行工作。

- 在遠端電腦上啟動互動式會話。 然後在互動式會話中啟動工作。 雖然所有動作都是在遠端電腦上執行，但是這些程式與執行本機工作相同。

- 在將其結果傳回本機電腦的遠端電腦上執行工作。 當您想要收集工作的結果，並將其保留在本機電腦上的中央位置時，請使用這個方法。

- 在遠端電腦上執行作業，以在遠端電腦上維護其結果。 當工作資料在原始電腦上更安全地維護時，請使用這個方法。

### <a name="start-a-job-in-an-interactive-session"></a>在互動式會話中啟動工作

您可以啟動遠端電腦的互動式會話，然後在互動式會話期間啟動作業。 如需互動式會話的詳細資訊，請參閱 about_Remote，並參閱 `Enter-PSSession` 。

在互動式會話中啟動作業的程式，與在本機電腦上啟動背景工作的程式幾乎完全相同。 但是，所有作業都會在遠端電腦上執行，而不是在本機電腦上執行。

1. 使用 `Enter-PSSession` Cmdlet 啟動遠端電腦的互動式會話。 您可以使用的 ComputerName 參數 `Enter-PSSession` 來建立互動式會話的暫時連接。 或者，您可以使用 Session 參數，在 PowerShell 會話中執行互動式會話， (PSSession) 。

   下列命令會在 Server01 電腦上啟動互動式會話。

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   命令提示字元會變更，顯示您現在已連線到 Server01 電腦。

   ```
   Server01\C:>
   ```

1. 若要在會話中啟動遠端作業，請使用 `Start-Job` Cmdlet。 下列命令會執行遠端作業，以取得 Server01 電腦上 Windows PowerShell 事件記錄檔中的事件。 `Start-Job`Cmdlet 會傳回代表作業的物件。

   此命令會將工作物件儲存在 `$job` 變數中。

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   當作業執行時，您可以使用互動式會話來執行其他命令，包括其他作業。 不過，您必須讓互動式會話保持開啟，直到工作完成為止。 如果您結束會話，作業將會中斷，且結果會遺失。

1. 若要找出作業是否已完成，請顯示變數的值 `$job` ，或使用 `Get-Job` Cmdlet 來取得工作。 下列命令會使用 `Get-Job` Cmdlet 來顯示工作。

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   `Get-Job`輸出顯示作業在「localhost」電腦上執行，因為工作是在同一部電腦上啟動， (在此案例中為 Server01) 。

1. 若要取得作業的結果，請使用 `Receive-Job` Cmdlet。 您可以在互動式會話中顯示結果，或將結果儲存在遠端電腦上的檔案中。 下列命令會取得 $job 變數中工作的結果。 此命令會使用重新導向操作員 (`>`) 將作業的結果儲存在 Server01 電腦上的 PsLog.txt 檔案中。

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. 若要結束互動式會話，請使用 `Exit-PSSession` Cmdlet。 命令提示字元會變更，顯示您已回到本機電腦上的原始會話。

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. 若要在 Server01 電腦上隨時查看檔案的內容 `PsLog.txt` ，請啟動另一個互動式會話，或執行遠端命令。 如果您想要使用數個命令來調查和管理檔案中的資料，這種類型的命令最適合在 PSSession (持續性連接) 中執行 `PsLog.txt` 。 如需 Pssession 的詳細資訊，請參閱 [about_PSSessions](about_PSSessions.md)。

   下列命令使用指令程式 `New-PSSession` 來建立連線到 Server01 電腦的 **PSSession** ，並使用 `Invoke-Command` 指令程式 `Get-Content` 在 pssession 中執行命令以查看檔案的內容。

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>啟動將結果傳回到本機電腦 (AsJob 的遠端工作) 

若要在將命令結果傳回本機電腦的遠端電腦上啟動作業，請使用 Cmdlet 的 **AsJob** 參數，例如 `Invoke-Command` Cmdlet。

當您使用 **AsJob** 參數時，會實際在本機電腦上建立工作物件，即使工作是在遠端電腦上執行也一樣。 當作業完成時，結果會傳回到本機電腦。

您可以使用包含作業名詞 (工作 Cmdlet) 的 Cmdlet 來管理任何 Cmdlet 所建立的任何作業。 許多具有 **AsJob** 參數的 Cmdlet 都不會使用 PowerShell 遠端功能，因此您甚至可以在未設定為遠端執行且不符合遠端處理需求的電腦上使用它們。

1. 下列命令使用的 **AsJob** 參數，在 `Invoke-Command` Server01 電腦上啟動作業。 作業 `Get-Eventlog` 會執行可取得系統記錄檔中事件的命令。 您可以使用 JobName 參數來指派作業的顯示名稱。

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   命令的結果類似下列範例輸出。

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   使用 **AsJob** 參數時，會傳回 `Invoke-Command` 相同類型的工作物件，該物件會傳回 `Start-Job` 。 您可以將工作物件儲存在變數中，也可以使用 `Get-Job` 命令來取得工作。

   請注意，Location 屬性的值顯示作業已在 Server01 電腦上執行。

1. 若要使用 Cmdlet 的 **AsJob** 參數來管理啟動的作業 `Invoke-Command` ，請使用 job Cmdlet。 因為代表遠端作業的工作物件是在本機電腦上，所以您不需要執行遠端命令來管理作業。

   若要判斷作業是否已完成，請使用 `Get-Job` 命令。 下列命令會取得在目前會話中啟動的所有工作。

   ```powershell
   Get-Job
   ```

   因為遠端作業是在目前的會話中啟動，所以本機 `Get-Job` 命令會取得工作。 工作物件的 State 屬性顯示命令已順利完成。

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. 若要取得作業的結果，請使用 `Receive-Job` Cmdlet。 因為工作結果會自動傳回到工作物件所在的電腦，所以您可以使用本機命令來取得結果 `Receive-Job` 。

   下列命令會使用 `Receive-Job` Cmdlet 來取得工作的結果。 它會使用會話識別碼來識別工作。 此命令會將工作結果儲存在 $results 變數中。 您也可以將結果重新導向至檔案。

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>啟動將結果保留在遠端電腦上的遠端作業

若要在遠端電腦上啟動可將命令結果保留在遠端電腦上的作業，請使用 `Invoke-Command` Cmdlet `Start-Job` 在遠端電腦上執行命令。 您可以使用此方法在多部電腦上執行工作。

當您從遠端執行 `Start-Job` 命令時，會在遠端電腦上建立工作物件，並在遠端電腦上維護工作結果。
從作業的觀點來看，所有作業都是本機的。 您只是在遠端執行命令來管理遠端電腦上的本機作業。

1. 使用 `Invoke-Command` Cmdlet `Start-Job` 在遠端電腦上執行命令。

   此命令需要 PSSession (持續性連接) 。 如果您使用的 ComputerName 參數 `Invoke-Command` 建立暫時連接，則在 `Invoke-Command` 傳回工作物件時，會將該命令視為已完成。 如此一來，就會關閉暫時連接，並取消作業。

   下列命令 `New-PSSession` 會使用 Cmdlet 來建立連線到 Server01 電腦的 PSSession。 此命令會將 PSSession 儲存在 `$s` 變數中。

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   下一個命令會使用 `Invoke-Command` Cmdlet `Start-Job` 在 PSSession 中執行命令。 `Start-Job`命令和 `Get-Eventlog` 命令會以大括弧括住。

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   結果類似下列範例輸出。

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   當您 `Start-Job` 從遠端執行命令時，會傳回 `Invoke-Command` 相同類型的工作物件，該物件會傳回 `Start-Job` 。 您可以將工作物件儲存在變數中，也可以使用 `Get-Job` 命令來取得工作。

   請注意，[ **位置** ] 屬性的值會顯示在本機電腦上執行的作業（稱為 "LocalHost"），即使作業在 Server01 電腦上執行也一樣。 由於工作物件是在 Server01 電腦上建立的，而且工作會在同一部電腦上執行，因此會被視為本機背景工作。

1. 若要管理遠端作業，請使用 **job** Cmdlet。 因為工作物件是在遠端電腦上，所以您需要執行遠端命令以取得、停止、等候或取出工作結果。

   若要查看作業是否已完成，請使用 `Invoke-Command` 命令 `Get-Job` 在連線到 Server01 電腦的 PSSession 中執行命令。

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   命令會傳回工作物件。 工作物件的 **State** 屬性顯示命令已順利完成。

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. 若要取得作業的結果，請使用 `Invoke-Command` `Receive-Job` 指令程式在連接到 Server01 電腦的 PSSession 中執行命令。

   下列命令會使用 `Receive-Job` Cmdlet 來取得工作的結果。 它會使用會話識別碼來識別工作。 此命令會將工作結果儲存在 `$results` 變數中。 它使用的 [保留] 參數 `Receive-Job` ，將結果保留在遠端電腦上的工作快取中。

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   您也可以將結果重新導向至本機或遠端電腦上的檔案。
   下列命令會使用重新導向運算子，將結果儲存在 Server01 電腦上的檔案中。

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a>如何以卸離進程的形式執行

如先前所述，當父會話終止時，所有執行中的子工作都會連同其子進程一起終止。 您可以使用本機電腦上的遠端處理，來執行未附加至目前 PowerShell 會話的作業。

在本機電腦上建立新的 PowerShell 會話。 `Invoke-Command`在此會話中用來啟動作業的。 `Invoke-Command` 可讓您中斷遠端會話的連線，並終止父會話。 稍後，您可以啟動新的 PowerShell 會話，並連接到先前已中斷連線的會話，以繼續監視工作。 不過，當會話終止時，傳回至原始 PowerShell 會話的任何資料都會遺失。 重新連線時，只會傳回中斷連接後所產生的新資料物件。

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

在此範例中，作業仍會附加至父 PowerShell 會話。
不過，父會話不是執行所在的原始 PowerShell 會話 `Invoke-Command` 。

## <a name="see-also"></a>另請參閱

- [about_Jobs](about_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_Remote_Variables](about_Remote_Variables.md)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
