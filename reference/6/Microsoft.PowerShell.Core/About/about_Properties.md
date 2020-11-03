---
description: 描述如何在 PowerShell 中使用物件屬性。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: 5c4efd3f94d8ce8fbb7c66db1cc5f91eebd0756e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206959"
---
# <a name="about-properties"></a><span data-ttu-id="0420f-104">關於屬性</span><span class="sxs-lookup"><span data-stu-id="0420f-104">About Properties</span></span>

## <a name="short-description"></a><span data-ttu-id="0420f-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="0420f-105">Short description</span></span>
<span data-ttu-id="0420f-106">描述如何在 PowerShell 中使用物件屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-106">Describes how to use object properties in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0420f-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="0420f-107">Long description</span></span>

<span data-ttu-id="0420f-108">PowerShell 會使用稱為物件的結構化集合來代表資料存放區中的專案或電腦的狀態。</span><span class="sxs-lookup"><span data-stu-id="0420f-108">PowerShell uses structured collections of information called objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="0420f-109">一般而言，您會使用屬於 Microsoft .NET Framework 的物件，但您也可以在 PowerShell 中建立自訂物件。</span><span class="sxs-lookup"><span data-stu-id="0420f-109">Typically, you work with object that are part of the Microsoft .NET Framework, but you can also create custom objects in PowerShell.</span></span>

<span data-ttu-id="0420f-110">項目和其物件之間的關聯非常緊密。</span><span class="sxs-lookup"><span data-stu-id="0420f-110">The association between an item and its object is very close.</span></span> <span data-ttu-id="0420f-111">當您變更物件時，通常會變更其所代表的項目。</span><span class="sxs-lookup"><span data-stu-id="0420f-111">When you change an object, you usually change the item that it represents.</span></span> <span data-ttu-id="0420f-112">例如，當您在 PowerShell 中取得檔案時，不會取得實際的檔案。</span><span class="sxs-lookup"><span data-stu-id="0420f-112">For example, when you get a file in PowerShell, you do not get the actual file.</span></span> <span data-ttu-id="0420f-113">而是會取得代表該檔案的 FileInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="0420f-113">Instead, you get a FileInfo object that represents the file.</span></span> <span data-ttu-id="0420f-114">當您變更 FileInfo 物件時，檔案也會變更。</span><span class="sxs-lookup"><span data-stu-id="0420f-114">When you change the FileInfo object, the file changes too.</span></span>

<span data-ttu-id="0420f-115">大部分的物件都具有屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-115">Most objects have properties.</span></span> <span data-ttu-id="0420f-116">屬性是與物件相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="0420f-116">Properties are the data that is associated with an object.</span></span> <span data-ttu-id="0420f-117">不同類型的物件有不同的屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-117">Different types of object have different properties.</span></span> <span data-ttu-id="0420f-118">例如，代表檔案的 FileInfo 物件具有 **IsReadOnly** 屬性，如果檔案是唯讀屬性，則會包含 $True，如果沒有，則為 $False。</span><span class="sxs-lookup"><span data-stu-id="0420f-118">For example, a FileInfo object, which represents a file, has an **IsReadOnly** property that contains $True if the file the read-only attribute and $False if it does not.</span></span>
<span data-ttu-id="0420f-119">代表檔案系統目錄的 DirectoryInfo 物件具有一個父屬性，其中包含父目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="0420f-119">A DirectoryInfo object, which represents a file system directory, has a Parent property that contains the path to the parent directory.</span></span>

### <a name="object-properties"></a><span data-ttu-id="0420f-120">物件屬性</span><span class="sxs-lookup"><span data-stu-id="0420f-120">Object properties</span></span>

<span data-ttu-id="0420f-121">若要取得物件的屬性，請使用 `Get-Member` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0420f-121">To get the properties of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="0420f-122">例如，若要取得 **FileInfo** 物件的屬性，請使用 `Get-ChildItem` Cmdlet 取得代表檔案的 FileInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="0420f-122">For example, to get the properties of a **FileInfo** object, use the `Get-ChildItem` cmdlet to get the FileInfo object that represents a file.</span></span> <span data-ttu-id="0420f-123">然後，使用管線運算子 ( # A0) 將 **FileInfo** 物件傳送至 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="0420f-123">Then, use a pipeline operator (&#124;) to send the **FileInfo** object to `Get-Member`.</span></span> <span data-ttu-id="0420f-124">下列命令會取得 PowerShell.exe 的檔案，並將它傳送至 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="0420f-124">The following command gets the PowerShell.exe file and sends it to `Get-Member`.</span></span>
<span data-ttu-id="0420f-125">\$Pshome 自動變數包含 PowerShell 安裝目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="0420f-125">The \$Pshome automatic variable contains the path of the PowerShell installation directory.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

<span data-ttu-id="0420f-126">命令的輸出會列出 **FileInfo** 物件的成員。</span><span class="sxs-lookup"><span data-stu-id="0420f-126">The output of the command lists the members of the **FileInfo** object.</span></span>
<span data-ttu-id="0420f-127">成員包含屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="0420f-127">Members include both properties and methods.</span></span> <span data-ttu-id="0420f-128">當您在 PowerShell 中工作時，您可以存取物件的所有成員。</span><span class="sxs-lookup"><span data-stu-id="0420f-128">When you work in PowerShell, you have access to all the members of the objects.</span></span>

<span data-ttu-id="0420f-129">若只要取得物件的屬性，而不只取得方法的屬性，請使用 Cmdlet 的 MemberType 參數搭配 `Get-Member` "property" 的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0420f-129">To get only the properties of an object and not the methods, use the MemberType parameter of the `Get-Member` cmdlet with a value of "property", as shown in the following example.</span></span>

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

<span data-ttu-id="0420f-130">找到屬性之後，您就可以在 PowerShell 命令中使用它們。</span><span class="sxs-lookup"><span data-stu-id="0420f-130">After you find the properties, you can use them in your PowerShell commands.</span></span>

## <a name="property-values"></a><span data-ttu-id="0420f-131">屬性值</span><span class="sxs-lookup"><span data-stu-id="0420f-131">Property values</span></span>

<span data-ttu-id="0420f-132">雖然特定類型的每個物件具有相同的屬性，這些屬性的值會描述特定的物件。</span><span class="sxs-lookup"><span data-stu-id="0420f-132">Although every object of a specific type has the same properties, the values of those properties describe the particular object.</span></span> <span data-ttu-id="0420f-133">例如，每個 FileInfo 物件都具有 CreationTime 屬性，但每個檔案的這個屬性值不同。</span><span class="sxs-lookup"><span data-stu-id="0420f-133">For example, every FileInfo object has a CreationTime property, but the value of that property differs for each file.</span></span>

<span data-ttu-id="0420f-134">取得物件屬性最長見的方式，是使用點方法。</span><span class="sxs-lookup"><span data-stu-id="0420f-134">The most common way to get the values of the properties of an object is to use the dot method.</span></span> <span data-ttu-id="0420f-135">輸入物件的參考 (例如，包含物件的變數) 或輸入取得物件的命令。</span><span class="sxs-lookup"><span data-stu-id="0420f-135">Type a reference to the object, such as a variable that contains the object, or a command that gets the object.</span></span> <span data-ttu-id="0420f-136">接著輸入點 (.)，後面加上屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="0420f-136">Then, type a dot (.) followed by the property name.</span></span>

<span data-ttu-id="0420f-137">例如，下列命令顯示 PowerShell.exe 檔案的 CreationTime 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0420f-137">For example, the following command displays the value of the CreationTime property of the PowerShell.exe file.</span></span> <span data-ttu-id="0420f-138">此 `Get-ChildItem` 命令會傳回代表 PowerShell.exe 檔案的 FileInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="0420f-138">The `Get-ChildItem` command returns a FileInfo object that represents the PowerShell.exe file.</span></span> <span data-ttu-id="0420f-139">命令以括號括住，可確保先執行命令再存取任何屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-139">The command is enclosed in parentheses to make sure that it is executed before any properties are accessed.</span></span> <span data-ttu-id="0420f-140">`Get-ChildItem`命令後面會加上點和 CreationTime 屬性的名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0420f-140">The `Get-ChildItem` command is followed by a dot and the name of the CreationTime property, as follows:</span></span>

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="0420f-141">您可以也儲存變數中的物件，然後使用點方法取得其屬性，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="0420f-141">You can also save an object in a variable and then get its properties by using the dot method, as shown in the following example:</span></span>

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="0420f-142">您也可以使用 `Select-Object` 和 `Format-List` Cmdlet 來顯示物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="0420f-142">You can also use the `Select-Object` and `Format-List` cmdlets to display the property values of an object.</span></span> <span data-ttu-id="0420f-143">`Select-Object` 而且 `Format-List` 每一個都有一個 **Property** 參數。</span><span class="sxs-lookup"><span data-stu-id="0420f-143">`Select-Object` and `Format-List` each have a **Property** parameter.</span></span> <span data-ttu-id="0420f-144">您可以使用 **Property** 參數來指定一個或多個屬性及其值。</span><span class="sxs-lookup"><span data-stu-id="0420f-144">You can use the **Property** parameter to specify one or more properties and their values.</span></span> <span data-ttu-id="0420f-145">或者，您可以使用萬用字元 (\*) 代表所有屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-145">Or, you can use the wildcard character (\*) to represent all the properties.</span></span>

<span data-ttu-id="0420f-146">例如，下列命令顯示 PowerShell.exe 檔案的所有屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0420f-146">For example, the following command displays the values of all the properties of the PowerShell.exe file.</span></span>

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

### <a name="static-properties"></a><span data-ttu-id="0420f-147">靜態屬性</span><span class="sxs-lookup"><span data-stu-id="0420f-147">Static properties</span></span>

<span data-ttu-id="0420f-148">您可以在 PowerShell 中使用 .NET 類別的靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-148">You can use the static properties of .NET classes in PowerShell.</span></span> <span data-ttu-id="0420f-149">靜態屬性是類別的屬性，有別於標準屬性，它們是物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-149">Static properties are properties of class, unlike standard properties, which are properties of an object.</span></span>

<span data-ttu-id="0420f-150">若要取得類別的靜態屬性，請使用 Get-Member Cmdlet 的靜態參數。</span><span class="sxs-lookup"><span data-stu-id="0420f-150">To get the static properties of an class, use the Static parameter of the Get-Member cmdlet.</span></span>

<span data-ttu-id="0420f-151">例如，下列命令會取得類別的靜態屬性 `System.DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="0420f-151">For example, the following command gets the static properties of the `System.DateTime` class.</span></span>

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

<span data-ttu-id="0420f-152">若要取得靜態屬性的值，請使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="0420f-152">To get the value of a static property, use the following syntax.</span></span>

```
[<ClassName>]::<Property>
```

<span data-ttu-id="0420f-153">例如，下列命令會取得類別 UtcNow 靜態屬性的值 `System.DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="0420f-153">For example, the following command gets the value of the UtcNow static property of the `System.DateTime` class.</span></span>

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a><span data-ttu-id="0420f-154">純量物件和集合的屬性</span><span class="sxs-lookup"><span data-stu-id="0420f-154">Properties of scalar objects and collections</span></span>

<span data-ttu-id="0420f-155">特定類型的單一 (「純量」) 物件屬性通常不同於同類型物件集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-155">The properties of one ("scalar") object of a particular type are often different from the properties of a collection of objects of the same type.</span></span>
<span data-ttu-id="0420f-156">例如，每個服務都有 **displayname** 屬性，但服務的集合沒有 **displayname** 屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-156">For example, every service has as **DisplayName** property, but a collection of services does not have a **DisplayName** property.</span></span>

<span data-ttu-id="0420f-157">下列命令會取得 ' Audiosrv ' 服務的 **DisplayName** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="0420f-157">The following command gets the value of the **DisplayName** property of the 'Audiosrv' service.</span></span>

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

<span data-ttu-id="0420f-158">從 PowerShell 3.0 開始，PowerShell 會嘗試避免因為純量物件和集合的不同屬性而產生的腳本錯誤。</span><span class="sxs-lookup"><span data-stu-id="0420f-158">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing properties of scalar objects and collections.</span></span> <span data-ttu-id="0420f-159">相同的命令會傳回傳回之每個服務的 **DisplayName** 屬性值 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="0420f-159">The same command returns the value of the **DisplayName** property of every service that `Get-Service` returns.</span></span>

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

<span data-ttu-id="0420f-160">當您提交集合，但要求只存在單一 ( 「純量」 ) 物件上的屬性時，PowerShell 會針對集合中的每個物件傳回該屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0420f-160">When you submit a collection, but request a property that exists only on single ("scalar") objects, PowerShell returns the value of that property for every object in the collection.</span></span>

<span data-ttu-id="0420f-161">所有集合都有一個 **Count** 屬性，會傳回集合中的物件數目。</span><span class="sxs-lookup"><span data-stu-id="0420f-161">All collections have a **Count** property that returns how many objects are in the collection.</span></span>

```powershell
(Get-Service).Count
```

```output
176
```

<span data-ttu-id="0420f-162">從 PowerShell 3.0 開始，如果您要求零個物件或一個物件的 Count 或 Length 屬性，PowerShell 就會傳回正確的值。</span><span class="sxs-lookup"><span data-stu-id="0420f-162">Beginning in PowerShell 3.0, if you request the Count or Length property of zero objects or one object, PowerShell returns the correct value.</span></span>

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

<span data-ttu-id="0420f-163">如果屬性存在於個別的物件和集合上，則只會傳回集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="0420f-163">If a property exists on the individual objects and on the collection, only the collection's property is returned.</span></span>

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

<span data-ttu-id="0420f-164">這項功能也適用於純量物件和集合的方法。</span><span class="sxs-lookup"><span data-stu-id="0420f-164">This feature also works on methods of scalar objects and collections.</span></span> <span data-ttu-id="0420f-165">如需詳細資訊，請參閱 [about_Methods](about_methods.md)。</span><span class="sxs-lookup"><span data-stu-id="0420f-165">For more information, see [about_Methods](about_methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0420f-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0420f-166">See also</span></span>

[<span data-ttu-id="0420f-167">about_Methods</span><span class="sxs-lookup"><span data-stu-id="0420f-167">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="0420f-168">about_Objects</span><span class="sxs-lookup"><span data-stu-id="0420f-168">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="0420f-169">Get-Member</span><span class="sxs-lookup"><span data-stu-id="0420f-169">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

[<span data-ttu-id="0420f-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="0420f-170">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="0420f-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="0420f-171">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)
