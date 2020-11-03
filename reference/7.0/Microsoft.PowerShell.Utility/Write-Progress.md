---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 35b417b35d67e5cbe0df8719ba790135645d64e1
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208492"
---
# Write-Progress

## 概要
在 PowerShell 命令視窗中顯示進度列。

## SYNTAX

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Write-Progress` Cmdlet 會在 PowerShell 命令視窗中顯示進度列，以描述執行中命令或腳本的狀態。 您可以選擇進度列反映的指示器及進度列上下方顯示的文字。

## 範例

### 範例1：顯示 For 迴圈的進度

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

此命令會顯示 For 迴圈從 1 計算至 100 的進度。

此 `Write-Progress` Cmdlet 包含狀態列標題 `Activity` 、狀態行和變數 `$i` (「For 迴圈」中的計數器) ，指出工作的相對完整性。

### 範例2：顯示 nested For 迴圈的進度

```powershell
for($I = 1; $I -lt 101; $I++ )
{
    Write-Progress -Activity Updating -Status 'Progress->' -PercentComplete $I -CurrentOperation OuterLoop
    for($j = 1; $j -lt 101; $j++ )
    {
        Write-Progress -Id 1 -Activity Updating -Status 'Progress' -PercentComplete $j -CurrentOperation InnerLoop
    }
}
```

```Output
Updating
Progress ->
 [ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo]
OuterLoop
Updating
Progress
 [oooooooooooooooooo                                                   ]
InnerLoop
```

此範例會顯示兩個巢狀 For 迴圈的進度，每個迴圈都會以進度列表示。

`Write-Progress`第二個進度列的命令包含用來區分它與第一個進度列的 **識別碼** 參數。

如果沒有 **Id** 參數，進度列就會彼此重迭，而不是顯示在另一個。

### 範例3：在搜尋字串時顯示進度

```powershell
# Use Get-EventLog to get the events in the System log and store them in the $Events variable.
$Events = Get-EventLog -LogName system
# Pipe the events to the ForEach-Object cmdlet.
$Events | ForEach-Object -Begin {
    # In the Begin block, use Clear-Host to clear the screen.
    Clear-Host
    # Set the $i counter variable to zero.
    $i = 0
    # Set the $out variable to a empty string.
    $out = ""
} -Process {
    # In the Process script block search the message property of each incoming object for "bios".
    if($_.message -like "*bios*")
    {
        # Append the matching message to the out variable.
        $out=$out + $_.Message
    }
    # Increment the $i counter variable which is used to create the progress bar.
    $i = $i+1
    # Use Write-Progress to output a progress bar.
    # The Activity and Status parameters create the first and second lines of the progress bar heading, respectively.
    Write-Progress -Activity "Searching Events" -Status "Progress:" -PercentComplete ($i/$Events.count*100)
} -End {
    # Display the matching messages using the out variable.
    $out
}
```

此命令會顯示在「系統」記錄檔中尋找 "bios" 字串之命令的進度。

值 **的計算** 方式是將已處理的事件總數所處理的事件數目除以， `$I` 然後將 `$Events.count` 該結果乘以100。

### 範例4：顯示每個嵌套進程層級的進度

```powershell
foreach ( $i in 1..10 ) {
  Write-Progress -Id 0 "Step $i"
  foreach ( $j in 1..10 ) {
    Write-Progress -Id 1 -ParentId 0 "Step $i - Substep $j"
    foreach ( $k in 1..10 ) {
      Write-Progress -Id 2  -ParentId 1 "Step $i - Substep $j - iteration $k"; start-sleep -m 150
    }
  }
}
```

```Output
Step 1
     Processing
    Step 1 - Substep 2
         Processing
        Step 1 - Substep 2 - Iteration 3
             Processing
```

在此範例中，您可以使用 **ParentId** 參數將輸出縮排，以顯示每個步驟進度中的父/子關聯性。

## PARAMETERS

### -Activity

指定狀態列上方標題中文字的第一行。
此文字說明正在報告其進度的活動。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Completed

指示是否顯示進度列。
如果省略此參數，則會 `Write-Progress` 顯示進度資訊。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CurrentOperation

指定進度列下方的文字行。
此文字說明目前執行的操作。

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

### -Id

指定區別每個進度列的識別碼。 在單一命令中建立超過一個進度列時，請使用此參數。 如果進度列沒有不同的識別碼，它們會重疊，而不會以序列方式顯示。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParentId

指定目前活動的父活動。
如果目前活動沒有父系活動，請使用 -1 作為值。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PercentComplete

指定完成之活動的百分比。
如果完成的百分比不明或不適用，請使用 -1 作為值。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondsRemaining

指定活動完成之前預計的剩餘秒數。
如果剩餘秒數不明或不適用，請使用 -1 作為值。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceId

指定記錄的來源。 您可以使用此取代 **識別碼** ，但不能搭配其他參數（例如 **ParentId** ）使用。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status

指定狀態列上方標題中文字的第二行。
此文字說明活動的目前狀態。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無

`Write-Progress` 不會產生任何輸出。

## 注意

如果沒有顯示進度列，請檢查變數的值 `$ProgressPreference` 。 如果值是設為 SilentlyContinue，就不會顯示進度列。 如需 PowerShell 喜好設定的詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

指令程式的參數會對應至 **ProgressRecord** 類別的屬性。 如需詳細資訊，請參閱 [ProgressRecord 類別](/dotnet/api/system.management.automation.progressrecord)。

## 相關連結

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
