---
description: 說明如何在遠端電腦上執行背景工作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: fb2270ea5c0acdcf2c506e687787d22c73e2cb2c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207731"
---
# <a name="about-remote-jobs"></a>關於遠端作業

## <a name="short-description"></a>簡短描述
說明如何在遠端電腦上執行背景工作。

## <a name="detailed-description"></a>詳細描述

背景工作是非同步執行的命令，而不會與目前的會話互動。 命令提示字元會立即傳回，而您可以在作業執行時繼續使用會話。

根據預設，背景工作會在本機電腦上執行。 不過，您可以使用數個不同的程式，在遠端電腦上執行背景工作。

本主題說明如何在遠端電腦上執行背景工作。 如需有關如何在本機電腦上執行背景工作的詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。 如需背景工作的詳細資訊，請參閱 [about_Job_Details](about_Job_Details.md)。

## <a name="remote-background-jobs"></a>遠端背景工作

您可以使用三種不同的方法，在遠端電腦上執行背景工作。

- 啟動遠端電腦的互動式會話，並在互動式會話中啟動工作。 雖然所有動作都是在遠端電腦上執行，但是這些程式與執行本機工作相同。

- 在將其結果傳回本機電腦的遠端電腦上執行背景工作。 當您想要收集背景工作的結果，並將其保留在本機電腦上的中央位置時，請使用這個方法。

- 在遠端電腦上執行背景工作，以在遠端電腦上維護其結果。 當工作資料在原始電腦上更安全地維護時，請使用這個方法。

### <a name="start-a-background-job-in-an-interactive-session"></a>在互動式會話中啟動背景工作

您可以啟動遠端電腦的互動式會話，然後在互動式會話期間啟動背景工作。 如需互動式會話的詳細資訊，請參閱 about_Remote，並查看輸入 PSSession。

在互動式會話中啟動背景工作的程式，與在本機電腦上啟動背景工作的程式幾乎完全相同。 但是，所有作業都會在遠端電腦上執行，而不是在本機電腦上執行。

#### <a name="step-1-enter-pssession"></a>步驟1：輸入-PSSESSION

使用 Enter-PSSession Cmdlet 來啟動遠端電腦的互動式會話。 您可以使用 Enter-PSSession 的 ComputerName 參數來建立互動式會話的暫時連接。 或者，您可以使用 Session 參數，在 PowerShell 會話中執行互動式會話， (PSSession) 。

下列命令會在 Server01 電腦上啟動互動式會話。

```powershell
C:\PS> Enter-PSSession -computername Server01
```

命令提示字元會變更，顯示您現在已連線到 Server01 電腦。

```
Server01\C:>
```

#### <a name="step-2-start-job"></a>步驟2：啟動-作業

若要在會話中啟動背景工作，請使用 Start-Job Cmdlet。

下列命令會執行背景工作，以取得 Server01 電腦上 Windows PowerShell 事件記錄檔中的事件。 Start-Job Cmdlet 會傳回代表作業的物件。

此命令會將工作物件儲存在 \$ 工作變數中。

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

當作業執行時，您可以使用互動式會話來執行其他命令，包括其他背景工作。 不過，您必須讓互動式會話保持開啟，直到工作完成為止。 如果您結束會話，作業將會中斷，且結果會遺失。

#### <a name="step-3-get-job"></a>步驟3：取得-作業

若要找出作業是否已完成，請顯示 \$ 工作變數的值，或使用 Get-Job Cmdlet 取得工作。 下列命令使用 Get-Job Cmdlet 來顯示工作。

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

Get-Job 輸出顯示作業正在 "localhost" 電腦上執行，因為工作是在同一部電腦上啟動，而且在相同的電腦上執行 (在此案例中為 Server01) 。

#### <a name="step-4-receive-job"></a>步驟4：接收作業

若要取得作業的結果，請使用 Receive-Job Cmdlet。 您可以在互動式會話中顯示結果，或將結果儲存在遠端電腦上的檔案中。 下列命令會取得 $job 變數中工作的結果。 此命令會使用重新導向操作員 ( # A0) 將作業的結果儲存在 Server01 電腦上的 PsLog.txt 檔案中。

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a>步驟5： EXIT-PSSESSION

若要結束互動式會話，請使用 Exit-PSSession Cmdlet。 命令提示字元會變更，顯示您已回到本機電腦上的原始會話。

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a>步驟6： INVOKE-COMMAND： GET-CONTENT

若要在 Server01 電腦上隨時查看 PsLog.txt 檔案的內容，請啟動另一個互動式會話，或執行遠端命令。 如果您想要使用數個命令來調查和管理 PsLog.txt 檔中的資料，這種類型的命令最適合在 PSSession (持續性連接) 中執行。 如需 Pssession 的詳細資訊，請參閱 about_PSSessions。

下列命令使用 New-PSSession Cmdlet 來建立連線到 Server01 電腦的 PSSession，並使用 Invoke-Command Cmdlet 在 PSSession 中執行 Get-Content 命令以查看檔案的內容。

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>啟動將結果傳回到本機電腦 ASJOB 的遠端作業 \(\)

若要在將命令結果傳回本機電腦的遠端電腦上啟動背景工作，請使用 Cmdlet 的 AsJob 參數，例如 Invoke-Command Cmdlet。

當您使用 AsJob 參數時，會實際在本機電腦上建立工作物件，即使工作是在遠端電腦上執行也一樣。 當作業完成時，結果會傳回到本機電腦。

您可以使用包含作業名詞 (工作 Cmdlet) 的 Cmdlet 來管理任何 Cmdlet 所建立的任何作業。 許多具有 AsJob 參數的 Cmdlet 都不會使用 PowerShell 遠端功能，因此您甚至可以在未設定為遠端執行且不符合遠端處理需求的電腦上使用它們。

#### <a name="step-1-invoke-command--asjob"></a>步驟1：調用-命令-ASJOB

下列命令使用 Invoke-Command 的 AsJob 參數，在 Server01 電腦上啟動背景工作。 此工作會執行取得系統記錄檔中之事件的 Get-Eventlog 命令。 您可以使用 JobName 參數來指派作業的顯示名稱。

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

命令的結果類似下列範例輸出。

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

使用 AsJob 參數時，Invoke-Command 會傳回 Start-Job 傳回的相同工作物件類型。 您可以將工作物件儲存在變數中，也可以使用 Get-Job 命令來取得工作。

請注意，Location 屬性的值顯示作業已在 Server01 電腦上執行。

#### <a name="step-2-get-job"></a>步驟2：取得-作業

若要管理使用 Invoke-Command Cmdlet 的 AsJob 參數啟動的工作，請使用 Job Cmdlet。 因為代表遠端作業的工作物件是在本機電腦上，所以您不需要執行遠端命令來管理作業。

若要判斷作業是否已完成，請使用 Get-Job 命令。 下列命令會取得在目前會話中啟動的所有工作。

```powershell
get-job
```

因為遠端作業是在目前會話中啟動，所以本機 Get-Job 命令會取得工作。 工作物件的 State 屬性顯示命令已順利完成。

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a>步驟3：接收作業

若要取得作業的結果，請使用 Receive-Job Cmdlet。 因為工作結果會自動傳回到工作物件所在的電腦，所以您可以使用本機 Receive-Job 命令取得結果。

下列命令使用 Receive-Job Cmdlet 取得工作的結果。 它會使用會話識別碼來識別工作。 此命令會將工作結果儲存在 $results 變數中。 您也可以將結果重新導向至檔案。

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>啟動將結果保留在遠端電腦上的遠端作業

若要在遠端電腦上啟動背景工作，以在遠端電腦上保存命令結果，請使用 Invoke-Command Cmdlet 在遠端電腦上執行 Start-Job 命令。 您可以使用此方法在多部電腦上執行背景工作。

當您從遠端執行 Start-Job 命令時，會在遠端電腦上建立工作物件，並在遠端電腦上維護工作結果。
從作業的觀點來看，所有作業都是本機的。 您只是在遠端執行命令來管理遠端電腦上的本機作業。

#### <a name="step-1-invoke-command-start-job"></a>步驟1： INVOKE-命令啟動-作業

使用 Invoke-Command Cmdlet 在遠端電腦上執行 Start-Job 命令。

此命令需要 PSSession (持續性連接) 。 如果您使用 Invoke-Command 的 ComputerName 參數來建立暫時連接，則在傳回工作物件時，Invoke-Command 命令會被視為已完成。 如此一來，就會關閉暫時連接，並取消作業。

下列命令使用 New-PSSession Cmdlet 來建立連線到 Server01 電腦的 PSSession。 命令會將 PSSession 儲存在 \$ s 變數中。

```powershell
$s = new-pssession -computername Server01
```

下一個命令會使用 Invoke-Command Cmdlet 在 PSSession 中執行 Start-Job 命令。 Start-Job 命令和 Get-Eventlog 命令會以大括弧括住。

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

結果類似下列範例輸出。

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

當您從遠端執行 Start-Job 命令時，Invoke-Command 會傳回 Start-Job 傳回的相同工作物件類型。 您可以將工作物件儲存在變數中，也可以使用 Get-Job 命令來取得工作。

請注意，[位置] 屬性的值會顯示在本機電腦上執行的作業（稱為 "LocalHost"），即使作業在 Server01 電腦上執行也一樣。 由於工作物件是在 Server01 電腦上建立的，而且工作會在同一部電腦上執行，因此會被視為本機背景工作。

#### <a name="step-2-invoke-command-get-job"></a>步驟2：叫用-命令 GET-JOB

若要管理遠端背景工作，請使用 Job Cmdlet。 因為工作物件是在遠端電腦上，所以您需要執行遠端命令以取得、停止、等候或取出工作結果。

若要查看作業是否已完成，請使用 Invoke-Command 命令，在連線到 Server01 電腦的 PSSession 中執行 Get-Job 命令。

```powershell
invoke-command -session $s -scriptblock {get-job}
```

命令會傳回工作物件。 工作物件的 State 屬性顯示命令已順利完成。

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a>步驟3：調用-命令接收-作業

若要取得工作的結果，請使用 Invoke-Command Cmdlet，在連線到 Server01 電腦的 PSSession 中執行 Receive-Job 命令。

下列命令使用 Receive-Job Cmdlet 取得工作的結果。 它會使用會話識別碼來識別工作。 此命令會將工作結果儲存在 \$ 結果變數中。 它使用 Receive-Job 的 Keep 參數，將結果保留在遠端電腦上的工作快取中。

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

您也可以將結果重新導向至本機或遠端電腦上的檔案。
下列命令會使用重新導向運算子，將結果儲存在 Server01 電腦上的檔案中。

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a>另請參閱

[about_Jobs](about_Jobs.md)

[about_Job_Details](about_Job_Details.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)

[Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)

[Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)

[Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)

[Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

