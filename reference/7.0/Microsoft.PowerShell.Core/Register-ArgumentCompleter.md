---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: 0e0b5fcd99372d699bd6250383adc85b3a5f8847
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201567"
---
# Register-ArgumentCompleter

## 概要

註冊自訂引數完成器。

## SYNTAX

### NativeSet

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### PowerShellSet

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## DESCRIPTION

此 `Register-ArgumentCompleter` Cmdlet 會註冊自訂引數完成器。 引數完成器可讓您在執行時間為您指定的任何命令提供動態 tab 鍵自動完成。

## 範例

### 範例1：註冊自訂引數完成器

下列範例會針對 Cmdlet 的 **Id** 參數註冊引數完成器 `Set-TimeZone` 。

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

第一個命令會建立腳本區塊，該區塊會採用使用者按下 <kbd>Tab 鍵</kbd>時所傳入的必要參數。如需詳細資訊，請參閱 **ScriptBlock** 參數描述。

在腳本區塊中，會使用 Cmdlet 抓取 **識別碼** 的可用值 `Get-TimeZone` 。 每個時區的 **識別碼** 屬性都會輸送至 `Where-Object` Cmdlet。 指令 `Where-Object` 程式會篩選出不是以提供的值開頭的任何識別碼 `$wordToComplete` ，代表使用者在按下 <kbd>Tab 鍵</kbd>之前所輸入的文字。篩選的識別碼會以管線傳送至 `For-EachObject` Cmdlet，此 Cmdlet 會將每個值括在引號中（如果值包含空格）。

第二個命令會藉由傳遞 scriptblock、 **ParameterName** **識別碼** 和 **CommandName** 來註冊引數完成器 `Set-TimeZone` 。

### 範例2：將詳細資料新增至您的 tab 鍵自動完成值

下列範例會覆寫 Cmdlet **Name** 參數的 tab 鍵自動完成 `Stop-Service` ，而且只會傳回執行中的服務。

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

第一個命令會建立腳本區塊，該區塊會採用使用者按下 <kbd>Tab 鍵</kbd>時所傳入的必要參數。如需詳細資訊，請參閱 **ScriptBlock** 參數描述。

在腳本區塊中，第一個命令會使用 Cmdlet 來抓取所有正在執行的服務 `Where-Object` 。 這些服務會透過管道傳送至 `ForEach-Object` Cmdlet。 此 `ForEach-Object` Cmdlet 會建立新的 [CompletionResult](/dotnet/api/system.management.automation.completionresult) 物件，並以管線變數) 所表示的目前服務 (名稱填入該物件 `$_.Name` 。

**CompletionResult** 物件可讓您針對每個傳回的值提供其他詳細資料：

- **completionText** (字串) -要當做自動完成結果使用的文字。 這是傳送至命令的值。
- **listItemText** (字串) -要在清單中顯示的文字，例如使用者按下 <kbd>Ctrl</kbd> + <kbd>空格鍵</kbd>時。 這僅供顯示，且在選取時不會傳遞至命令。
- **resultType** ( [CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) -完成結果的類型。
- **工具提示** (字串) -工具提示的文字，其中包含有關物件的詳細資料。
  當使用者在按下<kbd>Ctrl</kbd>空格鍵之後選取專案時，就會看到這種情況 + <kbd> </kbd>。

最後一個命令會示範已停止的服務仍然可以手動傳遞給 `Stop-Service` Cmdlet。 Tab 鍵自動完成是唯一受影響的層面。

### 範例3：註冊自訂原生引數完成器

您可以使用 **原生** 參數來提供原生命令的 tab 鍵自動完成。 下列範例會將命令列介面的 tab 鍵自動完成新增 `dotnet` (CLI) 。

> [!NOTE]
> 此 `dotnet complete` 命令僅適用于2.0 版和更高版本的 dotnet cli。

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

第一個命令會建立腳本區塊，該區塊會採用使用者按下 <kbd>Tab 鍵</kbd>時所傳入的必要參數。如需詳細資訊，請參閱 **ScriptBlock** 參數描述。

在腳本區塊中， `dotnet complete` 命令是用來執行 tab 鍵自動完成。
結果會輸送到 Cmdlet，以 `ForEach-Object` 使用 [CompletionResult](/dotnet/api/system.management.automation.completionresult)類別的 **新** 靜態方法來為每個值建立新的 **CompletionResult** 物件。

## PARAMETERS

### -CommandName

以陣列的形式指定命令的名稱。

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -原生

表示引數完成器適用于 PowerShell 無法完成參數名稱的原生命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParameterName

指定要完成其引數的參數名稱。 指定的參數名稱不可以是列舉值，例如 Cmdlet 的 **ForegroundColor** 參數 `Write-Host` 。

如需列舉的詳細資訊，請參閱 [about_Enum](./About/about_Enum.md)。

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

指定要執行的命令以執行 tab 鍵自動完成。 您提供的腳本區塊應該會傳回完成輸入的值。 腳本區塊必須使用管線 (`ForEach-Object` 、等等 `Where-Object` ) 或另一個適當的方法來展開值。 傳回值陣列會導致 PowerShell 將整個陣列視為 **一個** tab 鍵自動完成值。

腳本區塊必須以下列指定的順序接受下列參數。 參數的名稱並不重要，因為 PowerShell 會依位置傳遞值。

- `$commandName` (位置 0) -此參數會設定為腳本區塊提供 tab 鍵自動完成之命令的名稱。
- `$parameterName` (位置 1) -此參數會設定為其值需要 tab 鍵自動完成的參數。
- `$wordToComplete` (位置 2) -此參數會設定為使用者在按下 <kbd>Tab 鍵</kbd>之前所提供的值。您的腳本區塊應該使用此值來判斷 tab 鍵自動完成值。
- `$commandAst` (位置 3) -這個參數會設定為目前輸入行 (AST) 的抽象語法樹狀目錄。 如需詳細資訊，請參閱 [Ast 類別](/dotnet/api/system.management.automation.language.ast)。
- `$fakeBoundParameters` (位置 4) - `$PSBoundParameters` 在使用者按下索引標籤之前，此參數會設定為包含 Cmdlet 之<kbd>Tab</kbd>的雜湊表。如需詳細資訊，請參閱[about_Automatic_Variables](./About/about_Automatic_Variables.md)。

當您指定 **原生** 參數時，腳本區塊必須以指定的順序採用下列參數。 參數的名稱並不重要，因為 PowerShell 會依位置傳遞值。

- `$wordToComplete` (位置 0) -此參數會設定為使用者在按下 <kbd>Tab 鍵</kbd>之前所提供的值。您的腳本區塊應該使用此值來判斷 tab 鍵自動完成值。
- `$commandAst` (位置 1) -這個參數會設定為目前輸入行 (AST) 的抽象語法樹狀目錄。 如需詳細資訊，請參閱 [Ast 類別](/dotnet/api/system.management.automation.language.ast)。
- `$cursorPosition` (位置 2) -當使用者 <kbd>按下索引</kbd>標籤時，此參數會設定為游標的位置。

您也可以將 **ArgumentCompleter** 提供為參數屬性。 如需詳細資訊，請參閱 [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](./About/about_CommonParameters.md)。

## 輸入

### 無

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

## 相關連結
