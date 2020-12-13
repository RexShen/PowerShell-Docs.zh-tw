---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: d9c8d13f992e6631ff5982b4a33542c661991562
ms.sourcegitcommit: 7f712e12ec5b3f3f3e695da804b050ea0ce58b3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94661353"
---
# Get-Item

## 概要
取得指定位置的項目。

## SYNTAX

### 路徑 (預設值)

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### LiteralPath

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Item`Cmdlet 會取得指定位置的專案。 除非您使用萬用字元 (`*`) 來要求專案的所有內容，否則它不會在位置取得專案的內容。

PowerShell 提供者會使用此 Cmdlet 來流覽不同類型的資料存放區。

## 範例

### 範例1：取得當前目錄

這個範例會取得當前目錄。 點 ( '. ') 代表目前位置的專案， (不是其內容) 。

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### 範例2：取得目前目錄中的所有專案

這個範例會取得目前目錄中的所有專案。 萬用字元 (`*`) 代表目前專案的所有內容。

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### 範例3：取得磁片磁碟機的目前的目錄

此範例會取得磁片磁碟機的目前的目錄 `C:` 。 抓取的物件僅代表目錄，而非其內容。

```powershell
Get-Item C:\
```

### 範例4：取得指定磁片磁碟機中的專案

此範例會取得磁片磁碟機中的專案 `C:` 。 萬用字元 (`*`) 代表容器中的所有專案，而不只是容器。

```powershell
Get-Item C:\*
```

在 PowerShell 中，使用單一星號 (`*`) 來取得內容，而不是傳統 `*.*` 。 格式會以文字形式來解讀，因此 `*.*` 不會在沒有點的情況下抓取目錄或檔案名。

### 範例5：取得指定之目錄中的屬性

這個範例會取得目錄的 **LastAccessTime** 屬性 `C:\Windows` 。 **LastAccessTime** 只是檔案系統目錄的一個屬性。 若要查看目錄的所有屬性，請輸入 `(Get-Item <directory-name>) | Get-Member` 。

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### 範例6：顯示登錄機碼的內容

此範例會顯示 **Microsoft PowerShell** 登錄機碼的內容。 您可以使用這個指令程式搭配 PowerShell 登錄提供者來取得登錄機碼和子機碼，但您必須使用指令程式 `Get-ItemProperty` 來取得登錄值和資料。

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### 範例7：取得具有排除專案的目錄中的專案

這個範例會取得 Windows 目錄中名稱包含點 () 的專案 `.` ，但開頭不是 `w*` 。此範例僅適用于路徑包含萬用字元 (`*`) 來指定專案內容時。

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### 範例8：取得硬連結資訊

在 PowerShell 6.2 中，已新增替代視圖來取得硬連結的資訊。 若要取得硬連結的資訊，請將輸出輸送至 `Format-Table -View childrenWithHardlink`

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### 範例9：非 Windows 作業系統的輸出

在 Unix 系統上的 PowerShell 7.1 中，此 `Get-Item` Cmdlet 提供類似 Unix 的輸出：

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

現在屬於輸出的新屬性為：

- **UnixMode** 是 Unix 系統上所代表的檔案許可權
- **使用者** 是檔案擁有者
- **群組** 是群組擁有者
- **大小** 是 Unix 系統上表示的檔案或目錄大小

> [!NOTE]
> 這項功能已從實驗性移至 PowerShell 7.1 中的主流。

## PARAMETERS

### -Stream

從檔案中取得指定的替代 NTFS 檔案資料流。 輸入資料流名稱。 支援萬用字元。 若要取得所有資料流程，請使用星號 (`*`) 。 此參數在資料夾中無效。

**Stream** 是動態參數， **FileSystem** 提供者會將它新增至 `Get-Item` Cmdlet。
此參數只適用於檔案系統磁碟機。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
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

指定要限定 **路徑** 參數的篩選準則。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援篩選器的已安裝 PowerShell 提供者。 篩選比其他參數更有效率。 此提供者會在取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。 篩選字串會傳遞至 .NET API 以列舉檔案。 API 僅支援 `*` 和 `?` 萬用字元。

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

指出此 Cmdlet 會取得無法以其他方式存取的專案，例如隱藏的專案。
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

以字串陣列指定此 Cmdlet 在作業中納入的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。 **Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

指定項目的路徑。 此 Cmdlet 會取得指定位置的專案。 允許使用萬用字元。 這個參數是必要參數，但參數名稱 **路徑** 是選擇性的。

使用點 (`.`) 來指定目前的位置。 使用 (`*`) 萬用字元來指定目前位置中的所有專案。

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

### CommonParameters

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至此 Cmdlet。

## 輸出

### System.Object

這個 Cmdlet 會傳回它所取得的物件。 類型是由路徑中的物件類型決定。

## 注意

此 Cmdlet 不會有 **遞迴** 參數，因為它只會取得專案，而不是其內容。
若要以遞迴方式取得專案的內容，請使用 `Get-ChildItem` 。

若要流覽登錄，請使用此 Cmdlet 來取得登錄機碼和， `Get-ItemProperty` 以取得登錄值和資料。 登錄值可視為是登錄機碼的屬性。

此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

