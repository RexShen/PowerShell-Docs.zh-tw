---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: 3d33f0e3ab859d839b22a49a88860624ae06ddf2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202063"
---
# Remove-Item

## 概要
刪除指定的項目。

## SYNTAX

### 路徑 (預設值)

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

### LiteralPath

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Remove-Item` Cmdlet 會刪除一或多個專案。 由於有許多提供者支援，因此可以刪除許多不同類型的專案，包括檔案、資料夾、登錄機碼、變數、別名及函式。

## 範例

### 範例1：刪除具有任何副檔名的檔案

此範例會從資料夾中刪除名稱包含點 () 的所有檔案 `.` `C:\Test` 。 因為此命令指定一個點，所以此命令不會刪除沒有副檔名的資料夾或檔案。

```powershell
Remove-Item C:\Test\*.*
```

### 範例2：刪除資料夾中的部分檔檔案

這個範例會從目前的資料夾中刪除所有副檔名為的檔案， `.doc` 以及不包含的名稱 `*1*` 。

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

它會使用萬用字元 (`*`) 來指定目前資料夾的內容。 它會使用 **Include** 和 **Exclude** 參數來指定要刪除的檔案。

### 範例3：刪除隱藏的唯讀檔案

此命令會刪除 *隱藏* 和 *唯讀* 的檔案。

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

它會使用 **Path** 參數來指定檔案。 它會使用 **Force** 參數來刪除它。 若無 **強制** ，則無法刪除 _唯讀_ 或 _隱藏_ 的檔案。

### 範例4：以遞迴方式刪除子資料夾中的檔案

此命令會以遞迴方式刪除目前資料夾和所有子資料夾中的所有 CSV 檔案。

因為中的 **遞迴** 參數 `Remove-Item` 有已知的問題，所以此範例中的命令會使用 `Get-ChildItem` 來取得所需的檔案，然後使用管線運算子將它們傳遞給 `Remove-Item` 。

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

在 `Get-ChildItem` 命令中， **Path** 的值為 (`*`) ，代表目前資料夾的內容。 它使用 **Include** 來指定 CSV 檔案類型，並使用 **遞迴** 來使抓取遞迴。 如果您嘗試指定檔案類型的路徑（例如 `-Path *.csv` ），則 Cmdlet 會將搜尋的主旨解釋為沒有子專案的檔案，且 **遞迴** 失敗。

### 範例5：以遞迴方式刪除子機碼

此命令會刪除 "OldApp" 登錄機碼及其所有子機碼和值。 它會使用 `Remove-Item` 來移除索引鍵。 已指定路徑，但會省略選擇性參數名稱 ( **路徑** ) 。

**遞迴** 參數會以遞迴方式刪除 "OldApp" 索引鍵的所有內容。 如果機碼包含子機碼，而您省略了 **遞迴** 參數，系統會提示您確認是否要刪除機碼的內容。

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### 範例6：刪除具有特殊字元的檔案

下列範例示範如何刪除包含特殊字元的檔案，例如方括弧或括弧。

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### 範例7：移除替代資料流程

此範例示範如何使用 Cmdlet 的 **資料流程** 動態參數 `Remove-Item` 來刪除替代資料流程。 Stream 參數是在 Windows PowerShell 3.0 中引進。

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

**Stream** 參數會 `Get-Item` 取得檔案的 **區域。識別碼** 資料流程 `Copy-Script.ps1` 。 `Remove-Item` 使用 **資料流程** 參數來移除 **區域。** 檔案的識別碼資料流程。 最後，此 `Get-Item` Cmdlet 會顯示已刪除的 **區域識別碼** 串流。

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

強制 Cmdlet 移除無法以其他方式變更的專案，例如隱藏或唯讀的檔案，或是唯讀的別名或變數。 Cmdlet 無法移除常數別名或變數。
實作會依提供者而異。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。 即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。

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

### -Path

指定要移除之專案的路徑。
允許使用萬用字元。

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

### -Recurse

指出此 Cmdlet 會刪除指定位置和位置的所有子專案中的專案。

當搭配 **Include** 參數使用時， **遞迴** 參數可能不會刪除所有子資料夾或所有子專案。 這是已知的問題。 若要解決此問題，請嘗試將命令的結果傳送 `Get-ChildItem -Recurse` 至 `Remove-Item` ，如本主題的「範例4」所述。

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

### -Stream

**資料流程** 參數是動態參數，FileSystem 提供者會將其加入至 `Remove-Item` 。
此參數只適用於檔案系統磁碟機。

您可以使用 `Remove-Item` 刪除替代資料流程。 但是，不建議使用這個方法來取代封鎖從網際網路下載之檔案的安全性檢查。 如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。

此參數是在 Windows PowerShell 3.0 引進。

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

### -Confirm

在執行 Cmdlet 前提示您確認。 如需詳細資訊，請參閱下列文章：

- [about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

此 `Remove-Item` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

當您嘗試在不使用 **遞迴** 參數的情況下刪除包含專案的資料夾時，此 Cmdlet 會提示您確認。 使用 `-Confirm:$false` 不會抑制提示。 這是原廠設定。

## 相關連結

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

