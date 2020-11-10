---
description: FileSystem
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: FileSystem 提供者
ms.openlocfilehash: fad55a7fb7651dbb006e1765c513bf2546a73891
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390825"
---
# <a name="filesystem-provider"></a>FileSystem 提供者

## <a name="provider-name"></a>提供者名稱

FileSystem

## <a name="drives"></a>磁碟機

`C:`, `D:` ...

## <a name="capabilities"></a>功能

**篩選** 、 **ShouldProcess**

## <a name="short-description"></a>簡短描述

提供檔案與目錄的存取。

## <a name="detailed-description"></a>詳細描述

PowerShell **FileSystem** 提供者可讓您在 powershell 中取得、新增、變更、清除和刪除檔案和目錄。

**FileSystem** 磁片磁碟機是階層式命名空間，其中包含您電腦上的目錄和檔案。 **FileSystem** 磁片磁碟機可以是邏輯或 phsyical 磁片磁碟機、目錄或對應的網路共用。

名為的磁片磁碟機 `TEMP:` 將會對應至使用者的臨時目錄路徑。

>[!NOTE]
> TEMP：磁片磁碟機中的內容不會被 PowerShell 自動移除，而是由使用者或作業系統進行管理。

**FileSystem** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>此提供者公開的類型

檔案是 [FileInfo](/dotnet/api/system.io.fileinfo) 類別的實例。  目錄是 [DirectoryInfo](/dotnet/api/system.io.directoryinfo) 類別的實例。

## <a name="navigating-the-filesystem-drives"></a>流覽檔案系統磁片磁碟機

**FileSystem** 提供者會將電腦上的任何邏輯磁碟機對應為 PowerShell 磁片磁碟機，以公開其資料存放區。 若要使用 **檔案系統** 磁片磁碟機，您可以將位置變更為磁片磁碟機，uing 磁片磁碟機名稱後面接著冒號 (`:`) 。

```powershell
Set-Location C:
```

您也可以使用任何其他 PowerShell 磁片磁碟機的 **FileSystem** 提供者。 若要從另一個位置參考檔案或目錄，請 `C:` 在路徑中使用磁片磁碟機名稱 (， `D:` ) 。

> [!NOTE]
> PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。 和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。 和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。

## <a name="getting-files-and-directories"></a>取得檔案和目錄

Cmdlet 會傳回 `Get-ChildItem` 目前位置中的所有檔案和目錄。 您可以指定不同的路徑來搜尋和使用內建參數，以篩選和控制遞迴深度。

```powershell
Get-ChildItem
```

若要閱讀更多 Cmdlet 用法的詳細資訊，請參閱 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)。

## <a name="copying-files-and-directories"></a>複製檔案和目錄

`Copy-Item`Cmdlet 會將檔案和目錄複寫到您指定的位置。
參數可用於篩選和遞迴，類似于 `Get-ChildItem` 。

下列命令會將路徑 "C：\temp" 的所有檔案和目錄複寫 \" 到 "C:\Windows\Temp" 資料夾。

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

`Copy-Item` 覆寫目的地目錄中的檔案，而不提示確認。

此命令會將檔案 `a.txt` 從 `C:\a` 目錄複寫到 `C:\a\bb` 目錄。

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

將目錄中的所有目錄和檔案複製 `C:\a` 到 `C:\c` 目錄。 如果要複製的任一個目錄已經存在於目的地目錄中，除非您指定 Force 參數，否則此命令將會失敗。

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

如需詳細資訊，請參閱 [複製專案](xref:Microsoft.PowerShell.Management.Copy-Item)。

## <a name="moving-files-and-directories"></a>移動檔案和目錄

此命令會將 `c.txt` 目錄中的檔案移 `C:\a` 至 `C:\a\aa` 目錄：

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

此命令將不會自動覆寫具有相同名稱的現有檔案。 若要強制此 Cmdlet 覆寫現有的檔案，請指定 Force 參數。

當目錄為目前位置時，您無法移動該目錄。 當您使用 `Move-Item` 來移動目前位置的目錄時，您會看到此錯誤。

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a>管理檔案內容

### <a name="get-the-content-of-a-file"></a>取得檔案的內容

此命令會取得 "Test.txt" 檔案的內容，並在主控台中顯示它們。

```powershell
Get-Content -Path Test.txt
```

您可以使用管線將檔案的內容傳送至其他 Cmdlet。 例如，下列命令會讀取檔案的內容 `Test.txt` ，然後以輸入形式提供給 [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) Cmdlet：

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

您也可以將檔案的提供者路徑加上貨幣符號 () ，以取出檔案的內容 `$` 。 因為變數命名限制，路徑必須以大括弧括住。 如需詳細資訊，請參閱 [about_Variables](about_Variables.md)。

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a>將內容新增至檔案

此命令會將 "test content" 字串附加至檔案 `Test.txt` ：

```powershell
Add-Content -Path test.txt -Value "test content"
```

不會刪除檔案中的現有內容 `Test.txt` 。

### <a name="replace-the-content-of-a-file"></a>取代檔案的內容

此命令會以「測試內容」字串取代檔案的內容 `Test.txt` ：

```powershell
Set-Content -Path test.txt -Value "test content"
```

它會覆寫的內容 `Test.txt` 。 您可以使用 [新專案](xref:Microsoft.PowerShell.Management.New-Item)Cmdlet 的 **Value** 參數，在建立內容時將內容新增至檔案。

### <a name="loop-through-the-contents-of-a-file"></a>逐一查看檔案的內容

根據預設，此 `Get-Content` Cmdlet 會使用行結尾字元做為分隔符號，因此它會以字串集合的形式取得檔案，其中每一行都是檔案中的一個字串。

您可以使用 `-Delimiter` 參數來指定替代分隔符號。 如果您將它設定為代表某區段結尾或下一區段開頭的字元，就可以將檔案分割為邏輯部分。

第一個命令會取得檔案 `Employees.txt` 並將它分割成區段，而每個區段的結尾都是「員工記錄結尾」，並且會將它儲存在 `$e` 變數中。

第二個命令會使用陣列標記法，取得集合中的第一個專案 `$e` 。 因為 PowerShell 陣列是以零為基礎，所以它會使用索引0。

如需有關 Cmdlet 的詳細資訊 `Get-Content` ，請參閱 [取得內容](xref:Microsoft.PowerShell.Management.Get-Content)的說明主題。

如需陣列的詳細資訊，請參閱 [about_Arrays](../About/about_Arrays.md)。

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a>管理安全描述項

### <a name="view-the-acl-for-a-file"></a>查看檔案的 ACL

此命令會傳回 [AccessControl. system.security.accesscontrol.filesecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 物件：

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

如需此物件的詳細資訊，請將命令輸送至 [取得成員](xref:Microsoft.PowerShell.Utility.Get-Member) Cmdlet。 或者，請參閱 [System.security.accesscontrol.filesecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 類別。

### <a name="modify-the-acl-for-a-file"></a>修改檔案的 ACL

### <a name="create-and-set-an-acl-for-a-file"></a>建立並設定檔案的 ACL

## <a name="creating-files-and-directories"></a>建立檔案和目錄

### <a name="create-a-directory"></a>建立目錄

此命令會 `logfiles` 在磁片磁碟機上建立目錄 `C` ：

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

PowerShell 也包含 `mkdir` (別名 `md`) 的函式，該函 [式使用新專案](xref:Microsoft.PowerShell.Management.New-Item) Cmdlet 來建立新目錄。

### <a name="create-a-file"></a>建立檔案

此命令會 `log2.txt` 在目錄中建立檔案 `C:\logfiles` ，然後將 "test log" 字串新增至檔案：

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a>建立具有內容的檔案

在目錄中建立名為的檔案 `log2.txt` `C:\logfiles` ，並將字串 "test log" 新增至檔案。

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a>重新命名檔案和目錄

### <a name="rename-a-file"></a>重新命名檔案

此命令會將目錄中的檔案重新命名 `a.txt` `C:\a` 為 `b.txt` ：

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a>重新命名目錄

此命令會將 `C:\a\cc` 目錄重新命名為 `C:\a\dd` ：

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a>刪除檔案和目錄

### <a name="delete-a-file"></a>刪除檔案

此命令會刪除 `Test.txt` 目前目錄中的檔案：

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a>使用萬用字元刪除檔案

此命令會刪除目前目錄中副檔名為的所有檔案 `.xml` ：

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a>藉由叫用相關聯的檔案來啟動程式

### <a name="invoke-a-file"></a>叫用檔案

第一個命令會使用 [get-help](xref:Microsoft.PowerShell.Management.Get-Service) Cmdlet 來取得本機服務的相關資訊。

它會將資訊傳送至 [匯出 Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) Cmdlet，然後將該資訊儲存在檔案中 `Services.csv` 。

第二個命令會使用 [Invoke 專案](xref:Microsoft.PowerShell.Management.Invoke-Item) ， `services.csv` 在與擴充功能相關聯的程式中開啟檔案 `.csv` ：

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a>取得具有指定屬性的檔案和資料夾

### <a name="get-system-files"></a>取得系統檔案

此命令會取得目前目錄及其子目錄中的系統檔案。

它會使用 `-File` 參數，只取得 (非目錄) 的檔案，以及 `-System` 只取得具有 "system" 屬性之專案的參數。

它會使用 `-Recurse` 參數來取得目前目錄和所有子目錄中的專案。

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a>取得隱藏的檔案

此命令會取得目前目錄中的所有檔案 (包括隱藏的檔案)。

它會使用具有兩個值的 **屬性** 參數，這些值會 `!Directory+Hidden` 取得隱藏的檔案，以及 `!Directory` 取得所有其他檔案。

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

`dir -att !d,!d+h` 相當於這個命令。

### <a name="get-compressed-and-encrypted-files"></a>取得壓縮和加密的檔案

此命令會取得目前目錄中已壓縮或加密的檔案。

它會使用 `-Attributes` 具有兩個值的參數： `Compressed` 和 `Encrypted` 。 這些值會以逗號分隔， `,` 表示 "OR" 運算子。

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a>動態參數

動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a>Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\>

指定檔案的編碼方式。 預設值為 ASCII。

- **Ascii** ：使用 ascii (7 位) 字元集的編碼方式。
- **BigEndianUnicode** ：使用位元組由大到小的位元組順序，以 Utf-16 格式編碼。
- **字串** ：使用字串的編碼類型。
- **Unicode** ：使用位元組由大到小的位元組順序，以 Utf-16 格式編碼。
- **UTF7** ：以 Utf-7 格式編碼。
- **UTF8** ：以 Utf-8 格式編碼。
- **UTF8BOM** ：使用 (BOM) 的位元組順序標記來編碼 utf-8 格式
- **UF8NOBOM** ：以不含位元組順序標記的 Utf-8 格式來編碼 (BOM) 
- **UTF32** ：以 UTF-32 格式編碼。
- **預設** ：在預設安裝的字碼頁中進行編碼。
- **OEM** ：對 MS-DOS 和主控台程式使用預設編碼。
- **未知** ：編碼類型未知或無效。 資料可視為二進位檔。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a>Delimiter \<System.String\>

指定分隔符號，讓 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 在讀取時可用來將檔案分割成物件。

預設值為 `\n` ，行尾字元。

讀取文字檔時， [Get 內容](xref:Microsoft.PowerShell.Management.Get-Content) 會傳回字串物件的集合，其中每個物件的結尾都是分隔符號。

輸入不存在於檔案中的分隔符號， [Get 內容](xref:Microsoft.PowerShell.Management.Get-Content) 會以單一、未分隔的物件形式傳回整個檔案。

您可以使用這個參數，藉由指定檔案分隔符號 (例如 "End of Example") 做為分隔符號，將大型檔案分割成較小的檔案。 分隔符號會保留 (不會被捨棄)，並成為每個檔案區段中的最後一個項目。

> [!NOTE]
> 目前，當參數的值 `-Delimiter` 為空字串時， [Get 內容](xref:Microsoft.PowerShell.Management.Get-Content) 不會傳回任何內容。
> 這是已知的問題。 若要強制 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 以單一、未分隔的物件形式傳回整個檔案，請輸入檔案中不存在的值。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a>Wait \<System.Management.Automation.SwitchParameter\>

等候要附加至檔案的內容。 如果內容已附加，就會傳回附加的內容。 如果內容已變更，則會傳回整個檔案。

等候時，[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 每秒會檢查檔案一次，直到您中斷它為止，例如，按下 CTRL+C。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a>Attributes \<FlagsExpression\>

取得具有指定屬性的檔案和資料夾。 此參數支援所有屬性，可讓您指定複雜的屬性組合。

`-Attributes`參數是在 Windows PowerShell 3.0 中引進。

`-Attributes`參數支援下列屬性：

- **封存**
- **Compressed**
- **裝置**
- **目錄**
- **已加密**
- **Hidden**
- **Normal**
- **NotContentIndexed**
- **離線**
- **ReadOnly**
- **ReparsePoint**
- **SparseFile**
- **系統**
- **暫存**

如需這些屬性的說明，請參閱 [FileAttributes](/dotnet/api/system.io.fileattributes) 列舉。

使用下列運算子來結合屬性。

- `!` -NOT
- `+` -和
- `,` -或

運算子和其屬性之間不允許有任何空格。 不過，逗號之前可以有空格。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a>Directory \<System.Management.Automation.SwitchParameter\>

取得目錄 (資料夾)。

`-Directory`參數是在 Windows PowerShell 3.0 中引進。

若只要取得目錄，請使用 `-Directory` 參數並省略 `-File` 參數。 若要排除目錄，請使用 `-File` 參數並省略 `-Directory` 參數，或使用 `-Attributes` 參數。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a>File \<System.Management.Automation.SwitchParameter\>

取得檔案。

`-File`參數是在 Windows PowerShell 3.0 中引進。

若只要取得檔案，請使用 `-File` 參數並省略 `-Directory` 參數。 若要排除檔案，請使用 `-Directory` 參數並省略 `-File` 參數，或使用 `-Attributes` 參數。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a>Hidden \<System.Management.Automation.SwitchParameter\>

只取得隱藏的檔案和目錄 (資料夾)。 根據預設， [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 只會取得非隱藏的專案。

`-Hidden`參數是在 Windows PowerShell 3.0 中引進。

若只要取得隱藏的專案，請使用 `-Hidden` 參數、其 `h` 或 `ah` 別名，或參數的 **隱藏** 值 `-Attributes` 。 若要排除隱藏的專案，請省略 `-Hidden` 參數或使用 `-Attributes` 參數。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a>ReadOnly \<System.Management.Automation.SwitchParameter\>

只取得唯讀的檔案和目錄 (資料夾)。

`-ReadOnly`參數是在 Windows PowerShell 3.0 中引進。

若只要取得唯讀專案，請使用參數 `-ReadOnly` 、其 `ar` 別名或參數的 **ReadOnly** 值 `-Attributes` 。 若要排除唯讀專案，請使用 `-Attributes` 參數。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a>System \<System.Management.Automation.SwitchParameter\>

只取得系統檔案和目錄 (資料夾)。

`-System`參數是在 Windows PowerShell 3.0 中引進。

若只要取得系統檔案和資料夾，請使用參數 `-System` 、其 `as` 別名或參數的 **系統** 值 `-Attributes` 。 若要排除系統檔案和資料夾，請使用 `-Attributes` 參數。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a>NewerThan \<System.DateTime\>

`$True`當檔案的 `LastWriteTime` 值大於指定的日期時傳回。 否則，它會傳回 `$False`。

輸入 [datetime](/dotnet/api/system.datetime) 物件（例如， [取得日期](xref:Microsoft.PowerShell.Utility.Get-Date) Cmdlet 所傳回的物件），或輸入可轉換為 [DateTime](/dotnet/api/system.datetime) 物件的字串，例如 `"August 10, 2011 2:00 PM"` 。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a>OlderThan \<System.DateTime\>

`$True`當檔案的 `LastWriteTime` 值小於指定的日期時傳回。 否則，它會傳回 `$False`。

輸入 [datetime](/dotnet/api/system.datetime) 物件（例如， [取得日期](xref:Microsoft.PowerShell.Utility.Get-Date) Cmdlet 所傳回的物件），或輸入可轉換為 [DateTime](/dotnet/api/system.datetime) 物件的字串，例如 `"August 10, 2011 2:00 PM"` 。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a>Stream \<System.String\>

管理替代資料流。 輸入資料流名稱。 只有在檔案系統磁片磁碟機中的 [Get 專案](xref:Microsoft.PowerShell.Management.Get-Item) 和 [移除專案](xref:Microsoft.PowerShell.Management.Remove-Item) 命令中，才允許使用萬用字元。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Clear-Content](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a>Raw \<SwitchParameter\>

忽略新行字元。 以單一項目形式傳回內容。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a>ItemType \<String\>

此參數可讓您指定要建立的專案 tye `New-Item`

此參數的可用值取決於您目前使用的提供者。

在 `FileSystem` 磁片磁碟機中，允許下列值：

- 檔案
- 目錄
- >symboliclink
- 接合
- 硬

### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>使用管線

提供者 Cmdlet 接受管線輸入。 您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。
若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。

## <a name="getting-help"></a>取得說明

從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。

若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 的參數來指定檔案系統磁片磁碟機。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a>另請參閱

[about_Providers](../About/about_Providers.md)
