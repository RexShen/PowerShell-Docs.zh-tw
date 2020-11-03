---
description: 描述如何在 PowerShell 中使用物件屬性。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: d4d3cd93e6b177e80d85315f125c647219fc4a45
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208304"
---
# <a name="about-properties"></a>關於屬性

## <a name="short-description"></a>簡短描述
描述如何在 PowerShell 中使用物件屬性。

## <a name="long-description"></a>完整描述

PowerShell 會使用稱為物件的結構化集合來代表資料存放區中的專案或電腦的狀態。 一般而言，您會使用屬於 Microsoft .NET Framework 的物件，但您也可以在 PowerShell 中建立自訂物件。

項目和其物件之間的關聯非常緊密。 當您變更物件時，通常會變更其所代表的項目。 例如，當您在 PowerShell 中取得檔案時，不會取得實際的檔案。 而是會取得代表該檔案的 FileInfo 物件。 當您變更 FileInfo 物件時，檔案也會變更。

大部分的物件都具有屬性。 屬性是與物件相關聯的資料。 不同類型的物件有不同的屬性。 例如，代表檔案的 FileInfo 物件具有 **IsReadOnly** 屬性，如果檔案是唯讀屬性，則會包含 $True，如果沒有，則為 $False。
代表檔案系統目錄的 DirectoryInfo 物件具有一個父屬性，其中包含父目錄的路徑。

### <a name="object-properties"></a>物件屬性

若要取得物件的屬性，請使用 `Get-Member` Cmdlet。 例如，若要取得 **FileInfo** 物件的屬性，請使用 `Get-ChildItem` Cmdlet 取得代表檔案的 FileInfo 物件。 然後，使用管線運算子 ( # A0) 將 **FileInfo** 物件傳送至 `Get-Member` 。 下列命令會取得 PowerShell.exe 的檔案，並將它傳送至 `Get-Member` 。
\$Pshome 自動變數包含 PowerShell 安裝目錄的路徑。

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

命令的輸出會列出 **FileInfo** 物件的成員。
成員包含屬性和方法。 當您在 PowerShell 中工作時，您可以存取物件的所有成員。

若只要取得物件的屬性，而不只取得方法的屬性，請使用 Cmdlet 的 MemberType 參數搭配 `Get-Member` "property" 的值，如下列範例所示。

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

找到屬性之後，您就可以在 PowerShell 命令中使用它們。

## <a name="property-values"></a>屬性值

雖然特定類型的每個物件具有相同的屬性，這些屬性的值會描述特定的物件。 例如，每個 FileInfo 物件都具有 CreationTime 屬性，但每個檔案的這個屬性值不同。

取得物件屬性最長見的方式，是使用點方法。 輸入物件的參考 (例如，包含物件的變數) 或輸入取得物件的命令。 接著輸入點 (.)，後面加上屬性名稱。

例如，下列命令顯示 PowerShell.exe 檔案的 CreationTime 屬性的值。 此 `Get-ChildItem` 命令會傳回代表 PowerShell.exe 檔案的 FileInfo 物件。 命令以括號括住，可確保先執行命令再存取任何屬性。 `Get-ChildItem`命令後面會加上點和 CreationTime 屬性的名稱，如下所示：

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

您可以也儲存變數中的物件，然後使用點方法取得其屬性，如下列範例所示︰

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

您也可以使用 `Select-Object` 和 `Format-List` Cmdlet 來顯示物件的屬性值。 `Select-Object` 而且 `Format-List` 每一個都有一個 **Property** 參數。 您可以使用 **Property** 參數來指定一個或多個屬性及其值。 或者，您可以使用萬用字元 (\*) 代表所有屬性。

例如，下列命令顯示 PowerShell.exe 檔案的所有屬性的值。

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a>靜態屬性

您可以在 PowerShell 中使用 .NET 類別的靜態屬性。 靜態屬性是類別的屬性，有別於標準屬性，它們是物件的屬性。

若要取得類別的靜態屬性，請使用 Get-Member Cmdlet 的靜態參數。

例如，下列命令會取得類別的靜態屬性 `System.DateTime` 。

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

若要取得靜態屬性的值，請使用下列語法。

```
[<ClassName>]::<Property>
```

例如，下列命令會取得類別 UtcNow 靜態屬性的值 `System.DateTime` 。

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a>純量物件和集合的屬性

特定類型的單一 (「純量」) 物件屬性通常不同於同類型物件集合的屬性。
例如，每個服務都有 **displayname** 屬性，但服務的集合沒有 **displayname** 屬性。

下列命令會取得 ' Audiosrv ' 服務的 **DisplayName** 屬性值。

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

從 PowerShell 3.0 開始，PowerShell 會嘗試避免因為純量物件和集合的不同屬性而產生的腳本錯誤。 相同的命令會傳回傳回之每個服務的 **DisplayName** 屬性值 `Get-Service` 。

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

當您提交集合，但要求只存在單一 ( 「純量」 ) 物件上的屬性時，PowerShell 會針對集合中的每個物件傳回該屬性的值。

所有集合都有一個 **Count** 屬性，會傳回集合中的物件數目。

```powershell
(Get-Service).Count
```

```output
176
```

從 PowerShell 3.0 開始，如果您要求零個物件或一個物件的 Count 或 Length 屬性，PowerShell 就會傳回正確的值。

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

如果屬性存在於個別的物件和集合上，則只會傳回集合的屬性。

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

這項功能也適用於純量物件和集合的方法。 如需詳細資訊，請參閱 [about_Methods](about_methods.md)。

## <a name="see-also"></a>另請參閱

[about_Methods](about_Methods.md)

[about_Objects](about_Objects.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

