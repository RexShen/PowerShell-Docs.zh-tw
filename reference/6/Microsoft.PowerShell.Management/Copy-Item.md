---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: 0aeebac75c5a84fd78056954d7178de1dbac1460
ms.sourcegitcommit: 33ac34789e86ffb4e7e69453ae38fc0bd24933dd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "93206163"
---
# Copy-Item

## 概要
將項目從某個位置複製到另一個位置。

## SYNTAX

### 路徑 (預設值)

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### LiteralPath

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## DESCRIPTION

`Copy-Item`Cmdlet 會將專案從某個位置複製到相同命名空間中的另一個位置。
比方說，它可以將檔案複製到資料夾，但它無法將檔案複製到憑證磁片磁碟機。

此 Cmdlet 不會剪下或刪除複製的專案。 Cmdlet 可以複製的特定專案需視公開專案的 PowerShell 提供者而定。 例如，它可以在檔案系統磁片磁碟機中複製檔案和目錄，以及在登錄磁片磁碟機中複製登錄機碼和專案。

這個 Cmdlet 可以在同一個命令中複製及重新命名專案。 若要重新命名專案，請在 **Destination** 參數的值中輸入新的名稱。 若要重新命名專案但不復制它，請使用 `Rename-Item` Cmdlet。

## 範例

### 範例1：將檔案複製到指定的目錄

此範例會將檔案複製 `mar1604.log.txt` 到 `C:\Presentation` 目錄。 不會刪除原始檔案。

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### 範例2：將目錄內容複寫到現有的目錄

此範例會將目錄的內容複寫 `C:\Logfiles` 到現有的 `C:\Drawings` 目錄。 `Logfiles`不會複製目錄。

如果 `Logfiles` 目錄包含子目錄中的檔案，則會複製這些子目錄的檔案樹狀結構不變。 依預設， **Container** 參數會設定為 **True** ，以保留目錄結構。

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> 如果您需要 `Logfiles` 在複本中包含目錄，請 `\*` 從 **路徑** 中移除。
> 例如：
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### 範例3：將目錄和內容複寫到新的目錄

此範例會複製 `C:\Logfiles` 來原始目錄的內容，並建立新的目的地目錄。 新的目的地目錄 `\Logs` 是在中建立 `C:\Drawings` 。

若要包含來原始目錄的名稱，請複製到現有的目的地目錄，如 **範例 2** 所示。 或者，將新的目的地目錄命名為與來原始目錄相同的名稱。

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> 如果 **路徑** 包含 `\*` ，所有目錄的檔案內容（包括子目錄樹狀目錄）都會複製到新的目的地目錄。 例如：
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### 範例4：將檔案複製到指定的目錄，並將檔案重新命名

此範例會使用 `Copy-Item` Cmdlet 將 `Get-Widget.ps1` 腳本從 `\\Server01\Share` 目錄複寫到 `\\Server12\ScriptArchive` 目錄。 在複製作業過程中，命令會將專案名稱從變更 `Get-Widget.ps1` 為 `Get-Widget.ps1.txt` ，因此可以附加至電子郵件訊息。

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### 範例5：將檔案複製到遠端電腦

使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。

`Copy-Item`Cmdlet 會 `test.log` `D:\Folder001` `C:\Folder001_Copy` 使用儲存在變數中的會話資訊，從資料夾將資料夾複製到遠端電腦上的資料夾 `$Session` 。 不會刪除原始檔案。

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### 範例6：將資料夾複製到遠端電腦

使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。

此 `Copy-Item` Cmdlet 會 `D:\Folder002` `C:\Folder002_Copy` 使用儲存在變數中的會話資訊，將資料夾複製到遠端電腦上的目錄 `$Session` 。 任何子資料夾或檔案都不會在不使用 **遞迴** 參數的情況下複製。
`Folder002_Copy`如果資料夾還不存在，此作業會建立資料夾。

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### 範例7：以遞迴方式將資料夾的整個內容複寫到遠端電腦

使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。

此 `Copy-Item` Cmdlet 會 `D:\Folder003` `C:\Folder003_Copy` 使用儲存在變數中的會話資訊，將資料夾中的整個內容複寫到遠端電腦上的目錄 `$Session` 。 這些子資料夾的檔案樹狀結構會原封不動地複製。 `Folder003_Copy`如果資料夾還不存在，此作業會建立資料夾。

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### 範例8：將檔案複製到遠端電腦，然後重新命名檔案

使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。

`Copy-Item`Cmdlet 會 `scriptingexample.ps1` `D:\Folder004` `C:\Folder004_Copy` 使用儲存在變數中的會話資訊，從資料夾將資料夾複製到遠端電腦上的資料夾 `$Session` 。 在複製作業過程中，命令會將專案名稱從變更 `scriptingexample.ps1` 為 `scriptingexample_copy.ps1` ，因此可以附加至電子郵件訊息。 不會刪除原始檔案。

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### 範例9：將遠端檔案複製到本機電腦

使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。

`Copy-Item`Cmdlet 會 `test.log` `C:\MyRemoteData\` `D:\MyLocalData` 使用儲存在變數中的會話資訊，從遠端複製到本機資料夾 `$Session` 。 不會刪除原始檔案。

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### 範例10：將遠端資料夾的整個內容複寫到本機電腦

使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。

此 `Copy-Item` Cmdlet 會 `C:\MyRemoteData\scripts` `D:\MyLocalData` 使用儲存在變數中的會話資訊，將遠端資料夾中的整個內容複寫到本機資料夾 `$Session` 。 如果 scripts 資料夾包含子資料夾中的檔案，則會複製這些子資料夾的檔案樹狀結構不變。

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### 範例11：以遞迴方式將遠端資料夾的整個內容複寫到本機電腦

使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。

此 `Copy-Item` Cmdlet 會 `C:\MyRemoteData\scripts` `D:\MyLocalData\scripts` 使用儲存在變數中的會話資訊，將遠端資料夾中的整個內容複寫到本機資料夾 `$Session` 。 因為使用了 **遞迴** 參數，所以作業會建立腳本資料夾（如果尚未存在）。 如果 scripts 資料夾包含子資料夾中的檔案，則會複製這些子資料夾的檔案樹狀結構不變。

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### 範例12：以遞迴方式將檔案從資料夾樹狀結構複製到目前的資料夾

此範例示範如何將多層的資料夾結構中的檔案複製到單一的一般資料夾中。
前三個命令會顯示現有的資料夾結構，以及兩個檔案的內容，這兩個都是名稱 `file3.txt` 。

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

`Copy-Item`Cmdlet 的 **容器** 參數設定為 `$false` 。 這會導致複製源資料夾的內容，但不會保留資料夾結構。 請注意，在目的資料夾中會覆寫具有相同名稱的檔案。

## PARAMETERS

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

### -Container

指出此 Cmdlet 會在複製作業期間保留容器物件。 依預設， **Container** 參數會設定為 **True** 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

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

指定新位置的路徑。 預設值是目前的目錄。

若要重新命名複製的專案，請在 **Destination** 參數的值中指定新名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
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

指出此 Cmdlet 會複製無法以其他方式變更的專案，例如複製唯讀檔案或別名。

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

### -FromSession

指定要從中複製遠端檔案的 **PSSession** 物件。 當您使用這個參數時， **Path** 和 **LiteralPath** 參數會參考遠端電腦上的本機路徑。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

傳回代表您正在使用之專案的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

以字串陣列指定要複製之專案的路徑。 允許使用萬用字元。

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

指出此 Cmdlet 會執行遞迴複製。

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

### -ToSession

指定要將遠端檔案複製到其中的 **PSSession** 物件。 當您使用此參數時， **目的地** 參數會參考遠端電腦上的本機路徑。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 不會執行此 Cmdlet。

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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至此 Cmdlet。

## 輸出

### 無或代表複製專案的物件

當您使用 **PassThru** 參數時，此 Cmdlet 會傳回代表所複製專案的物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Clear-Item](Clear-Item.md)

[Get-Item](Get-Item.md)

[Get-PSProvider](Get-PSProvider.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)
