---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: b318abb06d36be5e28b9dcc3dc62fd4a70ab38fb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204071"
---
# Clear-Content

## 概要
刪除項目的內容，但不會刪除項目。

## SYNTAX

### 路徑 (預設值)

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

### LiteralPath

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

## DESCRIPTION

此 `Clear-Content` Cmdlet 會刪除專案的內容，例如刪除檔案中的文字，但不會刪除專案。
因此，項目會存在，但會是空的。
`Clear-Content`類似于 `Clear-Item` ，但它適用于具有內容的專案，而不是具有值的專案。

## 範例

### 範例1：從目錄中刪除所有內容

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

此命令刪除 SmpUsers 目錄之所有子目錄中的 "init.txt" 檔案的所有內容。
檔案不會被刪除，但會是空的。

### 範例2：使用萬用字元刪除所有檔案的內容

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

此命令刪除目前目錄中副檔名為 ".log" 之所有檔案的內容，包括具有唯讀屬性的檔案。
路徑中的星號 (\*) 代表目前目錄中的所有項目。
**Force** 參數可讓命令在唯讀檔案上生效。
使用篩選器，將命令限制為副檔名為 .log 的檔案，而不是 \* 在路徑中指定. log，讓作業更快。

### 範例3：清除資料流程中的所有資料

此範例示範 Cmdlet 如何 `Clear-Content` 從替代資料流程清除內容，同時讓資料流程保持不變。

第一個命令會使用 `Get-Content` Cmdlet 來取得 Copy-Script.ps1 檔案中的區域識別碼串流，該檔案是從網際網路下載。

第二個命令會使用 `Clear-Content` Cmdlet 來清除內容。

第三個命令重複第一個命令。 它會確認內容已清除，但資料流程仍然存在。 如果資料流程已刪除，則命令會產生錯誤。

您可以使用像這樣的方法來清除替代資料流程的內容。 但是，不建議使用這個方法來取代封鎖從網際網路下載之檔案的安全性檢查。 如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。

```powershell
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
[ZoneTransfer]
ZoneId=3
```

```powershell
Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output

```

## PARAMETERS

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。 若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 Invoke 命令。

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

### -Exclude

以字串陣列指定此 Cmdlet 從內容路徑省略的字串。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

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

以提供者的格式或語言指定篩選。
此參數的值會限定 **Path** 參數。
篩選的語法 (包括是否使用萬用字元) 取決於提供者。
篩選比其他參數更有效率，因為提供者會在抓取物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。

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

以字串陣列指定此 Cmdlet 所清除的內容。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

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

指定要從中刪除內容之項目的路徑。
與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

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

### -Path

指定要從中刪除內容之項目的路徑。
允許使用萬用字元。
路徑需為項目的路徑，而非容器的路徑。
例如，您必須指定一或多個檔案的路徑，而非目錄的路徑。
允許使用萬用字元。
此為必要參數，但是參數名稱 ("Path") 為選擇性。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Stream

指定內容的替代資料流程。
如果資料流程不存在，此 Cmdlet 會建立該資料流程。
不支援萬用字元。

**Stream** 是動態參數，FileSystem 提供者會將其加入至 `Clear-Content` 。
此參數只適用於檔案系統磁碟機。

您可以使用 `Clear-Content` Cmdlet 來變更區域的內容。識別碼替代資料流程。
不過，我們不建議您這樣做，以排除封鎖從網際網路下載之檔案的安全性檢查。
如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。

此參數是在 Windows PowerShell 3.0 引進。

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

### -UseTransaction

將命令加入使用中交易。
只有交易為處理中狀態時，此參數才有效。
如需詳細資訊，請參閱 [about_transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。

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

### 無

您無法透過管道傳送物件至 `Clear-Content` 。

## 輸出

### 無

此 Cmdlet 不會傳回任何物件。

## 注意

您可以搭配 `Clear-Content` PowerShell FileSystem 提供者和其他操作內容的提供者使用。
若要清除不被視為內容的專案，例如 PowerShell 憑證或登錄提供者所管理的專案，請使用 `Clear-Item` 。

此 `Clear-Content` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。
若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。
如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Add-Content](Add-Content.md)

[Get-Content](Get-Content.md)

[Get-Item](Get-Item.md)

[Set-Content](Set-Content.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
