---
ms.date: 09/13/2016
ms.topic: reference
title: 延伸輸出物件
description: 延伸輸出物件
ms.openlocfilehash: 9fea476e3032002bd206609313581cc6373dfddc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652909"
---
# <a name="extending-output-objects"></a><span data-ttu-id="e6ffa-103">延伸輸出物件</span><span class="sxs-lookup"><span data-stu-id="e6ffa-103">Extending Output Objects</span></span>

<span data-ttu-id="e6ffa-104">您可以使用 ( .ps1xml) 的類型檔案，擴充 Cmdlet、函式和腳本所傳回的 .NET Framework 物件。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-104">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="e6ffa-105">類型檔案是以 XML 為基礎的檔案，可讓您將屬性和方法新增至現有的物件。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-105">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="e6ffa-106">例如，Windows PowerShell 提供 Types.ps1的 xml 檔，這會將專案新增至數個現有的 .NET Framework 物件。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-106">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="e6ffa-107">Types.ps1xml 檔案位於 Windows PowerShell 安裝目錄 (`$pshome`) 。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-107">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="e6ffa-108">您可以建立自己的類型檔案，進一步擴充這些物件或擴充其他物件。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-108">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="e6ffa-109">當您使用類型檔案來擴充物件時，會以新的元素擴充物件的任何實例。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-109">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="e6ffa-110">擴充 System.object 陣列物件</span><span class="sxs-lookup"><span data-stu-id="e6ffa-110">Extending the System.Array Object</span></span>

<span data-ttu-id="e6ffa-111">下列範例顯示 Windows PowerShell 如何擴充 Types.ps1xml 檔案中的 [system.object](/dotnet/api/System.Array) 物件。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-111">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="e6ffa-112">依預設， [system.object](/dotnet/api/System.Array) 物件有一個 `Length` 屬性，會列出陣列中的物件數目。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-112">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="e6ffa-113">不過，因為名稱 "length" 並不清楚地描述屬性，Windows PowerShell 加入 `Count` alias 屬性，它會顯示與屬性相同的值 `Length` 。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-113">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="e6ffa-114">下列 XML 會將 `Count` 屬性加入至 [system.object](/dotnet/api/System.Array) 型別。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-114">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

<span data-ttu-id="e6ffa-115">若要查看這個新的別名屬性，請使用任何陣列上的 [Get 成員](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) 命令，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-115">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="e6ffa-116">此命令會傳回下列結果。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-116">The command returns the following results.</span></span>

```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```

<span data-ttu-id="e6ffa-117">您可以使用 `Count` 屬性或 `Length` 屬性來判斷陣列中有多少物件。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-117">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="e6ffa-118">例如：</span><span class="sxs-lookup"><span data-stu-id="e6ffa-118">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="e6ffa-119">自訂類型檔案</span><span class="sxs-lookup"><span data-stu-id="e6ffa-119">Custom Types Files</span></span>

<span data-ttu-id="e6ffa-120">若要建立自訂類型檔案，請從複製現有的類型檔案開始。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-120">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="e6ffa-121">新檔案可以有任何名稱，但它的副檔名必須是 .ps1xml。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-121">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="e6ffa-122">當您複製檔案時，可以將新檔案放在 Windows PowerShell 可存取的任何目錄中，但是將檔案放在 Windows PowerShell 安裝目錄 (`$pshome`) 或安裝目錄的子目錄中會很有用。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-122">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="e6ffa-123">若要將您自己的擴充類型加入至檔案中，請為您想要擴充的每個物件加入類型元素。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-123">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="e6ffa-124">下列主題提供範例。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-124">The following topics provide examples.</span></span>

- <span data-ttu-id="e6ffa-125">如需加入屬性和屬性集的詳細資訊，請參閱 [擴充屬性](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="e6ffa-125">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="e6ffa-126">如需新增方法的詳細資訊，請參閱 [擴充方法](./defining-default-methods-for-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-126">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="e6ffa-127">如需新增成員集的詳細資訊，請參閱 [擴充成員集合](./defining-default-member-sets-for-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-127">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="e6ffa-128">在您定義自己的擴充類型之後，請使用下列其中一種方法來讓您的擴充物件可供使用：</span><span class="sxs-lookup"><span data-stu-id="e6ffa-128">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="e6ffa-129">若要讓您的擴充類型檔案可用於目前的會話，請使用 [TypeData 指令程式](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) 來新增檔案。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-129">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="e6ffa-130">如果您想要讓您的類型優先于其他類型檔案中定義的類型 (包括 Types.ps1xml 檔案) ，請使用 `PrependData` [TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-130">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="e6ffa-131">若要讓您的擴充類型檔案可供所有未來的會話使用，請將類型檔案新增至模組、匯出目前的會話，或將 [TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) 命令新增至您的 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-131">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="e6ffa-132">簽署類型檔案</span><span class="sxs-lookup"><span data-stu-id="e6ffa-132">Signing Types Files</span></span>

<span data-ttu-id="e6ffa-133">類型檔案應經過數位簽署，以防止篡改，因為 XML 可以包含腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="e6ffa-133">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="e6ffa-134">如需有關新增數位簽章的詳細資訊，請參閱 [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="e6ffa-134">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="e6ffa-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6ffa-135">See Also</span></span>

[<span data-ttu-id="e6ffa-136">定義物件的預設屬性</span><span class="sxs-lookup"><span data-stu-id="e6ffa-136">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="e6ffa-137">定義物件的預設方法</span><span class="sxs-lookup"><span data-stu-id="e6ffa-137">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="e6ffa-138">定義物件的預設成員集合</span><span class="sxs-lookup"><span data-stu-id="e6ffa-138">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="e6ffa-139">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e6ffa-139">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
