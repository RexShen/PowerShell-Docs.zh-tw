---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 97d342d9f5d7227fb831794055c2cfa75b8cf765
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208788"
---
# Set-PSReadLineKeyHandler

## 概要
將索引鍵系結至使用者定義或 PSReadLine 的索引鍵處理函式。

## SYNTAX

### ScriptBlock

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### 函式

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## DESCRIPTION

`Set-PSReadLineKeyHandler`Cmdlet 會在按下按鍵或按鍵序列時自訂結果。 透過使用者定義的金鑰系結，您幾乎可以從 PowerShell 腳本內進行任何可能的作業。

## 範例

### 範例1：將箭號系結至函式

此命令會將向上箭號系結至 **HistorySearchBackward** 函式。 此函式會搜尋命令列的命令歷程記錄，其開頭為命令列的目前內容。

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### 範例2：將索引鍵系結至腳本區塊

這個範例會示範如何使用單一索引鍵來執行命令。 此命令會將金鑰系結 `Ctrl+B` 至清除該行的腳本區塊、插入 "build" 一字，然後接受該行。

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## PARAMETERS

### -BriefDescription

按鍵系結的簡短描述。 Cmdlet 會顯示此描述 `Get-PSReadLineKeyHandler` 。

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -弦

要系結至函數或腳本區塊的索引鍵或索引鍵序列。 使用單一字串來指定單一系結。 如果系結是索引鍵的序列，請以逗號分隔索引鍵，如下列範例所示：

`Ctrl+X,Ctrl+L`

此參數接受字串陣列。 每個字串都是個別的系結，而不是單一系結的索引鍵序列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

指定 Cmdlet 輸出中可見的按鍵系結更詳細描述 `Get-PSReadLineKeyHandler` 。

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Function

指定 PSReadLine 所提供之現有金鑰處理常式的名稱。 此參數可讓您重新系結現有的金鑰系結，或系結目前未系結的處理常式。

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

指定輸入弦時要執行的腳本區塊值。 PSReadLine 會將一或兩個參數傳遞至這個腳本區塊。 第一個參數是 **ConsoleKeyInfo** 物件，代表按下的按鍵。 第二個引數可以是任何物件（視內容而定）。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

指定要套用系結的 vi 模式。

有效值為：

- 插入
- Command

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[移除-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[PSReadLineOption](Get-PSReadLineOption.md)

[設定-PSReadLineOption](Set-PSReadLineOption.md)

