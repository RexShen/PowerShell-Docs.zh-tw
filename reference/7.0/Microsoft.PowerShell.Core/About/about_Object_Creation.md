---
description: 說明如何在 PowerShell 中建立物件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 885218848081aae364e662c3060500af3f5759ab
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206776"
---
# <a name="about-object-creation"></a>關於建立物件

## <a name="short-description"></a>簡短描述

說明如何在 PowerShell 中建立物件。

## <a name="long-description"></a>完整描述

您可以在 PowerShell 中建立物件，並使用您在命令和腳本中建立的物件。

建立物件的方式有很多種，這份清單並不是最終的：

- [新物件](xref:Microsoft.PowerShell.Utility.New-Object)：建立 .NET Framework 物件或 COM 物件的實例。
- 匯[入-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv) /
  [Convertfrom-string-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv)：從定義為逗點分隔值的專案建立自訂物件 ( **PSCustomObject** ) 。
- [Convertfrom-string-json](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json)：建立 JAVASCRIPT 物件標記法 (Json) 中定義的自訂物件。
- [Convertfrom-string-至 convertfrom-stringdata](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)：建立定義為機碼值組的自訂物件。
- [Add 類型](xref:Microsoft.PowerShell.Utility.Add-Type)：可讓您在 PowerShell 會話中定義可供具現化的類別 `New-Object` 。
- [New-Module](xref:Microsoft.PowerShell.Core.New-Module)： **AsCustomObject** 參數會建立您使用腳本區塊定義的自訂物件。
- [新增成員](xref:Microsoft.PowerShell.Utility.Add-Member)：將屬性加入至現有的物件。 您可以使用 `Add-Member` 從簡單的類型（例如）建立自訂物件 `[System.Int32]` 。
- [Select-object](xref:Microsoft.PowerShell.Utility.Select-Object)：選取物件上的屬性。 您可以使用在已具現 `Select-Object` 化的物件上建立自訂和計算屬性。

本文涵蓋下列其他方法：

- 藉由使用靜態方法呼叫類型的函式 `new()`
- 藉由 typecasting 屬性名稱和屬性值的雜湊表

## <a name="static-new-method"></a>靜態 new ( # A1 方法

所有 .NET 類型都有一種 `new()` 方法，可讓您更輕鬆地建立實例。 您也可以查看指定類型的所有可用的函式。

若要查看類型的函式，請在 `new` 類型名稱之後指定方法名稱，然後按下 `<ENTER>` 。

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

現在，您可以藉由指定適當的函式來建立 **系統 Uri** 。

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

您可以使用下列範例，判斷目前載入哪些 .NET 類型以具現化。

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

使用方法建立的物件 `new()` 可能會與 PowerShell Cmdlet 所建立之相同類型的物件具有相同的屬性。 PowerShell Cmdlet、提供者和擴充類型系統可以將額外的屬性新增至實例。

例如，PowerShell 中的 FileSystem 提供者會將六個 **NoteProperty** 值新增至所傳回的 **DirectoryInfo** 物件 `Get-Item` 。

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

當您直接建立 **DirectoryInfo** 物件時，它不會有這六個 **NoteProperty** 值。

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

如需擴充類型系統的詳細資訊，請參閱 [about_Types.ps1xml](about_Types.ps1xml.md)。

這項功能已新增至 PowerShell 5。0

## <a name="create-objects-from-hash-tables"></a>從雜湊表建立物件

您可以從屬性和屬性值的雜湊表建立物件。

語法如下：

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

這個方法僅適用于具有無參數的函式的類別。 物件屬性必須是公用而且可設定。

這項功能已新增至 PowerShell 3.0 版

## <a name="create-custom-objects-from-hash-tables"></a>從雜湊表建立自訂物件

自訂物件非常有用，而且可以使用雜湊表方法輕鬆建立。 **PSCustomObject** 類別是特別針對此用途所設計。

自訂物件是從函數或腳本傳回自訂輸出的絕佳方法。 這比傳回無法重新格式化或輸送至其他命令的格式化輸出更有用。

中的命令會 `Test-Object function` 設定一些變數值，然後使用這些值來建立自訂物件。 您可以在 Cmdlet 說明主題的範例一節中看到此物件正在使用中 `Update-Help` 。

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

此函式的輸出預設是一些格式化為表格的自訂物件。

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

使用者可以管理自訂物件的屬性，就如同使用標準的物件。

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a>從雜湊表建立非自訂物件

您也可以使用雜湊表來建立非自訂類別的物件。 當您建立非自訂類別的物件時，需要命名空間限定的型別名稱，不過您可能會省略任何初始的 **系統** 命名空間元件。

例如，下列命令會建立工作階段選項物件。

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

雜湊表功能的需求，特別是無參數的函式需求，會消除許多現有的類別。 不過，大部分的 PowerShell _選項_ 類別都是設計來使用這項功能，以及其他非常實用的類別，例如 **ProcessStartInfo** 類別。

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

設定參數值時，您也可以使用雜湊表功能。 例如，的 **SessionOption** 參數值 `New-PSSession` 。
Cmdlet 可以是雜湊表。

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a>泛型物件

您也可以在 PowerShell 中建立泛型物件。 泛型是指一些類別、結構、介面與方法，其具有所儲存或使用之一或多個類型的預留位置 (類型參數)。

下列範例會建立 **Dictionary** 物件。

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

如需泛型的詳細資訊，請參閱 [.net 中的泛型](/dotnet/standard/generics)。

## <a name="see-also"></a>另請參閱

[about_Objects](about_Objects.md)

[about_Methods](about_Methods.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[about_Types.ps1xml](about_Types.ps1xml.md)
