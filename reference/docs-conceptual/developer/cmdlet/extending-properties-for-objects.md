---
ms.date: 08/21/2019
ms.topic: reference
title: 延伸物件的屬性
description: 延伸物件的屬性
ms.openlocfilehash: 37803d9fd87319204565c2abde62f269744481b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652882"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="3d1e4-103">延伸物件的屬性</span><span class="sxs-lookup"><span data-stu-id="3d1e4-103">Extending Properties for Objects</span></span>

<span data-ttu-id="3d1e4-104">當您擴充 .NET Framework 物件時，您可以將別名屬性、程式碼屬性、附注屬性、腳本屬性和屬性集加入至物件。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-104">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="3d1e4-105">下列各節將說明定義這些屬性的 XML。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-105">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="3d1e4-106">下列各節中的範例是來自 `Types.ps1xml` PowerShell 安裝目錄中的預設類型檔案 (`$PSHOME`) 。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-106">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="3d1e4-107">如需詳細資訊，請參閱 [關於 Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-107">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="3d1e4-108">別名屬性</span><span class="sxs-lookup"><span data-stu-id="3d1e4-108">Alias properties</span></span>

<span data-ttu-id="3d1e4-109">Alias 屬性會定義現有屬性的新名稱。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-109">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="3d1e4-110">在下列範例中， **Count** 屬性會加入至 [system.object](/dotnet/api/System.Array) 型別。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-110">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="3d1e4-111">[AliasProperty](/dotnet/api/system.management.automation.psaliasproperty)元素會將擴充屬性定義為別名屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-111">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="3d1e4-112">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定新的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-112">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="3d1e4-113">而且， [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) 元素會指定別名所參考的現有屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-113">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="3d1e4-114">您也可以將 `AliasProperty` 元素加入至 [MemberSets](/dotnet/api/system.management.automation.psmemberset) 專案的成員。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-114">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="3d1e4-115">程式碼屬性</span><span class="sxs-lookup"><span data-stu-id="3d1e4-115">Code properties</span></span>

<span data-ttu-id="3d1e4-116">程式碼屬性會參考 .NET Framework 物件的靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-116">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="3d1e4-117">在下列範例中， **Mode** 屬性會加入 [DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) 類型。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-117">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="3d1e4-118">[CodeProperty](/dotnet/api/system.management.automation.pscodeproperty)元素會將擴充屬性定義為程式碼屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-118">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="3d1e4-119">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定擴充屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-119">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="3d1e4-120">而且， [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) 元素會定義擴充屬性所參考的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-120">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="3d1e4-121">您也可以將 `CodeProperty` 元素加入至 [MemberSets](/dotnet/api/system.management.automation.psmemberset) 專案的成員。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-121">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="3d1e4-122">注意屬性</span><span class="sxs-lookup"><span data-stu-id="3d1e4-122">Note properties</span></span>

<span data-ttu-id="3d1e4-123">Note 屬性會定義具有靜態值的屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-123">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="3d1e4-124">在下列範例中， **Status** 屬性（其值一律為 **Success**）會新增至 [DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) 類型。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-124">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="3d1e4-125">[NoteProperty](/dotnet/api/system.management.automation.psnoteproperty)元素會將擴充屬性定義為附注屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-125">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="3d1e4-126">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定擴充屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-126">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="3d1e4-127">[Value](/dotnet/api/system.management.automation.psnoteproperty.value)元素會指定擴充屬性的靜態值。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-127">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="3d1e4-128">`NoteProperty`元素也可以加入至[MemberSets](/dotnet/api/system.management.automation.psmemberset)專案的成員。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-128">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="3d1e4-129">腳本屬性</span><span class="sxs-lookup"><span data-stu-id="3d1e4-129">Script properties</span></span>

<span data-ttu-id="3d1e4-130">腳本屬性會定義其值為腳本輸出的屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-130">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="3d1e4-131">在下列範例中， **VersionInfo** 屬性會新增至 [FileInfo](/dotnet/api/System.IO.FileInfo) 類型。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-131">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="3d1e4-132">[ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty)元素會將擴充屬性定義為腳本屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-132">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="3d1e4-133">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定擴充屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-133">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="3d1e4-134">而且， [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) 元素會指定產生屬性值的腳本。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-134">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="3d1e4-135">您也可以將 `ScriptProperty` 元素加入至 [MemberSets](/dotnet/api/system.management.automation.psmemberset) 專案的成員。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-135">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="3d1e4-136">屬性集</span><span class="sxs-lookup"><span data-stu-id="3d1e4-136">Property sets</span></span>

<span data-ttu-id="3d1e4-137">屬性集會定義一組可由集合名稱參考的擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-137">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="3d1e4-138">例如， [Format 資料表](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) 
 **屬性** 參數可以指定要顯示的特定屬性集。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-138">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="3d1e4-139">當指定屬性集時，只會顯示屬於該集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-139">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="3d1e4-140">可以針對物件定義的屬性集數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-140">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="3d1e4-141">但是，用來定義物件預設顯示內容的屬性集必須在 **PSStandardMembers** 成員集內指定。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-141">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="3d1e4-142">在類型檔案中 `Types.ps1xml` ，預設的屬性集名稱包含 **DefaultDisplayProperty**、 **DefaultDisplayPropertySet** 和 **DefaultKeyPropertySet**。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-142">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="3d1e4-143">您加入至 **PSStandardMembers** 成員集的任何其他屬性集都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-143">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="3d1e4-144">在下列範例中， **DefaultDisplayPropertySet** 屬性集會加入至 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)類型的 **PSStandardMembers** 成員集合。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-144">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="3d1e4-145">[PropertySet](/dotnet/api/system.management.automation.pspropertyset)元素會定義屬性的群組。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-145">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="3d1e4-146">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定屬性集的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-146">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="3d1e4-147">而且， [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) 元素會指定集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-147">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="3d1e4-148">您也可以將專案加入 `PropertySet` 至 [Type](/dotnet/api/system.management.automation.pstypename) 元素的成員。</span><span class="sxs-lookup"><span data-stu-id="3d1e4-148">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3d1e4-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="3d1e4-149">See also</span></span>

[<span data-ttu-id="3d1e4-150">關於 Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="3d1e4-150">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="3d1e4-151">System.Management.Automation</span><span class="sxs-lookup"><span data-stu-id="3d1e4-151">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="3d1e4-152">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3d1e4-152">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
