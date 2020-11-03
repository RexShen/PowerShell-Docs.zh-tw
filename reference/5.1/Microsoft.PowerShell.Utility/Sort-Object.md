---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: 1d27641f94d82b85bab694b392c0f09bb3265517
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205904"
---
# Sort-Object

## 概要
依屬性值排序物件。

## SYNTAX

### Default (預設值)

```
Sort-Object [[-Property] <Object[]>] [-Descending] [-Unique] [-InputObject <psobject>]
 [-Culture <string>] [-CaseSensitive] [<CommonParameters>]
```

## DESCRIPTION

此 `Sort-Object` Cmdlet 會根據物件屬性值，以遞增或遞減順序排序物件。 如果命令中沒有包含排序屬性，PowerShell 會使用第一個輸入物件的預設排序屬性。 如果輸入物件的類型沒有預設排序屬性，PowerShell 會嘗試比較物件本身。 如需詳細資訊，請參閱 [附注](#notes) 一節。

您可以依單一屬性或多個屬性來排序物件。 多個屬性會使用雜湊表，以遞增順序、遞減順序或排序次序的組合來排序。 屬性會排序為區分大小寫或不區分大小寫。 使用 **Unique** 參數可消除輸出中的重複專案。

## 範例

### 範例 1︰依名稱排序目前的目錄

此命令會排序目錄中的檔案和子目錄。

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

`Get-ChildItem`Cmdlet 會從 **Path** 參數 **C:\Test** 所指定的目錄中取得檔案和子目錄。 這些物件會向下傳送至 `Sort-Object` Cmdlet。
`Sort-Object` 未指定屬性，因此輸出會依預設排序屬性 [ **名稱** ] 排序。

### 範例 2︰依檔案長度排序目前的目錄

此命令會依長度以遞增順序顯示目前目錄中的檔案。

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

`Get-ChildItem`Cmdlet 會從 **Path** 參數所指定的目錄取得檔案。
**File** 參數指定 `Get-ChildItem` 只取得檔案物件。 這些物件會向下傳送至 `Sort-Object` Cmdlet。 `Sort-Object` 使用 **length** 參數，依長度以遞增順序排序檔案。

### 範例3：依記憶體使用量排序處理常式

這個範例會根據 (WS) 大小的工作集，顯示記憶體使用量最高的進程。

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

`Get-Process`Cmdlet 會取得在電腦上執行的進程清單。 處理常式物件會向下傳送至 `Sort-Object` Cmdlet。 `Sort-Object` 使用 **Property** 參數來依 **WS** 排序物件。 這些物件會向下傳送至 `Select-Object` Cmdlet。
`Select-Object` 使用 **最後一個** 參數來指定最後五個物件，也就是具有最高 **WS** 使用量的物件。

### 範例4：依識別碼排序 HistoryInfo 物件

此命令會使用 **Id** 屬性來排序 PowerShell 會話的 **HistoryInfo** 物件。 每個 PowerShell 會話都有自己的命令歷程記錄。

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

`Get-History`Cmdlet 會從目前的 PowerShell 會話取得歷程記錄物件。 這些物件會向下傳送至 `Sort-Object` Cmdlet。 `Sort-Object` 使用 **Property** 參數依 **識別碼** 排序物件。 **遞減** 參數會將命令歷程記錄從最新排序到最舊。

### 範例5：使用雜湊表以遞增和遞減順序排序屬性

此命令會使用兩個屬性來排序物件、 **狀態** 和 **DisplayName** 。 **狀態** 會以遞減順序排序，而 **DisplayName** 會以遞增順序排序。

雜湊表可用來指定 **屬性** 參數的值。 雜湊表會使用運算式來指定屬性名稱和排序次序。 如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。

雜湊表中使用的 **Status** 屬性是列舉屬性。
如需詳細資訊，請參閱 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

`Get-Service`Cmdlet 會取得電腦上的服務清單。 服務物件會向下傳送至 `Sort-Object` Cmdlet。 `Sort-Object` 使用 **property** 參數搭配雜湊表來指定屬性名稱和排序次序。 **屬性** 參數會依兩個屬性 **排序，以** 遞減順序和 **DisplayName** 以遞增順序排序。

**狀態** 是列舉的屬性。 [已 **停止** ] 的值為 **1** **，且執行的值** 為 **4** 。 **遞減** 的參數會設定為， `$True` 以便 **Running** 在 **停止** 的進程之前顯示執行中的處理常式。 **DisplayName** 會將 **遞減** 參數設定為， `$False` 以依字母順序排序顯示名稱。

### 範例 6︰依時間範圍排序文字檔案

此命令會依 **CreationTime** 和 **LastWriteTime** 之間的時間範圍，以遞減順序排序文字檔。

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt

```

此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 **C:\Test** 和所有檔案 `*.txt` 。 這些物件會向下傳送至 `Sort-Object` Cmdlet。
`Sort-Object` 使用 **Property** 參數搭配雜湊表，以判斷每個檔案在 **CreationTime** 和 **LastWriteTime** 之間的時間範圍。 **遞減** 的參數會設定為， `$False` 以最長到最短時間範圍的順序排序。

### 範例 7︰在文字檔案中排序名稱

此範例顯示如何從文字檔排序清單。 原始檔案會顯示為未排序的清單。 `Sort-Object` 排序內容，然後使用移除重複專案的 **唯一** 參數來排序內容。

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目錄和檔案名。 File **ServerNames.txt** 包含未排序的電腦名稱稱清單。

此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目錄和檔案名。 File **ServerNames.txt** 包含未排序的電腦名稱稱清單。 這些物件會向下傳送至 `Sort-Object` Cmdlet。 `Sort-Object` 以預設順序昇冪排序清單。

此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目錄和檔案名。 File **ServerNames.txt** 包含未排序的電腦名稱稱清單。 這些物件會向下傳送至 `Sort-Object` Cmdlet。 `Sort-Object` 使用 **Unique** 參數移除重複的電腦名稱稱。 清單會以預設順序（遞增）排序。

### 範例8：將字串排序為整數

這個範例示範如何將包含字串物件的文字檔排序為整數。 您可以將管線中的每個命令向下傳送至 `Get-Member` ，並確認物件是字串，而不是整數。 在這些範例中，檔案 `ProductId.txt` 包含未排序的產品編號清單。

在第一個範例中，會取得檔案的 `Get-Content` 內容以及 Cmdlet 的管道線 `Sort-Object` 。 `Sort-Object` 以遞增順序排序字串物件。

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

在第二個範例中，會取得檔案的 `Get-Content` 內容以及 Cmdlet 的管道線 `Sort-Object` 。 `Sort-Object` 使用腳本區塊將字串轉換成整數。 在範例程式碼中， `[int]` 會將字串轉換成整數，並 `$_` 代表每個字串，因為它會在管線中關閉。 整數物件會向下傳送至 `Sort-Object` Cmdlet。
`Sort-Object` 依數位順序排序整數物件。

此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目錄和檔案名。 檔案 **ProductId.txt** 包含未排序的產品編號清單。 字串物件會將管線向下傳送至 `ForEach-Object` Cmdlet。 `ForEach-Object` 使用腳本區塊將字串轉換成整數。 在範例程式碼中， `[int]` 會將字串轉換成整數，並 `$_` 代表每個字串，因為它會在管線中關閉。 整數物件會向下傳送至 `Sort-Object` Cmdlet。 `Sort-Object` 依數位順序排序整數物件。
## PARAMETERS

### -CaseSensitive

指出排序會區分大小寫。 依預設，排序不區分大小寫。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### -Culture

指定要用於排序的文化設定。 使用 `Get-Culture` 來顯示系統的文化特性設定。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Descending

表示 `Sort-Object` 以遞減順序排序物件。 預設值為遞增排序。

若要使用不同的排序次序來排序多個屬性，請使用雜湊表。 例如，您可以使用雜湊表，以遞增順序排序一個屬性，並以遞減順序排序另一個屬性。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

若要排序物件，請將其傳送至管線 `Sort-Object` 。 如果您使用 **InputObject** 參數來提交專案的集合，則 `Sort-Object` 會接收代表集合的一個物件。 因為無法排序一個物件，所以會傳回 `Sort-Object` 未變更的整個集合。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Property

指定 `Sort-Object` 用來排序物件的屬性名稱。 允許使用萬用字元。
物件會根據屬性值排序。 如果您未指定屬性，則會 `Sort-Object` 根據物件類型或物件本身的預設屬性進行排序。

您可以依遞增順序、遞減順序或排序次序的組合來排序多個屬性。 當您指定多個屬性時，物件會依第一個屬性排序。 如果有多個物件的第一個屬性具有相同的值，則會依第二個屬性排序這些物件。 此程序會持續執行到沒有指定的屬性或物件群組為止。

**屬性** 參數的值可以是計算的屬性。 若要建立計算的屬性，請使用雜湊表。

雜湊表的有效索引鍵如下所示：

- `expression` - `<string>` 或 `<script block>`
- `ascending` 或 `descending` - `<boolean>`

如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### -Unique

指出會 `Sort-Object` 排除重複專案，並只傳回集合的唯一成員。 唯一值的第一個實例會包含在排序的輸出中。

**Unique** 不區分大小寫。 只有字元大小寫不同的字串會被視為相同。
例如，字元和字元。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線傳送要排序的物件 `Sort-Object` 。

## 輸出

### System.Management.Automation.PSObject

`Sort-Object` 傳回已排序的物件。

## 注意

此 `Sort-Object` Cmdlet 會根據命令中指定的屬性或物件類型的預設排序屬性來排序物件。 預設排序屬性是使用在檔案 `PropertySet` 中命名的來定義 `DefaultKeyPropertySet` `types.ps1xml` 。 如需詳細資訊，請參閱 [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml)。

如果物件沒有其中一個指定的屬性，則會將該物件的屬性值解釋 `Sort-Object` 為 **Null** ，並置於排序次序的結尾。

當沒有排序屬性可用時，PowerShell 會嘗試比較物件本身。
`Sort-Object` 針對每個屬性使用 **Compare** 方法。 如果屬性不會執行 **IComparable** ，此 Cmdlet 會將屬性值轉換為字串，並針對 **system.string** 使用 **Compare** 方法。 如需詳細資訊，請參閱 [CompareTo (物件) 方法](/dotnet/api/system.management.automation.psobject.compareto)。

如果您對列舉屬性（例如 **狀態** ）進行排序，則 `Sort-Object` 依列舉值排序。 針對 Windows 服務，已 **停止** 的值為 **1** ， **且執行的值** 為 **4** 。
**由於列舉** 值的原因，已 **停止** 會先排序。 如需詳細資訊，請參閱 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Tee-Object](Tee-Object.md)
