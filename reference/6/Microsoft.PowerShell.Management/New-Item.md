---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 09ed5697299ea2a9f516597df9de44ac714350ed
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202867"
---
# New-Item

## 概要
建立新的項目。

## SYNTAX

### pathSet (預設值)

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### nameSet

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `New-Item` Cmdlet 會建立新的專案，並設定其值。 可以建立的專案類型取決於專案的位置。 例如，在檔案系統中， `New-Item` 建立檔案和資料夾。 在登錄中， `New-Item` 建立登錄機碼和專案。

`New-Item` 也可以設定它所建立之專案的值。 例如，在建立新檔案時， `New-Item` 可以將初始內容新增至檔案。

## 範例

### 範例1：在目前的目錄中建立檔案

此命令會在目前的目錄中建立名為 "testfile1.txt" 的文字檔。 點 ( '. ' **Path** 參數值中的 ) 表示目前的目錄。 在 **Value** 參數後面加上引號的文字會加入檔案中作為內容。

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### 範例2：建立目錄

此命令會在磁片磁碟機中建立名為「日誌」的目錄 `C:` 。 **ItemType** 參數會指定新專案為目錄，而不是檔案或其他檔案系統物件。

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### 範例3：建立設定檔

此命令會在變數所指定的路徑中建立 PowerShell 設定檔 `$profile` 。

您可以使用設定檔來自訂 PowerShell。 `$profile` 是自動 (內建的) 變數，可儲存 "CurrentUser/CurrentHost" 設定檔的路徑和檔案名。 根據預設，設定檔並不存在，即使 PowerShell 會儲存它的路徑和檔案名也一樣。

在這個命令中， `$profile` 變數代表檔案的路徑。 **ItemType** 參數會指定命令建立檔案。 **Force** 參數可讓您在設定檔路徑中建立檔案，即使路徑中的目錄不存在也一樣。

建立設定檔之後，您可以在設定檔中輸入別名、函式和腳本來自訂您的 shell。

如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) 和 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### 範例4：在不同的目錄中建立目錄

此範例會在 "C:\PS-Test" 目錄中建立新的腳本目錄。

新目錄專案的名稱 "script" 會包含在 **Path** 參數的值中，而不是在 **name** 的值中指定。 如語法所指示，任何一個命令格式都是有效的。

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### 範例5：建立多個檔案

此範例會在兩個不同的目錄中建立檔案。 因為 **Path** 接受多個字串，所以您可以使用它來建立多個專案。

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### 範例6：使用萬用字元在多個目錄中建立檔案

此 `New-Item` Cmdlet 支援 **Path** 參數中的萬用字元。 下列命令會 `temp.txt` 在 **Path** 參數中以萬用字元指定的所有目錄中建立檔案。

```powershell
Get-ChildItem -Path C:\Temp\
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d-----        5/15/2019   6:45 AM        1   One
d-----        5/15/2019   6:45 AM        1   Two
d-----        5/15/2019   6:45 AM        1   Three
```

```powershell
New-Item -Path * -Name temp.txt -ItemType File | Select-Object FullName
```

```Output
FullName
--------
C:\Temp\One\temp.txt
C:\Temp\Three\temp.txt
C:\Temp\Two\temp.txt
```

此 `Get-ChildItem` Cmdlet 會在目錄底下顯示三個目錄 `C:\Temp` 。 使用萬用字元時， `New-Item` Cmdlet 會 `temp.txt` 在目前的目錄下的所有目錄中建立檔案。 此 `New-Item` Cmdlet 會輸出您建立的專案（以管線傳送至）， `Select-Object` 以確認新建立之檔案的路徑。

### 範例7：建立檔案或資料夾的符號連結

這個範例會在目前的資料夾中建立 Notice.txt 檔案的符號連結。

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

在此範例中， **Target** 是 **Value** 參數的別名。 符號連結的目標可以是相對路徑。 在 PowerShell 6.2 之前，目標必須是完整路徑。

> [!CAUTION]
> 如果您要建立 **>symboliclink** 至 Windows 上的資料夾，您必須使用完整路徑。 如果您使用相對路徑，則會將連結建立為檔案類型連結，而不是目錄類型的連結。

### 範例8：使用-Force 參數嘗試重新建立資料夾

這個範例會建立一個資料夾，其中包含內的檔案。 然後，嘗試使用建立相同的資料夾 `-Force` 。 它不會覆寫資料夾，只會傳回現有的資料夾物件，並建立不完整的檔案。

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### 範例9：使用-Force 參數來覆寫現有的檔案

這個範例會建立具有值的檔案，然後使用重新建立檔案 `-Force` 。 這會覆寫現有的檔案，而其內容將會遺失，因為 length 屬性可以看到它。

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> 搭配使用 `New-Item` 參數與 `-Force` 參數來建立登錄機碼時，命令的行為會與覆寫檔案時相同。 如果登錄機碼已經存在，則會以空白的登錄機碼覆寫機碼和所有屬性和值。

## PARAMETERS

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。 若要在執行這個 Cmdlet 時模擬另一位使用者或提升您的認證，請使用 `Invoke-Command` 。

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

### -Force

強制這個 Cmdlet 建立寫入現有唯讀專案的專案。 實作會依提供者而異。 即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。

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

### -ItemType

指定新項目的提供者指定類型。 此參數的可用值取決於您目前使用的提供者。

如果您的位置位於 `FileSystem` 磁片磁碟機中，則允許下列值：

- 檔案
- 目錄
- >symboliclink
- 接合
- 硬

> [!NOTE]
> `SymbolicLink`在 Windows 上建立類型需要以系統管理員的許可權提升許可權。 不過，已啟用開發人員模式的 Windows 10 (組建14972或) 更新版本，不再需要提高建立符號連結的許可權。

在 `Certificate` 磁片磁碟機中，這些是您可以指定的值：

- 憑證提供者
- 憑證
- 市集
- StoreLocation

如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定新項目的名稱。 您可以在 [ **名稱** ] 或 [ **路徑** ] 參數值中指定新專案的名稱，也可以在 [ **名稱** ] 或 [ **路徑** ] 值中指定新專案的路徑。 使用 **Name** 參數傳遞的專案名稱會與 **Path** 參數的值相對應。

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定新專案的位置路徑。 當省略 **路徑** 時，預設值為目前的位置。 您可以在 [ **名稱** ] 中指定新專案的名稱，或將它包含在 **Path** 中。 使用 **Name** 參數傳遞的專案名稱會與 **Path** 參數的值相對應。

針對此 Cmdlet， **Path** 參數的運作方式就像其他 Cmdlet 的 **LiteralPath** 參數。
萬用字元不會被解讀。 所有字元都會傳遞至位置的提供者。 提供者可能不支援所有字元。 例如，您無法建立包含星號 (`*`) 字元的檔案名。

```yaml
Type: System.String[]
Parameter Sets: pathSet, nameSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Value

指定新項目的值。 您也可以使用管線將值傳送至 `New-Item` 。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System.Object

您可以使用管線將新專案的值傳送至此 Cmdlet。

## 輸出

### System.Object

這個 Cmdlet 會傳回它所建立的專案。

## 注意

`New-Item` 的設計目的是要與任何提供者公開的資料搭配使用。 若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
