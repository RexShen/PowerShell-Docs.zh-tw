---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204027"
---
# Get-ComputerRestorePoint

## 概要
在本機電腦上取得還原點。

## SYNTAX

### ID (預設值)

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### LastStatus

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## DESCRIPTION

此 `Get-ComputerRestorePoint` Cmdlet 會取得本機電腦的系統還原點。 而且，它可以顯示最近嘗試還原電腦的狀態。

您可以使用中的資訊 `Get-ComputerRestorePoint` 來選取還原點。 例如，使用序號來識別 Cmdlet 的還原點 `Restore-Computer` 。

`Get-ComputerRestorePoint`只有用戶端作業系統（例如 Windows 10、windows 7、Windows Vista 和 WINDOWS XP）才支援系統還原點和 Cmdlet。

## 範例

### 範例1：取得所有系統還原點

在此範例中，會 `Get-ComputerRestorePoint` 取得所有本機電腦的系統還原點。

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### 範例2：取得特定序號

此範例會取得特定序號的系統還原點。

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

`Get-ComputerRestorePoint` 使用 **RestorePoint** 參數來指定以逗號分隔的序號陣列。

### 範例3：顯示系統還原的狀態

此範例會顯示本機電腦上最近系統還原的狀態。

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

`Get-ComputerRestorePoint` 使用 **LastStatus** 參數來顯示最近系統還原的結果。

### 範例4：使用運算式來轉換 CreationTime

`Get-ComputerRestorePoint` 將 **CreationTime** 輸出為 WINDOWS MANAGEMENT INSTRUMENTATION (WMI) 日期和時間字串。

在此範例中，變數會儲存將 **CreationTime** 字串轉換成 **DateTime** 物件的運算式。 若要在轉換之前先查看 **CreationTime** 字串，請使用類似的命令 `((Get-ComputerRestorePoint).CreationTime)` 。 如需 WMI 日期和時間字串的詳細資訊，請參閱 [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime)。

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

`$date`變數會利用使用 **ConvertToDateTime** 方法的運算式來儲存雜湊表。 運算式會將 **CreationTime** 屬性的值從 WMI 字串轉換成 **DateTime** 物件。

`Get-ComputerRestorePoint` 將系統還原點物件沿著管線向下傳送。 `Select-Object` 使用 **Property** 參數來指定要顯示的屬性。 針對管線中的每個物件，中的運算式會 `$date` 轉換 **CreationTime** ，並在 **Date** 屬性中輸出結果。

### 範例5：使用屬性取得序號

此範例會使用 **SequenceNumber** 屬性和陣列索引來取得序號。 輸出只包含序號。

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

`Get-ComputerRestorePoint` 使用 **SequenceNumber** 屬性搭配陣列索引。 的陣列索引會 `-1` 取得陣列中最近的序號。

## PARAMETERS

### -LastStatus

表示 `Get-ComputerRestorePoint` 取得最新系統還原作業的狀態。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePoint

指定系統還原點的序號。 您可以指定單一序號或序號的逗號分隔陣列。

如果未指定 **RestorePoint** 參數，則會傳回 `Get-ComputerRestorePoint` 所有本機電腦的系統還原點。

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法將物件沿著管線向下傳送至 `Get-ComputerRestorePoint` 。

## 輸出

### System.management.managementobject # root\default\SystemRestore 或 String

`Get-ComputerRestorePoint` 傳回 **SystemRestore** 物件，這是 WINDOWS MANAGEMENT INSTRUMENTATION (WMI) **SystemRestore** 類別的實例。

當您使用 **LastStatus** 參數時，會傳回 `Get-ComputerRestorePoint` 字串。

## 注意

若要 `Get-ComputerRestorePoint` 在 Windows Vista 和更新版本的 windows 上執行命令，請使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。

`Get-ComputerRestorePoint` 使用 WMI **SystemRestore** 類別。

## 相關連結

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)

[SystemRestore](/windows/win32/sr/systemrestore)
