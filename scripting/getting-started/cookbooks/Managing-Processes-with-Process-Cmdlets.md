---
title: 使用處理程序 Cmdlet 管理處理程序
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
---
# 使用處理程序 Cmdlet 管理處理程序
您可以使用 Windows PowerShell 中的處理程序 Cmdlet，管理 Windows PowerShell 中的本機和遠端處理程序。

## 取得處理程序 (Get-Process)
若要取得在本機電腦上執行的處理程序，請在不使用參數的情況下執行 **Get-Process**。

您可以藉由指定處理程序的名稱或識別碼，來取得特定處理程序。 下列命令會取得閒置處理程序︰

```
PS> Get-Process -id 0
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

雖然 Cmdlet 在某些情況下未傳回任何資料是正常的，但是當您依處理程序的 ProcessId 指定處理程序時，由於一般目的是擷取已知的執行中處理程序，因此如果 **Get-Process** 找不到任何相符項目，則會產生錯誤。 如果沒有該識別碼的處理程序，很可能是識別碼不正確，或感興趣的處理程序已經結束：

```
PS> Get-Process -Id 99
Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

您可以使用 Get-Process Cmdlet 的 Name 參數，根據處理序名稱指定處理程序的子集。 Name 參數可以接受以逗號分隔的多個名稱清單，而且支援使用萬用字元，因此您可以輸入名稱模式。

例如，下列命令會取得名稱開頭為 "ex" 的處理程序。

```
PS> Get-Process -Name ex*
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

因為 .NET System.Diagnostics.Process 類別是 Windows PowerShell 處理程序的基礎，所以它會遵循 System.Diagnostics.Process 所使用的一些慣例。 其中一個慣例是可執行檔的處理程序名稱，絕對不可以在可執行檔名稱結尾包含 ".exe"。

**Get-Process** 也接受 Name 參數有多個值。

```
PS> Get-Process -Name exp*,power* 
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

您可以使用 Get-Process 的 ComputerName 參數取得遠端電腦上的處理程序。 例如，下列命令會取得本機電腦 (以 "localhost" 表示) 和兩部遠端電腦上的 PowerShell 處理程序。

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

電腦名稱雖然未出現在此顯示中，但儲存在 Get-Process 所傳回之處理程序物件的 MachineName 屬性中。 下列命令會使用 Format-Table Cmdlet 顯示處理程序物件的處理程序 ID、ProcessName 和 MachineName (ComputerName) 屬性。

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName
  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

這個更複雜的命令會將 MachineName 屬性新增至標準 Get-Process 顯示。 倒單引號 (`)(ASCII 96) 是 Windows PowerShell 接續字元。

```
get-process powershell -computername localhost, Server01, Server02 | format-table -property Handles, `
                    @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}}, `
                    @{Label="PM(K)";Expression={[int]($_.PM/1024)}}, `
                    @{Label="WS(K)";Expression={[int]($_.WS/1024)}}, `
                    @{Label="VM(M)";Expression={[int]($_.VM/1MB)}}, `
                    @{Label="CPU(s)";Expression={if ($_.CPU -ne $()` 
                    {$_.CPU.ToString("N")}}}, `                                                                         
                    Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## 停止處理程序 (Stop-Process)
Windows PowerShell 可讓您彈性地列出處理程序，但停止處理程序又如何？

**Stop-Process** Cmdlet 接受使用 Name 或 Id 指定您要停止的處理程序。 您是否能夠停止處理程序取決於您的權限。 某些處理程序無法停止。 例如，如果您嘗試停止閒置處理程序，您會收到錯誤︰

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

您也可以 **Confirm** 參數來強制提示。 如果您在指定處理程序名稱時使用萬用字元，此參數特別有用，因為您可能會不小心比對一些不想停止的處理程序︰

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

您可以使用一些物件篩選 Cmdlet 來管理複雜的處理程序。 因為當處理程序物件不再回應時的 Responding 屬性為 true，所以您可以使用下列命令停止所有無回應的應用程式︰

```
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

您可以在其他情況下使用相同的方法。 例如，假設當使用者啟動另一個應用程式時，次要通知區域應用程式會自動執行。 您可能會發現這在終端機服務工作階段中無法正常運作，但您仍然想要在實體電腦主控台上執行的工作階段中予以保留。 連線到實體電腦桌面之工作階段的工作階段識別碼一律為 0，因此您可以使用 **Where-Object** 和處理程序 **SessionId**，停止該處理程序在其他工作階段中的所有執行個體：

```
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Stop-Process Cmdlet 沒有 ComputerName 參數。 因此，若要在遠端電腦上執行停止處理程序命令，您需要使用 Invoke-Command Cmdlet。 例如，若要停止 Server01 遠端電腦上的 PowerShell 處理程序，請輸入：

```
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## 停止所有其他 Windows PowerShell 工作階段
能夠停止目前工作階段以外的所有執行中 PowerShell 工作階段有時可能會很有用。 如果工作階段使用太多資源或無法存取 (可能在遠端執行或在其他桌面工作階段中)，您可能無法直接將它停止。 不過如果您嘗試停止所有執行中的工作階段，可能反而終止目前的工作階段。

每個 Windows PowerShell 工作階段都有包含 Windows PowerShell 處理程序識別碼的環境變數 PID。 您可以根據每個工作階段的識別碼檢查 $PID，並只終止具有不同識別碼的 Windows PowerShell 工作階段。 下列管線命令會執行這項操作，並傳回終止的工作階段清單 (因為使用了 **PassThru** 參數)：

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -
PassThru
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## 啟動、偵錯及等候處理程序
Windows PowerShell 也提供啟動 (或重新啟動)、偵錯處理程序，以及等候處理程序完成再執行命令的 Cmdlet。 如需這些 Cmdlet 的資訊，請參閱每個 Cmdlet 的 Cmdlet 說明主題。

## 另請參閱
[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
[Start-Process](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
[Wait-Process](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
[Debug-Process](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
[Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)



<!--HONumber=Apr16_HO2-->


