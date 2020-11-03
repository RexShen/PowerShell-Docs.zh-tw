---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 859738998de9d2a61a5fb7d9f39ff6ef8b74ad4d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203843"
---
# Clear-History

## 概要
從 PowerShell 會話命令歷程記錄中刪除專案。

## SYNTAX

### IDParameter (預設值)

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandLineParameter

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## DESCRIPTION

`Clear-History` 從 PowerShell 會話刪除命令歷程記錄。 每個 PowerShell 會話都有自己的命令歷程記錄。 若要顯示命令歷程記錄，請使用 `Get-History` Cmdlet。

根據預設，會 `Clear-History` 從 PowerShell 會話刪除整個命令歷程記錄。 您可以使用參數搭配 `Clear-History` 來刪除選取的命令。

`Clear-History` 不會清除 `PSReadLine` 命令歷程記錄檔。 `PSReadLine`模組會儲存歷程記錄檔案，其中包含每個 powershell 會話的每個 powershell 命令。 從 PowerShell 提示字元中，使用鍵盤上的向上和向下箭號來流覽命令歷程記錄。 若要顯示 `PSReadLine` 命令歷程記錄的設定，請使用 `Get-PSReadLineOption` 。
`PSReadLine` 隨附于 PowerShell 5.0 和更新版本。 如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

## 範例

### 範例1：從 PowerShell 會話刪除命令歷程記錄

此命令會從 PowerShell 會話的歷程記錄中刪除所有命令。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。 `Clear-History` 刪除整個命令歷程記錄。 `Get-History` 顯示已更新的命令歷程記錄，並確認已刪除先前的歷程記錄。

### 範例2：刪除最新的命令

此命令會使用 **Count** 和 **最新** 的參數，從 PowerShell 會話的歷程記錄中刪除最新的命令。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。 `Clear-History` 用來刪除命令歷程記錄。 **Count** 參數指定要刪除的命令數目（包含指定的 **識別碼** ）。 **最新** 的參數指定從歷程記錄中清除最新的命令。 `Get-History`顯示已更新的命令歷程記錄，並確認已刪除五個最新的命令， **識別碼 6**  -  **識別碼 10** 。

### 範例3：刪除符合特定準則的命令

此命令會刪除符合命令 **行** 參數所定義之特定準則的命令。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。 `Clear-History` 刪除命令歷程記錄。 命令 **行** 參數 **指定包含說明** 或結尾 **語法** 的命令。 `Get-History` 顯示已更新的命令歷程記錄，並確認已刪除命令 **識別碼 3** 、 **id 5** 、 **id 6** 和 **id 7** 。

### 範例4：依識別碼刪除命令

此命令會使用 **識別碼** 刪除特定的記錄專案。若要刪除多個命令，請提交以逗號分隔的 **識別碼** 清單。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。 `Clear-History` 刪除命令歷程記錄。 **Id** 參數指定要刪除的命令。 `Get-History` 顯示已更新的命令歷程記錄，並確認已刪除 **識別碼 3** 和 **識別碼 5** 。

### 範例5：依識別碼和計數刪除命令

此命令會使用 **Id** 和 **Count** 參數來刪除命令歷程記錄。 命令會以反向順序從指定的 **識別碼** 中刪除，最新到最舊。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

此 `Get-History` Cmdlet 會顯示 PowerShell 會話的歷程記錄。 `Clear-History` 刪除命令歷程記錄。 **Id** 參數指定開頭為 **id 7** 。 **Count** 參數指定要刪除五個命令，內含指定的 **識別碼** 。`Get-History`顯示已更新的命令歷程記錄，並確認已刪除五個命令， **識別碼 3**  -  **識別碼 7** 。

## PARAMETERS

### -CommandLine

從 PowerShell 會話刪除命令歷程記錄。 字串必須完全相符，或使用萬用字元來比對顯示之 PowerShell 會話歷程記錄中的命令 `Get-History` 。 如果您輸入一個以上的字串，則會 `Clear-History` 刪除符合任何字串的命令。 **命令列** 參數可以搭配 **Count** 使用。

針對具有空格的字串，請使用單一引號。 如需詳細資訊，請參閱 [about_Quoting_Rules](About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Count

指定要刪除之記錄專案的數目 `Clear-History` 。 從歷程記錄中最舊的專案開始，依序刪除命令。

**Count** 和 **Id** 參數可以一起使用。 **Count** 參數指定要刪除的命令數目（包含指定的 **識別碼** ）。從指定的 **識別碼** 開始，會以反向順序刪除命令。 例如，如果 **識別碼** 為30且 **計數** 為10，則會 `Clear-History` 刪除專案21到30。

**Count** 和 **命令列** 參數可以一起使用。 **Count** 指定要刪除符合 **命令列** 參數值的命令數目。 這些命令會依順序刪除。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定刪除的命令歷程記錄 **識別碼** `Clear-History` 。 若要顯示 **識別碼** ，請使用 `Get-History` Cmdlet。 **識別碼** 是連續的，而且命令會在 PowerShell 會話中保留其 **識別碼** 號碼。 **Id** 參數可以搭配 **Count** 和 **最新** 使用。

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Newest

使用 **最新** 的參數時，會 `Clear-History` 刪除歷程記錄中的最新專案。 依預設，會 `Clear-History` 刪除歷程記錄中最舊的專案。

**最新** 的參數可以搭配 **Id** 和 **Count** 使用。 **Count** 參數指定要刪除的命令數目（包含指定的 **識別碼** ）。從指定的 **識別碼** 開始，會依順序刪除命令。 例如，如果 **識別碼** 為30且 **計數** 為10，則會 `Clear-History` 刪除30到39的專案。

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

### -Confirm

在執行 Cmdlet 前提示您確認 `Clear-History` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示當 Cmdlet 執行時，會發生什麼事 `Clear-History` 。 Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### 無

您無法透過管道傳送物件至 `Clear-History` 。

## 輸出

### 無

`Clear-History` 不會產生任何輸出。

## 注意

PowerShell 會話歷程記錄是在 PowerShell 會話期間輸入的命令清單。 您可以檢視歷程記錄、新增和刪除命令，以及從歷程記錄執行命令。 如需詳細資訊，請參閱 [about_History](About/about_History.md)。

會話歷程記錄是與 **PSReadLine** 模組所維護的歷程記錄分開管理。
這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。 此 Cmdlet 僅適用于會話歷程記錄。 如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

## 相關連結

[about_History](About/about_History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[about_Quoting_Rules](About/about_Quoting_Rules.md)

[Add-History](Add-History.md)

[Get-History](Get-History.md)

[Invoke-History](Invoke-History.md)

[PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[設定-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)
