---
description: 說明如何在 PowerShell 中建立物件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 20df0b3f5e95bc5238ecbc56738c2e800a1c360a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207031"
---
# <a name="about-object-creation"></a><span data-ttu-id="bd0fb-104">關於建立物件</span><span class="sxs-lookup"><span data-stu-id="bd0fb-104">About Object Creation</span></span>

## <a name="short-description"></a><span data-ttu-id="bd0fb-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="bd0fb-105">Short description</span></span>

<span data-ttu-id="bd0fb-106">說明如何在 PowerShell 中建立物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-106">Explains how to create objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="bd0fb-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="bd0fb-107">Long description</span></span>

<span data-ttu-id="bd0fb-108">您可以在 PowerShell 中建立物件，並使用您在命令和腳本中建立的物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-108">You can create objects in PowerShell and use the objects that you create in commands and scripts.</span></span>

<span data-ttu-id="bd0fb-109">建立物件的方式有很多種，這份清單並不是最終的：</span><span class="sxs-lookup"><span data-stu-id="bd0fb-109">There are many ways to create objects, this list is not definitive:</span></span>

- <span data-ttu-id="bd0fb-110">[新物件](xref:Microsoft.PowerShell.Utility.New-Object)：建立 .NET Framework 物件或 COM 物件的實例。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-110">[New-Object](xref:Microsoft.PowerShell.Utility.New-Object): Creates an instance of a .NET Framework object or COM object.</span></span>
- <span data-ttu-id="bd0fb-111">匯[入-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv) /
  [Convertfrom-string-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv)：從定義為逗點分隔值的專案建立自訂物件 ( **PSCustomObject** ) 。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-111">[Import-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv)/
  [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): Creates custom objects ( **PSCustomObject** ) from the items defined as comma separated values.</span></span>
- <span data-ttu-id="bd0fb-112">[Convertfrom-string-json](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json)：建立 JAVASCRIPT 物件標記法 (Json) 中定義的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-112">[ConvertFrom-Json](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): Creates custom objects defined in JavaScript Object Notation (JSON).</span></span>
- <span data-ttu-id="bd0fb-113">[Convertfrom-string-至 convertfrom-stringdata](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)：建立定義為機碼值組的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-113">[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): Creates custom objects defined as key value pairs.</span></span>
- <span data-ttu-id="bd0fb-114">[Add 類型](xref:Microsoft.PowerShell.Utility.Add-Type)：可讓您在 PowerShell 會話中定義可供具現化的類別 `New-Object` 。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-114">[Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type): Allows you to define a class in your PowerShell session that you can instantiate with `New-Object`.</span></span>
- <span data-ttu-id="bd0fb-115">[New-Module](xref:Microsoft.PowerShell.Core.New-Module)： **AsCustomObject** 參數會建立您使用腳本區塊定義的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-115">[New-Module](xref:Microsoft.PowerShell.Core.New-Module): The **AsCustomObject** parameter creates a custom object you define using script block.</span></span>
- <span data-ttu-id="bd0fb-116">[新增成員](xref:Microsoft.PowerShell.Utility.Add-Member)：將屬性加入至現有的物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-116">[Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member): Adds properties to existing objects.</span></span> <span data-ttu-id="bd0fb-117">您可以使用 `Add-Member` 從簡單的類型（例如）建立自訂物件 `[System.Int32]` 。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-117">You can use `Add-Member` to create a custom object out of a simple type, like `[System.Int32]`.</span></span>
- <span data-ttu-id="bd0fb-118">[Select-object](xref:Microsoft.PowerShell.Utility.Select-Object)：選取物件上的屬性。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-118">[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object): Selects properties on an object.</span></span> <span data-ttu-id="bd0fb-119">您可以使用在已具現 `Select-Object` 化的物件上建立自訂和計算屬性。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-119">You can use `Select-Object` to create custom and calculated properties on an already instantiated object.</span></span>

<span data-ttu-id="bd0fb-120">本文涵蓋下列其他方法：</span><span class="sxs-lookup"><span data-stu-id="bd0fb-120">The following additional methods are covered in this article:</span></span>

- <span data-ttu-id="bd0fb-121">藉由使用靜態方法呼叫類型的函式 `new()`</span><span class="sxs-lookup"><span data-stu-id="bd0fb-121">By calling a type's constructor using a static `new()` method</span></span>
- <span data-ttu-id="bd0fb-122">藉由 typecasting 屬性名稱和屬性值的雜湊表</span><span class="sxs-lookup"><span data-stu-id="bd0fb-122">By typecasting hash tables of property names and property values</span></span>

## <a name="static-new-method"></a><span data-ttu-id="bd0fb-123">靜態 new ( # A1 方法</span><span class="sxs-lookup"><span data-stu-id="bd0fb-123">Static new() method</span></span>

<span data-ttu-id="bd0fb-124">所有 .NET 類型都有一種 `new()` 方法，可讓您更輕鬆地建立實例。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-124">All .NET types have a `new()` method that allows you to construct instances more easily.</span></span> <span data-ttu-id="bd0fb-125">您也可以查看指定類型的所有可用的函式。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-125">You can also see all the available constructors for a given type.</span></span>

<span data-ttu-id="bd0fb-126">若要查看類型的函式，請在 `new` 類型名稱之後指定方法名稱，然後按下 `<ENTER>` 。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-126">To see the constructors for a type, specify the `new` method name after the type name and press `<ENTER>`.</span></span>

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

<span data-ttu-id="bd0fb-127">現在，您可以藉由指定適當的函式來建立 **系統 Uri** 。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-127">Now, you can create a **System.Uri** by specifying the appropriate constructor.</span></span>

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

<span data-ttu-id="bd0fb-128">您可以使用下列範例，判斷目前載入哪些 .NET 類型以具現化。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-128">You can use the following sample to determine what .NET types are currently loaded for you to instantiate.</span></span>

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

<span data-ttu-id="bd0fb-129">使用方法建立的物件 `new()` 可能會與 PowerShell Cmdlet 所建立之相同類型的物件具有相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-129">Objects created using the `new()` method may not have the same properties as objects of the same type that are created by PowerShell cmdlets.</span></span> <span data-ttu-id="bd0fb-130">PowerShell Cmdlet、提供者和擴充類型系統可以將額外的屬性新增至實例。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-130">PowerShell cmdlets, providers, and Extended Type System can add extra properties to the instance.</span></span>

<span data-ttu-id="bd0fb-131">例如，PowerShell 中的 FileSystem 提供者會將六個 **NoteProperty** 值新增至所傳回的 **DirectoryInfo** 物件 `Get-Item` 。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-131">For example, the FileSystem provider in PowerShell adds six **NoteProperty** values to the **DirectoryInfo** object returned by `Get-Item`.</span></span>

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

<span data-ttu-id="bd0fb-132">當您直接建立 **DirectoryInfo** 物件時，它不會有這六個 **NoteProperty** 值。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-132">When you create a **DirectoryInfo** object directly, it does not have those six **NoteProperty** values.</span></span>

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

<span data-ttu-id="bd0fb-133">如需擴充類型系統的詳細資訊，請參閱 [about_Types.ps1xml](about_Types.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-133">For more information about the Extended Type System, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

<span data-ttu-id="bd0fb-134">這項功能已新增至 PowerShell 5。0</span><span class="sxs-lookup"><span data-stu-id="bd0fb-134">This feature was added in PowerShell 5.0</span></span>

## <a name="create-objects-from-hash-tables"></a><span data-ttu-id="bd0fb-135">從雜湊表建立物件</span><span class="sxs-lookup"><span data-stu-id="bd0fb-135">Create objects from hash tables</span></span>

<span data-ttu-id="bd0fb-136">您可以從屬性和屬性值的雜湊表建立物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-136">You can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="bd0fb-137">語法如下：</span><span class="sxs-lookup"><span data-stu-id="bd0fb-137">The syntax is as follows:</span></span>

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="bd0fb-138">這個方法僅適用于具有無參數的函式的類別。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-138">This method works only for classes that have a parameterless constructor.</span></span> <span data-ttu-id="bd0fb-139">物件屬性必須是公用而且可設定。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-139">The object properties must be public and settable.</span></span>

<span data-ttu-id="bd0fb-140">這項功能已新增至 PowerShell 3.0 版</span><span class="sxs-lookup"><span data-stu-id="bd0fb-140">This feature was added in PowerShell version 3.0</span></span>

## <a name="create-custom-objects-from-hash-tables"></a><span data-ttu-id="bd0fb-141">從雜湊表建立自訂物件</span><span class="sxs-lookup"><span data-stu-id="bd0fb-141">Create custom objects from hash tables</span></span>

<span data-ttu-id="bd0fb-142">自訂物件非常有用，而且可以使用雜湊表方法輕鬆建立。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-142">Custom objects are very useful and are easy to create using the hash table method.</span></span> <span data-ttu-id="bd0fb-143">**PSCustomObject** 類別是特別針對此用途所設計。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-143">The **PSCustomObject** class is designed specifically for this purpose.</span></span>

<span data-ttu-id="bd0fb-144">自訂物件是從函數或腳本傳回自訂輸出的絕佳方法。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-144">Custom objects are an excellent way to return customized output from a function or script.</span></span> <span data-ttu-id="bd0fb-145">這比傳回無法重新格式化或輸送至其他命令的格式化輸出更有用。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-145">This is more useful than returning formatted output that cannot be reformatted or piped to other commands.</span></span>

<span data-ttu-id="bd0fb-146">中的命令會 `Test-Object function` 設定一些變數值，然後使用這些值來建立自訂物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-146">The commands in the `Test-Object function` set some variable values and then use those values to create a custom object.</span></span> <span data-ttu-id="bd0fb-147">您可以在 Cmdlet 說明主題的範例一節中看到此物件正在使用中 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-147">You can see this object in use in the example section of the `Update-Help` cmdlet help topic.</span></span>

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

<span data-ttu-id="bd0fb-148">此函式的輸出預設是一些格式化為表格的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-148">The output of this function is a collection of custom objects formatted as a table by default.</span></span>

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

<span data-ttu-id="bd0fb-149">使用者可以管理自訂物件的屬性，就如同使用標準的物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-149">Users can manage the properties of the custom objects just as they do with standard objects.</span></span>

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a><span data-ttu-id="bd0fb-150">從雜湊表建立非自訂物件</span><span class="sxs-lookup"><span data-stu-id="bd0fb-150">Create non-custom objects from hash tables</span></span>

<span data-ttu-id="bd0fb-151">您也可以使用雜湊表來建立非自訂類別的物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-151">You can also use hash tables to create objects for non-custom classes.</span></span> <span data-ttu-id="bd0fb-152">當您建立非自訂類別的物件時，需要命名空間限定的型別名稱，不過您可能會省略任何初始的 **系統** 命名空間元件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-152">When you create an object for a non-custom class, the namespace-qualified type name is required, although you may omit any initial **System** namespace component.</span></span>

<span data-ttu-id="bd0fb-153">例如，下列命令會建立工作階段選項物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-153">For example, the following command creates a session option object.</span></span>

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

<span data-ttu-id="bd0fb-154">雜湊表功能的需求，特別是無參數的函式需求，會消除許多現有的類別。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-154">The requirements of the hash table feature, especially the parameterless constructor requirement, eliminate many existing classes.</span></span> <span data-ttu-id="bd0fb-155">不過，大部分的 PowerShell _選項_ 類別都是設計來使用這項功能，以及其他非常實用的類別，例如 **ProcessStartInfo** 類別。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-155">However, most PowerShell _option_ classes are designed to work with this feature, as well as other very useful classes, such as the **ProcessStartInfo** class.</span></span>

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

<span data-ttu-id="bd0fb-156">設定參數值時，您也可以使用雜湊表功能。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-156">You can also use the hash table feature when setting parameter values.</span></span> <span data-ttu-id="bd0fb-157">例如，的 **SessionOption** 參數值 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-157">For example, the value of the **SessionOption** parameter of the `New-PSSession`.</span></span>
<span data-ttu-id="bd0fb-158">Cmdlet 可以是雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-158">cmdlet can be a hash table.</span></span>

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

## <a name="generic-objects"></a><span data-ttu-id="bd0fb-159">泛型物件</span><span class="sxs-lookup"><span data-stu-id="bd0fb-159">Generic objects</span></span>

<span data-ttu-id="bd0fb-160">您也可以在 PowerShell 中建立泛型物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-160">You can also create generic objects in PowerShell.</span></span> <span data-ttu-id="bd0fb-161">泛型是指一些類別、結構、介面與方法，其具有所儲存或使用之一或多個類型的預留位置 (類型參數)。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-161">Generics are classes, structures, interfaces, and methods that have placeholders (type parameters) for one or more of the types that they store or use.</span></span>

<span data-ttu-id="bd0fb-162">下列範例會建立 **Dictionary** 物件。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-162">The following example creates a **Dictionary** object.</span></span>

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

<span data-ttu-id="bd0fb-163">如需泛型的詳細資訊，請參閱 [.net 中的泛型](/dotnet/standard/generics)。</span><span class="sxs-lookup"><span data-stu-id="bd0fb-163">For more information on Generics, see [Generics in .NET](/dotnet/standard/generics).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd0fb-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd0fb-164">See also</span></span>

[<span data-ttu-id="bd0fb-165">about_Objects</span><span class="sxs-lookup"><span data-stu-id="bd0fb-165">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="bd0fb-166">about_Methods</span><span class="sxs-lookup"><span data-stu-id="bd0fb-166">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="bd0fb-167">about_Properties</span><span class="sxs-lookup"><span data-stu-id="bd0fb-167">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="bd0fb-168">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="bd0fb-168">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="bd0fb-169">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="bd0fb-169">about_Types.ps1xml</span></span>](about_Types.ps1xml.md)
