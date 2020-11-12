---
description: 提供有關 PowerShell 背景工作如何在背景中執行命令或運算式的資訊，而不需與目前的會話互動。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 6ddb54bac62e7bc11a045874700acb3982a0093b
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524447"
---
# <a name="about-jobs"></a>關於工作

## <a name="short-description"></a>簡短描述
提供有關 PowerShell 背景工作如何在背景中執行命令或運算式的資訊，而不需與目前的會話互動。

## <a name="long-description"></a>完整描述

PowerShell 會透過作業同時執行命令和腳本。 PowerShell 提供三種工作類型來支援平行存取。

- `RemoteJob` -命令和腳本會在遠端會話上執行。 如需詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。
- `BackgroundJob` -命令和腳本會在本機電腦上的個別進程中執行。
- `PSTaskJob` 或 `ThreadJob` -命令和腳本會在本機電腦上相同進程內的個別執行緒中執行。 如需詳細資訊，請參閱 [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)。

在不同的電腦或個別的進程中遠端執行腳本，可提供絕佳的隔離。 在遠端作業中發生的任何錯誤，都不會影響到其他執行中的作業或啟動作業的父會話。 不過，遠端層會增加額外負荷，包括物件序列化。 所有物件都會進行序列化和還原序列化，因為它們會在父會話和遠端 (作業) 會話之間傳遞。 大型複雜資料物件的序列化可能會耗用大量的計算和記憶體資源，並在網路上傳輸大量資料。

以執行緒為基礎的作業不像遠端和背景工作一樣健全，因為它們在不同執行緒上的相同進程中執行。 如果有一項作業發生嚴重錯誤，導致進程損毀，則會終止進程中的所有其他工作。

不過，以執行緒為基礎的作業需要較少的額外負荷。 它們不會使用遠端層或序列化。 結果物件會傳回做為目前會話中之即時物件的參考。 如果沒有此額外負荷，以執行緒為基礎的作業執行速度會更快，且使用的資源比其他作業類型還要少。

> [!IMPORTANT]
> 建立作業的父會話也會監視作業狀態，並收集管線資料。 當工作達到已完成狀態時，父進程會終止作業子進程。 如果父會話終止，則所有執行中的子工作都會連同其子進程一起終止。

有兩種方式可以解決這項限制：

1. 用 `Invoke-Command` 來建立在已中斷連線的會話中執行的作業。 如需詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。
1. 用 `Start-Process` 來建立新的處理常式，而不是作業。 如需詳細資訊，請參閱 [啟動流程](xref:Microsoft.PowerShell.Management.Start-Process)。

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

當您啟動背景工作時，命令提示字元會立即傳回，即使作業需要較長的時間才能完成。 工作執行時，您可以在工作階段中繼續工作，而不需中斷。

此 `Start-Job` 命令會傳回代表作業的物件。 工作物件包含工作的相關實用資訊，但是不包含工作結果。

您可以將工作物件儲存在變數中，然後將它與其他 **工作** Cmdlet 搭配使用，以管理背景工作。 下列命令會啟動工作物件，並將產生的工作物件儲存在 `$job` 變數中。

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

從 PowerShell 6.0 開始，您可以使用 `&` 管線結尾 () 背景運算子來啟動背景工作。 如需詳細資訊，請參閱 [背景運算子](about_Operators.md#background-operator-)。

使用 background 運算子的功能相當於使用 `Start-Job` 上述範例中的 Cmdlet。

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a>取得工作物件

指令 `Get-Job` 程式會傳回物件，代表在目前會話中啟動的背景工作。 如果沒有參數，則會傳回 `Get-Job` 在目前會話中啟動的所有工作。

```powershell
Get-Job
```

工作物件包含工作的狀態，指出作業是否已完成。 完成的作業狀態為 [已 **完成** ] 或 [ **失敗** ]。 作業也可能 **遭到封鎖** 或 **正在** 執行。

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

您可以將工作物件儲存在變數中，並在稍後的命令中使用它來表示作業。 下列命令會取得識別碼為1的作業，並將它儲存在 `$job` 變數中。

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a>取得作業的結果

當您執行背景工作時，結果不會立即出現。 若要取得背景工作的結果，請使用 `Receive-Job` Cmdlet。

下列範例會 `Receive-Job` 使用變數中的工作物件，來取得工作的結果 `$job` 。

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

您可以將工作的結果儲存在變數中。 下列命令會將工作的結果儲存在變數中 `$job` `$results` 。

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a>取得和保留部分工作結果

`Receive-Job`Cmdlet 會取得背景工作的結果。 如果作業已完成，則會 `Receive-Job` 取得所有工作結果。 如果作業仍在執行中， `Receive-Job` 則會取得到目前為止產生的結果。 您可以 `Receive-Job` 再次執行命令以取得剩餘的結果。

根據預設， `Receive-Job` 會從儲存工作結果的快取中刪除結果。 當您再次執行時 `Receive-Job` ，只會取得第一次執行後抵達的新結果。

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

使用 **Keep** 參數以防止 `Receive-Job` 刪除傳回的工作結果。 下列命令顯示在尚未完成的作業上使用 **Keep** 參數的效果。

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

### <a name="waiting-for-the-results"></a>等候結果

如果您執行需要很長時間才能完成的命令，您可以使用工作物件的屬性來判斷作業何時完成。 下列命令會使用 `Get-Job` 物件取得目前會話中的所有背景工作。

```powershell
Get-Job
```

結果會出現在資料表中。 作業狀態會顯示在 [ **狀態** ] 資料行中。

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

在此情況下， **State** 屬性會顯示作業2仍在執行。 如果您現在要使用 `Receive-Job` Cmdlet 來取得工作結果，結果會是不完整的。 您可以重複使用此 `Receive-Job` Cmdlet 來取得所有結果。 使用 **State** 屬性來判斷作業何時完成。

您也可以使用 Cmdlet 的 **Wait** 參數 `Receive-Job` 。 使用此參數時，此 Cmdlet 不會傳回命令提示字元，直到工作完成且所有結果都可用為止。

您也可以使用 `Wait-Job` Cmdlet 來等候工作的任何或所有結果。 `Wait-Job` 讓您等候一或多個特定工作或所有作業。
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

作業可能會因為許多原因而失敗。 工作物件包含 **Reason** 屬性，其中包含失敗原因的相關資訊。

下列範例會在沒有所需認證的情況下啟動作業。

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

檢查 **Reason** 屬性以找出造成作業失敗的錯誤。

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

在此情況下，作業失敗，因為遠端電腦需要明確的認證才能執行此命令。 **Reason** 屬性包含下列訊息：

> 連線到遠端伺服器失敗，出現下列錯誤訊息：「拒絕存取」。

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
