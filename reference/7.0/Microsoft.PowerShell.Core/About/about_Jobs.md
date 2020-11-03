---
description: 提供有關 PowerShell 背景工作如何在背景中執行命令或運算式的資訊，而不需與目前的會話互動。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 838e142fe39260b759e9a44c6d69b80d3c5b293e
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208603"
---
# <a name="about-jobs"></a>關於工作

## <a name="short-description"></a>簡短描述
提供有關 PowerShell 背景工作如何在背景中執行命令或運算式的資訊，而不需與目前的會話互動。

## <a name="long-description"></a>完整描述

PowerShell 會透過作業同時執行命令和腳本。 PowerShell 提供三個以工作為基礎的解決方案，以支援平行存取。

|工作 (Job)            |Description                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |命令和腳本會在遠端電腦上執行。                 |
|`BackgroundJob`|命令和腳本在本機的個別進程中執行    |
|               |新的虛擬主機。                                                     |
|`ThreadJob`    |命令和腳本在相同的執行緒中執行  |
|               |在本機電腦上處理。                                |

每種類型的作業都有其優點和缺點。 在不同的電腦上或在個別的進程中遠端執行腳本有很大的隔離。 任何錯誤都不會影響其他執行中的工作或啟動作業的用戶端。 但是遠端層會增加額外負荷，包括物件序列化。 在遠端會話中傳遞的所有物件都必須序列化，然後在用戶端與目標會話之間傳遞時還原序列化。 序列化作業可以針對大型複雜資料物件使用許多計算和記憶體資源。

本主題說明如何在本機電腦上的 PowerShell 中執行背景工作。 如需在遠端電腦上執行背景工作的詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。 如需執行緒作業的詳細資訊，請參閱 [about_Thread_Jobs](about_Thread_Jobs.md)。

當您啟動背景工作時，命令提示字元會立即傳回，即使作業需要較長的時間才能完成。 工作執行時，您可以在工作階段中繼續工作，而不需中斷。

## <a name="the-job-cmdlets"></a>作業 Cmdlet

|Cmdlet          |描述                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |在本機電腦上啟動背景工作。           |
|`Get-Job`       |取得在中啟動的背景工作。      |
|                |目前的會話。                                       |
|`Receive-Job`   |取得背景工作的結果。                   |
|`Stop-Job`      |停止背景工作。                                |
|`Wait-Job`      |抑制命令提示字元，直到其中一個或所有工作為|
|                |完成。                                              |
|`Remove-Job`    |移除背景工作。                              |
|`Invoke-Command`|**AsJob** 參數會在上建立背景工作  |
|                |遠端電腦。 您可以使用 `Invoke-Command` 執行   |
|                |遠端的任何工作命令，包括 `Start-Job` 。       |

## <a name="how-to-start-a-job-on-the-local-computer"></a>如何在本機電腦上啟動作業

若要在本機電腦上啟動背景工作，請使用 `Start-Job` Cmdlet。

若要撰寫 `Start-Job` 命令，請以大括弧括住工作執行的命令 (`{}`) 。 使用 **ScriptBlock** 參數來指定命令。

下列命令會啟動在 `Get-Process` 本機電腦上執行命令的背景工作。

```powershell
Start-Job -ScriptBlock {Get-Process}
```

此 `Start-Job` 命令會傳回代表作業的物件。 工作物件包含工作的相關實用資訊，但是不包含工作結果。

將工作物件儲存在變數中，然後使用其他工作 Cmdlet 來管理背景工作。 下列命令會啟動工作物件，並將產生的工作物件儲存在 `$job` 變數中。

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

從 PowerShell 6.0 開始，您可以 `&` 在管線結尾使用 amersand () ，以啟動背景工作。 下列命令在功能上等同于上述命令。

```powershell
$job = Get-Process &
```

 () 的 & 符號 `&` 稱為背景運算子。 如需詳細資訊，請參閱 [背景運算子](about_Operators.md#background-operator-)。

您也可以使用 `Get-Job` Cmdlet 來取得物件，這些物件代表在目前會話中啟動的工作。 `Get-Job` 傳回傳回的相同工作物件 `Start-Job` 。

## <a name="getting-job-objects"></a>取得工作物件

若要取得物件，以代表目前會話中啟動的背景工作，請使用 `Get-Job` Cmdlet。 如果沒有參數，則會傳回 `Get-Job` 在目前會話中啟動的所有工作。

例如，下列命令會取得目前會話中的工作。

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

您也可以將工作物件儲存在變數中，並在稍後的命令中使用它來表示作業。 下列命令會取得識別碼為1的作業，並將它儲存在 `$job` 變數中。

```powershell
$job = Get-Job -Id 1
```

工作物件包含工作的狀態，指出作業是否已完成。 完成的作業狀態為 [已 **完成** ] 或 [ **失敗** ]。 作業也可能 **遭到封鎖** 或 **正在** 執行。

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a>取得作業的結果

當您執行背景工作時，結果不會立即出現。 相反地，此 `Start-Job` Cmdlet 會傳回代表工作的工作物件，但不包含結果。 若要取得背景工作的結果，請使用 `Receive-Job` Cmdlet。

下列命令會使用 `Receive-Job` Cmdlet 來取得工作的結果。 它會使用儲存在變數中的工作物件 `$job` 來識別作業。

```powershell
Receive-Job -Job $job
```

Cmdlet 會傳回 `Receive-Job` 作業的結果。

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

您也可以將工作的結果儲存在變數中。 下列命令會將工作的結果儲存在變數中 `$job` `$results` 。

```powershell
$results = Receive-Job -Job $job
```

而且，您可以使用重新導向運算子 () 或 Cmdlet，將作業的結果儲存在檔案中 `>` `Out-File` 。 下列命令會使用重新導向運算子，將作業的結果儲存在檔案中的 `$job` 變數中 `Results.txt` 。

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a>取得和保留部分工作結果

`Receive-Job`Cmdlet 會取得背景工作的結果。 如果作業已完成，則會 `Receive-Job` 取得所有工作結果。 如果作業仍在執行中， `Receive-Job` 則會取得到目前為止產生的結果。 您可以 `Receive-Job` 再次執行命令以取得剩餘的結果。

傳回 `Receive-Job` 結果時，根據預設，它會從儲存工作結果的快取中刪除這些結果。 如果您執行另一個 `Receive-Job` 命令，則只會取得尚未接收的結果。

下列命令 `Receive-Job` 會顯示作業完成之前執行的命令結果。

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

若要防止 `Receive-Job` 刪除傳回的工作結果，請使用 **Keep** 參數。 如此一來，就會傳回 `Receive-Job` 所有在該時間之前產生的結果。

下列命令顯示在尚未完成的作業上使用 **Keep** 參數的效果。

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

## <a name="waiting-for-the-results"></a>等候結果

如果您執行需要很長時間才能完成的命令，您可以使用工作物件的屬性來判斷作業何時完成。 下列命令會使用 `Get-Job` 物件取得目前會話中的所有背景工作。

```powershell
Get-Job
```

結果會出現在資料表中。 作業狀態會顯示在 [ **狀態** ] 資料行中。

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

在此情況下，State 屬性會顯示作業2仍在執行。 如果您現在要使用 `Receive-Job` Cmdlet 來取得工作結果，結果會是不完整的。 您可以重複使用此 `Receive-Job` Cmdlet 來取得所有結果。 根據預設，每次使用它時，您只會取得尚未接收的結果，但您可以使用 Cmdlet 的 **Keep** 參數 `Receive-Job` 來保留結果，即使已經收到這些結果也是一樣。

您可以將部分結果寫入檔案，然後在新的結果抵達時附加它們，或者您可以稍後等候並檢查作業的狀態。

您可以使用 Cmdlet 的 **Wait** 參數 `Receive-Job` ，它不會傳回命令提示字元，直到工作完成且所有結果都可供使用為止。

您也可以使用 `Wait-Job` Cmdlet 來等候工作的任何或所有結果。 `Wait-Job` 讓您等待特定工作、所有作業，或任何要完成的作業。

下列命令會使用 `Wait-Job` Cmdlet 來等候 **識別碼** 為
10.

```powershell
Wait-Job -ID 10
```

因此，在作業完成之前，會抑制 PowerShell 提示字元。

您也可以等候預定的一段時間。 此命令會使用 **Timeout** 參數將等待時間限制為120秒。 當時間過期時，命令提示字元會傳回，但是工作會繼續在背景執行。

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a>停止作業

若要停止背景工作，請使用 `Stop-Job` Cmdlet。 下列命令會啟動作業，以取得系統事件記錄檔中的每個專案。 它會將工作物件儲存在 `$job` 變數中。

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

下列命令會停止作業。 它使用管線運算子 (`|`) 將變數中的工作傳送 `$job` 至 `Stop-Job` 。

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a>刪除作業

若要移除背景工作，請使用 `Remove-Job` Cmdlet。 下列命令會刪除變數中的工作 `$job` 。

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a>調查失敗的作業

若要找出作業失敗的原因，請使用工作物件的 **Reason** 屬性。

下列命令會啟動不含所需認證的作業。 它會將工作物件儲存在 `$job` 變數中。

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

下列命令會使用 Reason 屬性來尋找導致作業失敗的錯誤。

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

在此情況下，作業失敗，因為遠端電腦需要明確的認證才能執行此命令。 **Reason** 屬性的值為：

連線到遠端伺服器失敗，出現下列錯誤訊息：「拒絕存取」。

## <a name="see-also"></a>另請參閱

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_PSSessions](about_PSSessions.md)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
