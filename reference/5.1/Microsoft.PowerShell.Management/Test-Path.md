---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: ced5a5db05674c15fefada73ab55969d724117e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203452"
---
# Test-Path

## 概要
判斷路徑的所有元素是否都存在。

## SYNTAX

### 路徑 (預設值)

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>] [-UseTransaction]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### LiteralPath

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>] [-UseTransaction]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## DESCRIPTION

`Test-Path`Cmdlet 會判斷路徑的所有元素是否都存在。 `$True`如果所有專案都存在且遺失任何專案，則會傳回 `$False` 。 它也可以分辨路徑語法是否有效，以及路徑是否會導向至容器或終端機或分葉元素。 如果 `Path` 是空白字元，則 `$False` 會傳回。 如果 `Path` 是空字串、 `$null` 、陣列 `$null` 或空白陣列，則會傳回非終止錯誤。

## 範例

### 範例1：測試路徑

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

此命令會檢查路徑中的所有元素是否都存在，亦即 C：目錄、Documents and Settings 目錄，以及 DavidC 目錄。 如果有任何遺漏，則 Cmdlet 會傳回 `$False` 。
否則，它會傳回 `$True`。

### 範例2：測試組態檔的路徑

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

這些命令會測試 PowerShell 設定檔的路徑。

第一個命令會判斷路徑中的所有元素是否都存在。 第二個命令會判斷路徑的語法是否正確。 在此情況下，路徑為 `$False` ，但語法正確 `$True` 。 這些命令 `$profile` 會使用指向設定檔位置的自動變數（即使設定檔不存在）。

如需自動變數的相關詳細資訊，請參閱 about_Automatic_Variables。

### 範例3：檢查指定類型以外是否有任何檔案

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

此命令會檢查商業大樓目錄中是否有任何檔案，而非 dwg 檔。

此命令會使用 **path** 參數來指定路徑。 由於路徑包含空格，因此路徑會以引號括住。 路徑尾端的星號會指示 Commercial Building 目錄的內容。 使用較長的路徑（例如，），輸入路徑的前幾個字母，然後使用 TAB 鍵來完成路徑。

此命令會指定 **Exclude** 參數，以指定將在評估時省略的檔案。

在此情況下，因為目錄僅包含 dwg 檔案，所以結果為 `$False` 。

### 範例4：檢查檔案

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

此命令會檢查儲存在變數中的路徑是否會 `$profile` 導致檔案。 在此情況下，由於 PowerShell 設定檔是檔案，因此 Cmdlet 會傳回 `.ps1` `$True` 。

### 範例5：檢查登錄中的路徑

這些命令會搭配 `Test-Path` PowerShell 登錄提供者使用。

第一個命令會測試系統上的 **Microsoft PowerShell** 登錄機碼登錄路徑是否正確。 如果 PowerShell 已正確安裝，則 Cmdlet 會傳回 `$True` 。

> [!IMPORTANT]
> `Test-Path` 無法與所有 PowerShell 提供者正常搭配運作。 例如，您可以使用 `Test-Path` 來測試登錄機碼的路徑，但是如果您使用它來測試登錄專案的路徑，它一律會傳回 `$False` ，即使登錄專案存在也一樣。

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### 範例6：測試檔案是否比指定的日期更新

此命令會使用 **NewerThan** 動態參數，來判斷電腦上的 "PowerShell.exe" 檔案是否比「2009年7月13日」更新。

NewerThan 參數只適用於檔案系統磁碟機。

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### 範例7：使用 null 做為值來測試路徑

傳回的錯誤 `null` 、 `null` 或空白陣列的陣列為非終止錯誤。 您可以使用來隱藏它 `-ErrorAction SilentlyContinue` 。 下列範例會顯示傳回錯誤的所有案例 `NullPathNotPermitted` 。

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### 範例8：測試具有空白字元的路徑作為值

為參數提供空白字元字串時 `-Path` ，會傳回 **True** 。 提供空字串時，會傳回 `Test-Path` 錯誤。 下列範例會顯示空白字元和空字串。

```powershell
Test-Path ' '
Test-Path ''
```

```Output
True
Test-Path : Cannot bind argument to parameter 'Path' because it is an empty string.
At line:1 char:11
+ Test-Path ''
+           ~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorEmptyStringNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

## PARAMETERS

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。 若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

指定此 Cmdlet 省略的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 "*.txt"。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

以提供者的格式或語言指定篩選。 此參數的值會限定 **Path** 參數。 篩選的語法 (包括是否使用萬用字元) 取決於提供者。 篩選比其他參數更有效率，因為提供者會在抓取物件時套用，而不是在抓取物件之後篩選物件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

指定此 Cmdlet 測試的路徑。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 "*.txt"。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -IsValid

指出此 Cmdlet 會測試路徑的語法，無論路徑的元素是否存在。 `$True`如果路徑語法有效，則這個 Cmdlet 會傳回，否則會傳回 `$False` 。

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

### -LiteralPath

指定要測試的路徑。 與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含可由 PowerShell 解釋為 escape 序列的字元，您必須將路徑括在單引號中，使其不會被解讀。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewerThan

將時間指定為 **DateTime** 物件。

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OlderThan

將時間指定為 **DateTime** 物件。

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定要測試的路徑。 允許使用萬用字元。 如果路徑包含空格，請將它括在引號中。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -PathType

指定路徑中最後一個元素的類型。 `$True`如果元素是指定的類型，則這個 Cmdlet 會傳回，否則會傳回 `$False` 。 此參數可接受的值為：

- 容器。
  包含其他元素的元素，例如目錄或登錄機碼。
- 葉。
  未包含其他元素 (例如檔案) 的元素。
- 任何。
  容器或分葉。

告知路徑中的最終元素是否為特定類型。

> [!CAUTION]
>
> 最多 PowerShell 版本6.1.2，同時指定 **IsValid** 和 **PathType** 參數時，此 Cmdlet 會 `Test-Path` 忽略 **PathType** 參數，並只驗證語法路徑，而不會驗證路徑類型。
>
> 根據 [問題 #8607](https://github.com/PowerShell/PowerShell/issues/8607)，修正此行為可能是未來版本中的重大變更，其中 **IsValid** 和 **PathType** 參數屬於不同的參數集，因此無法一起使用以避免混淆。

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction

將命令加入使用中交易。 只有交易為處理中狀態時，此參數才有效。 如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。

## 輸出

### System.Boolean

Cmdlet 會傳回 **布林** 值。

## 注意

包含路徑名詞 (Path **Cmdlet 的 Cmdlet** 會 **Path** ) 使用路徑名稱，並傳回所有 PowerShell 提供者都可解讀的精簡格式名稱。 它們是設計用於程式與指令碼，您可以在其中以特定格式顯示所有或部分路徑名稱。
您可以使用 **Dirname** 、 **Normpath** 、 **Realpath** 、 **Join** 或其他路徑操作工具。

`Test-Path`是設計來處理任何提供者所公開的資料。
若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。
如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)
