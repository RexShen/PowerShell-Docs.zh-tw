---
title: 擴充輸出物件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068159"
---
# <a name="extending-output-objects"></a><span data-ttu-id="5503b-102">延伸輸出物件</span><span class="sxs-lookup"><span data-stu-id="5503b-102">Extending Output Objects</span></span>

<span data-ttu-id="5503b-103">您可以擴充.NET Framework 物件所使用的類型檔案 (.ps1xml) 傳回的 cmdlet、 函數和指令碼。</span><span class="sxs-lookup"><span data-stu-id="5503b-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="5503b-104">類型檔案是以 XML 為基礎，可讓您將屬性和方法新增至現有的物件。</span><span class="sxs-lookup"><span data-stu-id="5503b-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="5503b-105">比方說，Windows PowerShell 會提供將元素加入至數個現有的.NET Framework 物件的 Types.ps1xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="5503b-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="5503b-106">Types.ps1xml 檔案位於 Windows PowerShell 安裝目錄 (`$pshome`)。</span><span class="sxs-lookup"><span data-stu-id="5503b-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="5503b-107">您可以建立您自己的類型檔案以進一步擴充這些物件或擴充其他物件。</span><span class="sxs-lookup"><span data-stu-id="5503b-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="5503b-108">當您擴充物件所使用的類型檔案時，物件的任何執行個體已擴充與新的項目。</span><span class="sxs-lookup"><span data-stu-id="5503b-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="5503b-109">擴充 System.Array 物件</span><span class="sxs-lookup"><span data-stu-id="5503b-109">Extending the System.Array Object</span></span>

<span data-ttu-id="5503b-110">下列範例示範如何擴充 Windows PowerShell [System.Array](/dotnet/api/System.Array) Types.ps1xml 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="5503b-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="5503b-111">根據預設， [System.Array](/dotnet/api/System.Array)物件具有`Length`列出陣列中的物件數目的屬性。</span><span class="sxs-lookup"><span data-stu-id="5503b-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="5503b-112">不過，因為名稱 「 長度 」 不會清楚地描述屬性，Windows PowerShell 新增`Count`別名屬性，它會顯示相同的值`Length`屬性。</span><span class="sxs-lookup"><span data-stu-id="5503b-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="5503b-113">下列 XML 會新增`Count`屬性，以[System.Array](/dotnet/api/System.Array)型別。</span><span class="sxs-lookup"><span data-stu-id="5503b-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="5503b-114">若要查看這個新的別名屬性，請使用[Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)命令上任何的陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5503b-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="5503b-115">此命令會傳回下列結果。</span><span class="sxs-lookup"><span data-stu-id="5503b-115">The command returns the following results.</span></span>
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
<span data-ttu-id="5503b-116">您可以使用`Count`屬性或`Length`屬性來判斷陣列中有多少物件。</span><span class="sxs-lookup"><span data-stu-id="5503b-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="5503b-117">例如：</span><span class="sxs-lookup"><span data-stu-id="5503b-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="5503b-118">自訂類型的檔案</span><span class="sxs-lookup"><span data-stu-id="5503b-118">Custom Types Files</span></span>

<span data-ttu-id="5503b-119">若要建立自訂的類型檔案時，先複製現有的類型檔案。</span><span class="sxs-lookup"><span data-stu-id="5503b-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="5503b-120">新的檔案可以有任何名稱，但它必須有副檔名為.ps1xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="5503b-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="5503b-121">當您將檔案複製，您可以將新的檔案放在可以存取 Windows PowerShell 的任何目錄，但您最好將檔案放在 Windows PowerShell 安裝目錄 (`$pshome`) 或的安裝目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="5503b-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="5503b-122">將您自己的延伸的類型新增至檔案，新增您想要擴充的每個物件的型別項目。</span><span class="sxs-lookup"><span data-stu-id="5503b-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="5503b-123">下列主題提供範例。</span><span class="sxs-lookup"><span data-stu-id="5503b-123">The following topics provide examples.</span></span>

- <span data-ttu-id="5503b-124">如需新增屬性和屬性集的詳細資訊，請參閱[擴充屬性](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="5503b-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="5503b-125">如需有關加入方法的詳細資訊，請參閱[擴充方法](./defining-default-methods-for-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="5503b-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="5503b-126">如需有關如何新增成員集的詳細資訊，請參閱[擴充成員設定](./defining-default-member-sets-for-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="5503b-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="5503b-127">定義您自己的延伸的類型之後，使用其中一種下列方法可讓您擴充的物件：</span><span class="sxs-lookup"><span data-stu-id="5503b-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="5503b-128">若要讓您延伸的類型的檔案目前的工作階段，請使用[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet 來新增新的檔案。</span><span class="sxs-lookup"><span data-stu-id="5503b-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="5503b-129">如果您想要您的型別中所定義的型別中的優先順序高於其他類型檔案 （包括 Types.ps1xml 檔案），請使用`PrependData`的參數[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5503b-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="5503b-130">若要將您的延伸的類型檔案提供給所有未來的工作階段，新增至模組的類型檔案、 匯出目前的工作階段，或新增[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData)命令到您的 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="5503b-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="5503b-131">簽章類型檔案</span><span class="sxs-lookup"><span data-stu-id="5503b-131">Signing Types Files</span></span>

<span data-ttu-id="5503b-132">應該數位簽章類型的檔案，以避免遭到竄改，因為 XML 可以包含指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="5503b-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="5503b-133">如需有關新增數位簽章的詳細資訊，請參閱[about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="5503b-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="5503b-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5503b-134">See Also</span></span>

[<span data-ttu-id="5503b-135">定義物件的預設屬性</span><span class="sxs-lookup"><span data-stu-id="5503b-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="5503b-136">定義物件的預設方法</span><span class="sxs-lookup"><span data-stu-id="5503b-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="5503b-137">為物件定義預設成員集</span><span class="sxs-lookup"><span data-stu-id="5503b-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="5503b-138">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5503b-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
