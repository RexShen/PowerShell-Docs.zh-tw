---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: 1898d0b80e715c817612b54d795d0c2f57b6c6b7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202092"
---
# Move-Item

## 概要
將項目從某個位置移動到另一個位置。

## SYNTAX

### 路徑 (預設值)

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Move-Item`Cmdlet 會將專案（包括其屬性、內容及子專案）從一個位置移到另一個位置。 移動的位置需由同一個提供者支援。
例如，它可以將檔案或子目錄從一個目錄移至另一個，或將登錄子機碼從一個機碼移至另一個。
當您移動項目後，就會將它加到新位置，並從其原始位置中刪除。

## 範例

### 範例1：將檔案移至另一個目錄，並將它重新命名

此命令會將檔案 `Test.txt` 從 `C:` 磁片磁碟機移至 `E:\Temp` 目錄，並將它重新命名 `test.txt` 為 `tst.txt` 。

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### 範例2：將目錄和其內容移至另一個目錄

此命令會將 `C:\Temp` 目錄和其內容移至 `C:\Logs` 目錄。
"Temp" 目錄及其所有子目錄和檔案都會出現在 "Logs" 目錄中。

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### 範例3：將指定之副檔名的所有檔案從目前目錄移至另一個目錄

此命令會將 `*.txt` 目前 (目錄中的所有文字檔 () ， (`.`) # A5 以點表示 `C:\Logs` 目錄。

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### 範例4：以遞迴方式將指定之副檔名的所有檔案從目前目錄移至另一個目錄

此命令會以遞迴方式將所有文字檔從目前的目錄和所有子目錄移至 "C:\TextFiles" 目錄。

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

此命令會使用 `Get-ChildItem` Cmdlet 來取得目前目錄中的所有子專案， (由點 \[ . \]) 及其子目錄（副檔名為 " *.txt"）。它會使用 **遞迴** 參數來使抓取遞迴，並使用 Include 參數將抓取限制為 "* .txt" 檔案。

管線運算子 (`|`) 將此命令的結果傳送至 `Move-Item` ，這會將文字檔移至 "TextFiles" 目錄。

如果要移至 "C:\Textfiles" 的檔案具有相同的名稱，則會 `Move-Item` 顯示錯誤並繼續進行，但是只會將每個名稱的一個檔案移至 "C:\Textfiles"。
其他檔案仍會留在原始的目錄中。

如果 "Textfiles" 目錄 (或目的地路徑) 的任何其他元素不存在，則命令會失敗。
即使您使用 **Force** 參數，也不會為您建立遺漏的目錄。
`Move-Item` 將第一個專案移至稱為 "Textfiles" 的檔案，然後顯示說明該檔案已存在的錯誤。

此外，根據預設，不 `Get-ChildItem` 會移動隱藏的檔案。
若要移動隱藏的檔案，請使用 **Force** 參數搭配 `Get-ChildItem` 。

> [!NOTE]
> 在 Windows PowerShell 2.0 中，使用 Cmdlet 的 **遞迴** 參數時 `Get-ChildItem` ， **Path** 參數的值必須是容器。
> 請使用 **Include** 參數來指定 .txt 副檔名篩選 (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`)。

### 範例5：將登錄機碼和值移至另一個金鑰

此命令會將 "MyCompany" 登錄機碼中的登錄機碼和值移 `HKLM\Software` 至 "mynewcompany 機" 機碼。
 () 的萬用字元 `*` 表示應移動 "MyCompany" 索引鍵的內容，而不是金鑰本身。
在這個命令中，會省略選擇性的 **路徑** 和 **目的地** 參數名稱。

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### 範例6：將目錄和其內容移至指定目錄的子目錄

此命令會將 "Logs \[ 9 月 \` 6 日 \] " 目錄 (及其內容) 移至 "logs \[ 2006 \] " 目錄。

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

使用 **LiteralPath** 參數而非 **Path** ，因為原始目錄名稱包含左括弧和右括弧字元 ( " \[ " 和 " \] " ) 。
路徑也會括在單引號 (' ') 中，因此不會誤譯倒單引號 (\`)。

**Destination** 參數不需要常值路徑，因為目的地變數也必須括在單引號中，因為它包含可能會誤解的括弧。

## PARAMETERS

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。
> 若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Destination

指定要移動之項目所在位置的路徑。
預設值是目前的目錄。
允許使用萬用字元，但是結果必須指定單一位置。

若要重新命名正在移動的專案，請在 **Destination** 參數的值中指定新名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Exclude

以字串陣列指定此 Cmdlet 在作業中排除的專案。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。 只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

指定要限定 **路徑** 參數的篩選準則。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。 您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。
篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。

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

### -Force

強制執行命令而不要求使用者確認。
實作會依提供者而異。
如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include

以字串陣列指定此 Cmdlet 在作業中納入的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `"*.txt"`。 允許使用萬用字元。 **Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

### -LiteralPath

指定一個或多個位置的路徑。 **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定項目之目前位置的路徑。
預設值是目前的目錄。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Confirm

在執行 Cmdlet 前提示您確認。

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

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至此 Cmdlet。

## 輸出

### 無或表示已移動專案的物件

當您使用 *PassThru* 參數時，此 Cmdlet 會產生代表已移動之專案的物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

- 此 Cmdlet 會在相同提供者所支援的磁片磁碟機之間移動檔案，但它只會在同一個磁片磁碟機內移動目錄。
- 由於 `Move-Item` 命令會移動專案的屬性、內容及子專案，因此所有移動預設都是遞迴的。
- 此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。
  若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。
  如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

