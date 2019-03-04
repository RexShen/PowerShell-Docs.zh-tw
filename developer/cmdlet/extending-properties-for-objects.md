---
title: 擴充物件的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854524"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="4e681-102">延伸物件的屬性</span><span class="sxs-lookup"><span data-stu-id="4e681-102">Extending Properties for Objects</span></span>

<span data-ttu-id="4e681-103">當您擴充.NET Framework 物件時，您可以新增別名屬性，程式碼屬性、 附註屬性、 指令碼屬性和屬性集的物件。</span><span class="sxs-lookup"><span data-stu-id="4e681-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="4e681-104">用來定義這些屬性的 XML 是由下列各節所述。</span><span class="sxs-lookup"><span data-stu-id="4e681-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="4e681-105">下列各節中的範例是從 Windows PowerShell 安裝目錄中預設 Types.ps1xml 類型檔案 (`$pshome`)。</span><span class="sxs-lookup"><span data-stu-id="4e681-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="4e681-106">別名屬性</span><span class="sxs-lookup"><span data-stu-id="4e681-106">Alias Properties</span></span>

<span data-ttu-id="4e681-107">別名屬性定義的現有屬性的新名稱。</span><span class="sxs-lookup"><span data-stu-id="4e681-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="4e681-108">在下列範例中，`Count`屬性會加入至[System.Array？Displayproperty = Fullname>](/dotnet/api/System.Array)型別。</span><span class="sxs-lookup"><span data-stu-id="4e681-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="4e681-109">[AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1)項目會定義為別名屬性的擴充的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="4e681-110">[名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定新的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e681-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="4e681-111">此外， [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a)項目會指定現有的屬性所參考的別名。</span><span class="sxs-lookup"><span data-stu-id="4e681-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="4e681-112">(您也可以加入[AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1)的成員的項目[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)</span><span class="sxs-lookup"><span data-stu-id="4e681-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="4e681-113">程式碼屬性</span><span class="sxs-lookup"><span data-stu-id="4e681-113">Code Properties</span></span>

<span data-ttu-id="4e681-114">程式碼屬性參考.NET Framework 物件的靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="4e681-115">在下列範例中，`Node`屬性會加入至[System.IO.Directoryinfo？Displayproperty = Fullname>](/dotnet/api/System.IO.DirectoryInfo)型別。</span><span class="sxs-lookup"><span data-stu-id="4e681-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="4e681-116">[CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db)項目會定義為程式碼屬性的擴充的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="4e681-117">[名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定擴充屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e681-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="4e681-118">此外， [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0)項目會定義擴充屬性所參考的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="4e681-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="4e681-119">(您也可以加入[CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db)的成員的項目[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)</span><span class="sxs-lookup"><span data-stu-id="4e681-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a><span data-ttu-id="4e681-120">附註屬性</span><span class="sxs-lookup"><span data-stu-id="4e681-120">Note Properties</span></span>

<span data-ttu-id="4e681-121">附註屬性會定義具有靜態值的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="4e681-122">在下列範例中， `Status` （其值一律是 「 成功 」） 的屬性會加入至[System.IO.Directoryinfo？Displayproperty = Fullname>](/dotnet/api/System.IO.DirectoryInfo)型別。</span><span class="sxs-lookup"><span data-stu-id="4e681-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="4e681-123">[NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb)項目為附註屬性，定義擴充的屬性[名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目指定名稱的擴充屬性，而[值](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c)項目指定的擴充屬性的靜態值。</span><span class="sxs-lookup"><span data-stu-id="4e681-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="4e681-124">( [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb)元素也可以加入的成員[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)</span><span class="sxs-lookup"><span data-stu-id="4e681-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a><span data-ttu-id="4e681-125">指令碼屬性</span><span class="sxs-lookup"><span data-stu-id="4e681-125">Script Properties</span></span>

<span data-ttu-id="4e681-126">指令碼屬性定義的屬性，且值為指令碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="4e681-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="4e681-127">在下列範例中，`VersionInfo`屬性會加入至[System.IO.Fileinfo？Displayproperty = Fullname>](/dotnet/api/System.IO.FileInfo)型別。</span><span class="sxs-lookup"><span data-stu-id="4e681-127">In the following example, the `VersionInfo` property is added to the [System.IO.Fileinfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="4e681-128">[ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350)項目會定義為指令碼屬性的擴充的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="4e681-129">[名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定擴充屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e681-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="4e681-130">此外， [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c)項目會指定產生的屬性值的指令碼。</span><span class="sxs-lookup"><span data-stu-id="4e681-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="4e681-131">(您也可以加入[ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350)的成員的項目[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)</span><span class="sxs-lookup"><span data-stu-id="4e681-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a><span data-ttu-id="4e681-132">屬性集</span><span class="sxs-lookup"><span data-stu-id="4e681-132">Property Sets</span></span>

<span data-ttu-id="4e681-133">屬性集定義一組可參考的集合名稱的擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="4e681-134">例如，`Property`的參數[Format-table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)指令程式可以指定將特定的屬性設定為顯示。</span><span class="sxs-lookup"><span data-stu-id="4e681-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="4e681-135">當指定屬性集時，會顯示只有屬於集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>
<span data-ttu-id="4e681-136">屬性集定義一組可參考的集合名稱的擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="4e681-137">例如，`Property`的參數[Format-table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)指令程式可以指定將特定的屬性設定為顯示。</span><span class="sxs-lookup"><span data-stu-id="4e681-137">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="4e681-138">當指定屬性集時，會顯示只有屬於集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="4e681-139">可以針對物件定義的屬性集的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="4e681-139">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="4e681-140">不過，必須指定用來定義物件的預設顯示屬性的屬性集 PSStandardMembers 成員集內。</span><span class="sxs-lookup"><span data-stu-id="4e681-140">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="4e681-141">在 Types.ps1xml 類型檔案中，預設屬性集名稱會包含 DefaultDisplayProperty、 DefaultDisplayPropertySet 和 DefaultKeyPropertySet。</span><span class="sxs-lookup"><span data-stu-id="4e681-141">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="4e681-142">您將新增至 PSStandardMembers 成員集的任何額外的屬性集都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="4e681-142">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="4e681-143">在下列範例中，DefaultDisplayPropertySet 屬性集新增至 PSStandardMembers 成員集的[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)型別。</span><span class="sxs-lookup"><span data-stu-id="4e681-143">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="4e681-144">[PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188)項目定義的屬性群組。</span><span class="sxs-lookup"><span data-stu-id="4e681-144">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="4e681-145">[名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定屬性集的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e681-145">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="4e681-146">此外， [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786)項目會指定集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e681-146">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="4e681-147">(您也可以加入[PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188)的成員的項目[型別](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe)項目。)</span><span class="sxs-lookup"><span data-stu-id="4e681-147">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="4e681-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e681-148">See Also</span></span>

[<span data-ttu-id="4e681-149">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e681-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
