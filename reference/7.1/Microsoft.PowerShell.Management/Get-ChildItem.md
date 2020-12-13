---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: 0bcd46e49559ad625621a7ff81162af695f6f93c
ms.sourcegitcommit: 7f712e12ec5b3f3f3e695da804b050ea0ce58b3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94661319"
---
# Get-ChildItem

## 概要

取得一或多個指定之位置中的項目與子項目。

## SYNTAX

### Items (預設值)

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### LiteralItems

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## DESCRIPTION

`Get-ChildItem`Cmdlet 會取得一或多個指定位置中的專案。 如果項目是容器，它便會取得容器內的項目，稱為子項目。 您可以使用 **遞迴** 參數來取得所有子容器中的專案，並使用 **Depth** 參數來限制要遞迴的層級數目。

`Get-ChildItem` 不顯示空的目錄。 當 `Get-ChildItem` 命令包含 **深度** 或 **遞迴** 參數時，輸出中不會包含空的目錄。

位置是 `Get-ChildItem` 由 PowerShell 提供者所公開。 位置可以是檔案系統目錄、登錄 hive 或憑證存放區。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 範例

### 範例1：從檔案系統目錄取得子專案

此範例會從檔案系統目錄取得子專案。 檔案名和子目錄名稱隨即顯示。 針對空的位置，此命令不會傳回任何輸出，並返回 PowerShell 提示字元。

此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 `C:\Test` 。
`Get-ChildItem` 在 PowerShell 主控台中顯示檔案和目錄。

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

依預設，會 `Get-ChildItem` 列出 (**屬性**) 、 **LastWriteTime**、檔案大小 (**長度**) 和專案 **名稱** 的模式。 **模式** 屬性中的字母可解讀如下：

- `l` (連結) 
- `d` (directory) 
- `a` (封存) 
- `r` (唯讀) 
- `h` (隱藏) 
- `s` (系統) 。

如需模式旗標的詳細資訊，請參閱 [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression)。

### 範例2：取得目錄中的子專案名稱

此範例只會列出目錄中專案的名稱。

此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 `C:\Test` 。 **Name** 參數只會傳回指定路徑中的檔案或目錄名稱。

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### 範例3：取得目前目錄和子目錄中的子專案

此範例會顯示位於目前的目錄及其子目錄中的 **.txt 檔案。**

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定 `C:\Test\*.txt` 。 **路徑** 使用星號 (`*`) 萬用字元來指定副檔名為副檔名的所有檔案 `.txt` 。 **遞迴** 參數會搜尋 **路徑** 目錄的子目錄，如 **目錄：** 標題所示。 **Force** 參數 `hiddenfile.txt` 會顯示具有 **h** 模式的隱藏檔案。

### 範例4：使用 Include 參數取得子專案

在此範例中，會 `Get-ChildItem` 使用 **Include** 參數，從 **Path** 參數所指定的目錄中尋找特定的專案。

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 **C:\Test**。 **Path** 參數包含尾端星號 (`*`) 萬用字元來指定目錄的內容。
**Include** 參數使用星號 (`*`) 萬用字元來指定副檔名為 **.txt** 的所有檔案。

使用 **Include** 參數時， **Path** 參數需要尾端星號 (`*`) 萬用字元來指定目錄的內容。 例如 `-Path C:\Test\*`。

- 如果將 **遞迴** 參數加入至命令，則 Path 參數中的尾端星號 (`*`) 是選擇性的。 **遞迴** 參數會從 **路徑** 目錄及其子目錄中取得專案。 例如， `-Path C:\Test\ -Recurse -Include *.txt`
- 如果尾端的星號 (`*`) 不包含在 **Path** 參數中，則此命令不會傳回任何輸出，並返回 PowerShell 提示字元。 例如 `-Path C:\Test\`。

### 範例5：使用 Exclude 參數取得子專案

範例的輸出會顯示目錄 **C:\Test\Logs** 的內容。 輸出是其他使用 **Exclude** 和 **遞迴** 參數之命令的參考。

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 `C:\Test\Logs` 。
**Exclude** 參數會使用星號 (`*`) 萬用字元來指定以或開頭的任何檔案或目錄 ，並從輸出中排除。

使用 **Exclude** 參數時， `*` **Path** 參數中 () 的尾端星號是選擇性的。 例如，`-Path C:\Test\Logs` 或 `-Path C:\Test\Logs\*`。

- 如果尾端星號 (`*`) 不包含在 **path** 參數中，就會顯示 **path** 參數的內容。 例外狀況是符合 **排除** 參數值的檔案名或子目錄名稱。
- 如果 `*` **path** 參數中包含尾端的星號 () ，命令就會 recurses 至 **path** 參數的子目錄。 例外狀況是符合 **排除** 參數值的檔案名或子目錄名稱。
- 如果將 **遞迴** 參數加入至命令，則無論 **Path** 參數是否包含尾端星號 () ，遞迴輸出都會相同 `*` 。

### 範例6：從登錄 hive 取得登錄機碼

這個範例會從取得所有的登錄機碼 `HKEY_LOCAL_MACHINE\HARDWARE` 。

`Get-ChildItem` 使用 **Path** 參數指定登錄機碼 `HKLM:\HARDWARE` 。 Hive 的路徑和最上層的登錄機碼會顯示在 PowerShell 主控台中。

如需詳細資訊，請參閱 [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)。

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

第一個命令顯示登錄機碼的內容 `HKLM:\HARDWARE` 。 **Exclude** 參數會告訴您不要傳回以開頭的任何子機碼 `Get-ChildItem` `D*` 。 目前， **Exclude** 參數只適用于子機碼，而不是專案屬性。

### 範例7：取得具有程式碼簽署授權單位的所有憑證

此範例會取得 PowerShell **Cert：** 磁片磁碟機中具有程式碼簽署授權單位的每個憑證。

此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定 **Cert：** provider。 **遞迴** 參數會搜尋 **路徑** 及其子目錄所指定的目錄。 **CodeSigningCert** 參數只會取得具有程式碼簽署授權單位的憑證。

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

如需有關憑證提供者和 Cert：磁片磁碟機的詳細資訊，請參閱 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。

### 範例8：使用 Depth 參數取得專案

此範例會顯示目錄及其子目錄中的專案。 **Depth** 參數會決定要包含在遞迴中的子目錄層級數目。 空白目錄會從輸出中排除。

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定 **C:\Parent**。 **Depth** 參數會指定兩個層級的遞迴。 `Get-ChildItem` 顯示 **Path** 參數所指定之目錄的內容，以及兩個子目錄層級。

### 範例9：取得永久連結資訊

在 PowerShell 6.2 中，已新增替代的視圖來取得永久連結資訊。

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

### 範例9：非 Windows 作業系統的輸出

在 Unix 系統上的 PowerShell 7.1 中， `Get-ChildItem` 提供類似 Unix 的輸出：

```powershell
PS> Get-ChildItem /etc/r*
```

```Output
    Directory: /etc

UnixMode   User Group    LastWriteTime Size Name
--------   ---- -----    ------------- ---- ----
drwxr-xr-x root wheel  9/30/2019 19:19  128 racoon
-rw-r--r-- root wheel  9/26/2019 18:20 1560 rc.common
-rw-r--r-- root wheel  7/31/2017 17:30 1560 rc.common~previous
-rw-r--r-- root wheel  9/27/2019 20:34 5264 rc.netboot
lrwxr-xr-x root wheel  11/8/2019 15:35   22 resolv.conf -> /private/var/run/resolv.conf
-rw-r--r-- root wheel 10/23/2019 17:41    0 rmtab
-rw-r--r-- root wheel 10/23/2019 17:41 1735 rpc
-rw-r--r-- root wheel  7/25/2017 18:37 1735 rpc~previous
-rw-r--r-- root wheel 10/23/2019 18:42  891 rtadvd.conf
-rw-r--r-- root wheel  8/24/2017 21:54  891 rtadvd.conf~previous
```

現在屬於輸出的新屬性為：

- **UnixMode** 是 Unix 系統上所代表的檔案許可權
- **使用者** 是檔案擁有者
- **群組** 是群組擁有者
- **大小** 是 Unix 系統上表示的檔案或目錄大小

> [!NOTE]
> 這項功能已從實驗性移至 PowerShell 7.1 中的主流。

## 參數

### -Attributes

取得具有指定屬性的檔案和資料夾。 此參數支援所有屬性，可讓您指定複雜的屬性組合。

例如，若要取得已加密或壓縮的非系統檔案 (非目錄)，請輸入：

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

若要尋找具有常用屬性的檔案和資料夾，請使用 **attributes** 參數。 或參數 **目錄**、 **File**、 **Hidden**、 **ReadOnly** 和 **System**。

**Attributes** 參數支援下列屬性：

- **封存**
- **Compressed**
- **裝置**
- **目錄**
- **已加密**
- **Hidden**
- **IntegrityStream**
- **Normal**
- **NoScrubData**
- **NotContentIndexed**
- **離線**
- **ReadOnly**
- **ReparsePoint**
- **SparseFile**
- **系統**
- **暫存**

如需這些屬性的說明，請參閱 [FileAttributes 列舉](/dotnet/api/system.io.fileattributes)。

若要結合屬性，請使用下列運算子：

- `!` (不) 
- `+` (和) 
- `,` (或) 

請勿在運算子和其屬性之間使用空格。 逗號之後會接受空格。

針對通用屬性，請使用下列縮寫：

- `D` (Directory) 
- `H` (隱藏) 
- `R` (唯讀) 
- `S` (系統) 

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Depth

此參數是在 PowerShell 5.0 中新增的，可讓您控制遞迴的深度。 依預設，會 `Get-ChildItem` 顯示上層目錄的內容。 **Depth** 參數會決定包含在遞迴中的子目錄層級數目，並顯示內容。

例如， `Depth 2` 包含 **Path** 參數的目錄、第一個子目錄層級和第二層子目錄。 依預設，目錄名稱和檔案名會包含在輸出中。

> [!NOTE]
> 從 PowerShell 或 **cmd.exe** 的 Windows 電腦上，您可以使用 **tree.com** 命令來顯示目錄結構的圖形化視圖。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Directory

若要取得目錄清單，請使用 **directory** 參數或 **Attributes** 參數搭配 **directory** 屬性。 您可以使用 **遞迴** 參數搭配 **目錄**。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

以字串陣列指定此 Cmdlet 從作業中排除的屬性或屬性。
此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt` 或 `A*` 。 (接受萬用字元)。

`*` **Path** 參數中 () 的尾端星號是選擇性的。 例如，`-Path C:\Test\Logs` 或 `-Path C:\Test\Logs\*`。 如果包含尾端星號 (`*`) ，則命令會 recurses 至 **Path** 參數的子目錄。 如果沒有星號 (`*`) ，則會顯示 **Path** 參數的內容。 範例5和 Notes 區段中包含更多詳細資料。

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

### -File

若要取得檔案的清單，請使用 **File** 參數。 您可以使用 **遞迴** 參數搭配 **File**。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

指定要限定 **路徑** 參數的篩選準則。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援篩選器的已安裝 PowerShell 提供者。 篩選比其他參數更有效率。 此提供者會在取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。 篩選字串會傳遞至 .NET API 以列舉檔案。 API 僅支援 `*` 和 `?` 萬用字元。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -FollowSymlink

根據預設，此 `Get-ChildItem` Cmdlet 會顯示在遞迴期間找到之目錄的符號連結，但不會將其遞迴。 使用 **FollowSymlink** 參數來搜尋以這些符號連結為目標的目錄。 **FollowSymlink** 是動態參數，只有 **FileSystem** 提供者才支援。

此參數是在 PowerShell 6.0 中引進。

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

### -Force

允許 Cmdlet 取得使用者無法存取的專案，例如隱藏的檔案或系統檔案。 **Force** 參數不會覆寫安全性限制。 實作因提供者而異。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

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

### -Hidden

若只要取得隱藏的專案，請使用 **hidden** 參數或 **Attributes** 參數搭配 **隱藏** 的屬性。 依預設， `Get-ChildItem` 不會顯示隱藏的專案。 使用 **Force** 參數來取得隱藏的專案。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

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
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

只取得位置中專案的名稱。 輸出是可向下傳送管線給其他命令的字串物件。 允許使用萬用字元。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

指定一個或多個位置的路徑。 可使用萬用字元。 預設位置是 () 的目前的目錄 `.` 。

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ReadOnly

若只要取得唯讀專案，請使用 **readonly** 參數或 **Attributes** 參數 **readonly** 屬性。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Recurse

取得指定之位置中的項目及那些位置中的所有子項目。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -System

只取得系統檔案和目錄。 若只要取得系統檔案和資料夾，請使用 **system** 參數或 **Attributes** 參數 **系統** 屬性。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至 `Get-ChildItem` 。

## 輸出

### System.Object

傳回的物件類型 `Get-ChildItem` 取決於提供者磁片磁碟機路徑中的物件。

### System.String

如果您使用 **Name** 參數，則會 `Get-ChildItem` 以字串形式傳回物件名稱。

## 注意

- `Get-ChildItem` 可以使用任何內建的別名、、和來執行 `ls` `dir` `gci` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。
- `Get-ChildItem` 預設不會取得隱藏的專案。 若要取得隱藏的項目，請使用 **Force** 參數。
- 此 `Get-ChildItem` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。
  如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-Alias](../Microsoft.PowerShell.Utility/Get-Alias.md)

[Get-Item](Get-Item.md)

[Get-Location](Get-Location.md)

[Get-Process](Get-Process.md)

[Get-PSProvider](Get-PSProvider.md)

[Split-Path](Split-Path.md)

