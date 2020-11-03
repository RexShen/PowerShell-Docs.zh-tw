---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: 1880651719d030bd015a6f431fce60527b56aae5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201399"
---
# Get-Process

## 概要
取得在本機電腦上執行的處理常式。

## SYNTAX

### Name (預設值)

```
Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### NameWithUserName

```
Get-Process [[-Name] <String[]>] -IncludeUserName [<CommonParameters>]
```

### Id

```
Get-Process -Id <Int32[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### IdWithUserName

```
Get-Process -Id <Int32[]> -IncludeUserName [<CommonParameters>]
```

### InputObject

```
Get-Process -InputObject <Process[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### InputObjectWithUserName

```
Get-Process -InputObject <Process[]> -IncludeUserName [<CommonParameters>]
```

## DESCRIPTION

`Get-Process`Cmdlet 會取得本機電腦上的處理常式。

如果沒有參數，這個 Cmdlet 會取得本機電腦上的所有處理常式。
您也可以使用進程名稱或處理序識別碼 (PID 來指定特定處理常式) 或透過管線將處理常式物件傳遞至此 Cmdlet。

根據預設，此 Cmdlet 會傳回包含此進程之詳細資訊的處理常式物件，並支援可讓您啟動和停止進程的方法。
您也可以使用 Cmdlet 的參數 `Get-Process` 來取得在處理常式中執行之程式的檔案版本資訊，以及取得處理常式所載入的模組。

## 範例

### 範例1：取得本機電腦上所有使用中進程的清單

```powershell
Get-Process
```

此命令會取得在本機電腦上執行之所有使用中進程的清單。
如需每個資料行的定義，請參閱 [附注](#notes) 一節。

### 範例2：取得一或多個處理常式的所有可用資料

```powershell
Get-Process winword, explorer | Format-List *
```

此命令取得電腦上 Winword 和 Explorer 處理程序的所有可用相關資料。
它會使用 **Name** 參數來指定處理常式，但會省略選擇性的參數名稱。
管線運算子會將 `|` 資料傳遞至 `Format-List` Cmdlet，此 Cmdlet 會顯示 `*` Winword 和 Explorer 處理常式物件的所有可用屬性。

您也可以依處理程序識別碼來識別處理程序。
例如， `Get-Process -Id 664, 2060` 。

### 範例3：取得工作集大於指定大小的所有處理常式

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

此命令取得工作集大於 20 MB 的所有處理程序。
它會使用 `Get-Process`  Cmdlet 來取得所有執行中的處理常式。
管線運算子會將 `|` 處理常式物件傳遞至 `Where-Object` Cmdlet，此 Cmdlet 只會選取值大於20000000個位元組的物件給工作 **WorkingSet** 人員屬性。

集 **量是處理** 程式物件的眾多屬性之一。
若要查看所有屬性，請輸入 `Get-Process | Get-Member` 。
根據預設，所有數量屬性都是以位元組為單位，即使預設顯示是以 KB 和 MB 來列示它們。

### 範例4：根據優先順序列出電腦上的進程

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

這些命令會根據其優先順序類別，將電腦上的處理常式列示在群組中。
第一個命令會取得電腦上的所有處理常式，然後將它們儲存在 `$A` 變數中。

第二個命令會使用管線將儲存在變數中的 **處理** 程式物件傳送 `$A` 至 `Get-Process` Cmdlet，然後傳送至 `Format-Table` Cmdlet，以使用 **優先權** 視圖來格式化處理常式。

**優先權** 視圖和其他視圖都是在 PowerShell 主目錄 () 中的 .ps1xml 格式檔案中定義 `$pshome` 。

### 範例5：將屬性新增至標準 Get-Process 輸出顯示

```powershell
Get-Process pwsh | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 .           pwsh
     6 23500 31348   142 2.75   4016 .           pwsh
    27 54572 54520   576 5.52   4428 .           pwsh
```

這個範例會提供 `Format-Table` 將 **MachineName** 屬性新增至標準 `Get-Process` 輸出顯示的命令。

### 範例6：取得處理常式的版本資訊

```powershell
Get-Process pwsh -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.2            6.1.2            C:\Program Files\PowerShell\6\pwsh.exe
```

此命令會使用 **FileVersionInfo** 參數來取得 PowerShell 處理常式的主要模組 pwsh.exe 檔案的版本資訊。

若要在 Windows Vista 和更新版本的 Windows 上，使用您未擁有的進程來執行此命令，您必須使用 [以系統管理員身分執行] 選項開啟 PowerShell。

### 範例7：取得以指定進程載入的模組

```powershell
Get-Process SQL* -Module
```

此命令會使用 **Module** 參數取得處理常式所載入的模組。
此命令會取得名稱開頭為 SQL 之進程的模組。

若要在 Windows Vista 和更新版本的 Windows 上，使用您未擁有的進程來執行此命令，您必須使用 [以系統管理員身分執行] 選項啟動 PowerShell。

### 範例8：尋找進程的擁有者

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     pwsh
```

此命令示範如何尋找處理程序的擁有者。
在 Windows 中， **IncludeUserName** 參數需要提高的使用者權限 (以系統管理員身分執行) 。
輸出顯示擁有者為 Domain01\user01。

### 範例9：使用自動變數來識別裝載目前會話的進程

```powershell
Get-Process pwsh
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21     105.95       4.33    1192  10 pwsh
    79    83.81     117.61       2.16   10580  10 pwsh
```

```powershell
Get-Process -Id $PID
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21      77.53       4.39    1192  10 pwsh
```

這些命令會示範如何使用 `$PID` 自動變數來識別裝載目前 PowerShell 會話的處理常式。
您可以使用這個方法來區別主機進程與其他您可能想要停止或關閉的 PowerShell 進程。

第一個命令會取得目前會話中的所有 PowerShell 處理常式。

第二個命令會取得裝載目前會話的 PowerShell 處理常式。

### 範例10：取得具有主視窗標題的所有處理常式，並將它們顯示在資料表中

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

此命令取得具有主視窗標題的所有處理程序，並將它們顯示在含有處理程序識別碼和處理程序名稱的表格中。

**MainWindowTitle** 屬性只是傳回之 **處理** 程式物件的許多實用屬性之一 `Get-Process` 。
若要查看所有屬性，請使用管線將命令的結果傳送 `Get-Process` 至 `Get-Member` Cmdlet `Get-Process | Get-Member` 。

## PARAMETERS

### -FileVersionInfo

指出此 Cmdlet 會取得在處理常式中執行之程式的檔案版本資訊。

在 Windows Vista 和更新版本的 Windows 上，您必須使用 [以系統管理員身分執行] 選項開啟 PowerShell，才能在不是您所擁有的處理常式上使用這個參數。

若要取得遠端電腦上處理常式的檔案版本資訊，請使用 `Invoke-Command` Cmdlet。

使用這個參數相當於取得每個處理常式物件的 **mainmodule.fileversioninfo. FileVersionInfo** 屬性。
當您使用這個參數時， `Get-Process` 會傳回 **FileVersionInfo** 物件 FileVersionInfo，而不是處理 **程式** 物件。
因此，您無法使用管線將命令的輸出傳送到預期處理常式物件的 Cmdlet，例如 `Stop-Process` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

依處理程序識別碼 (PID) 指定一個或多個處理程序。
若要指定多個識別碼，請使用逗號來分隔識別碼。
若要尋找處理程序的 PID，請輸入 `Get-Process`。

```yaml
Type: System.Int32[]
Parameter Sets: Id, IdWithUserName
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeUserName

指出會傳回 **進程** 物件的使用者名稱值與命令的結果。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定一個或多個處理程序物件。
輸入包含物件的變數，或輸入可取得物件的命令或運算式。

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Module

指出此 Cmdlet 會取得處理常式所載入的模組。

在 Windows Vista 和更新版本的 Windows 上，您必須使用 [以系統管理員身分執行] 選項開啟 PowerShell，才能在不是您所擁有的處理常式上使用這個參數。

若要取得遠端電腦上的處理常式所載入的模組，請使用 `Invoke-Command` Cmdlet。

這個參數相當於取得每個處理常式物件的 **模組** 屬性。
當您使用此參數時，此 Cmdlet 會傳回 **ProcessModule** 物件 ProcessModule，而不是處理 **程式** 物件。
因此，您無法使用管線將命令的輸出傳送到預期處理常式物件的 Cmdlet，例如 `Stop-Process` 。

當您在同一個命令中同時使用 *Module* 和 **FileVersionInfo** 參數時，此 Cmdlet 會傳回 **FileVersionInfo** 物件，其中包含所有模組之檔案版本的相關資訊。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

依處理程序名稱指定一個或多個處理程序。
您可以輸入多個處理程序名稱 (以逗號分隔) 及使用萬用字元。
參數名稱 ("Name") 為選擇性。

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.Diagnostics.Process

您可以使用管線將處理程序物件傳送至此 Cmdlet。

## 輸出

### FileVersionInfo，ProcessModule 的程式，系統診斷。

根據預設，此 Cmdlet 會傳回 **system.object** 物件。
如果您使用 **FileVersionInfo** 參數，它會傳回 **FileVersionInfo** 物件。
如果您使用 **Module** 參數，但沒有 **FileVersionInfo** 參數，則會傳回 **ProcessModule** 物件。

## 注意

- 您也可以透過內建的別名（ps 和 gps）來參考這個 Cmdlet。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。
- 在執行64位版 Windows 的電腦上，64位版本的 PowerShell 只會取得64位的進程模組，而32位版本的 PowerShell 只會取得32位的進程模組。
- 您可以在 PowerShell 中使用 Windows Management Instrumentation (WMI) Win32_Process 物件的屬性和方法。 如需詳細資訊，請參閱 `Get-WmiObject` 和 WMI SDK。
- 處理程序的預設顯示是一個包含下列欄位的表格。 如需處理常式物件的所有屬性描述，請參閱 MSDN library 中的 [處理常式屬性](/dotnet/api/system.diagnostics.process) 。
  - 控制碼：進程已開啟的控制碼數目。
  - NPM (K) ：進程正在使用的非分頁式記憶體數量（以 kb 為單位）。
  - PM (K) ：進程正在使用的可分頁記憶體數量（以 kb 為單位）。
  - WS (K) ：進程的工作集大小（以 kb 為單位）。
    工作集是由處理程序最近參照的記憶體分頁組成。
  - VM (M) ：進程正在使用的虛擬記憶體數量（以 mb 為單位）。
    虛擬記憶體包括磁碟上分頁檔案中的儲存體。
  - CPU (s) ：進程已在所有處理器上使用的處理器時間量（以秒為單位）。
  - 識別碼：進程的處理序識別碼 (PID) 。
  - ProcessName：進程的名稱。
    如需處理程序相關概念的說明，請參閱 [說明及支援中心] 中的 [詞彙] 和 [工作管理員] 的 [說明]。
- 您也可以使用所提供之進程的內建替代視圖 `Format-Table` ，例如 **StartTime** 和 **Priority** ，也可以設計自己的觀點。

## 相關連結

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
