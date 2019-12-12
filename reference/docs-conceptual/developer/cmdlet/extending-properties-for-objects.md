---
title: 擴充物件的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364447"
---
# <a name="extending-properties-for-objects"></a>延伸物件的屬性

當您擴充 .NET Framework 物件時，您可以將別名屬性、程式碼屬性、附注屬性、腳本屬性和屬性集加入至物件。 下列各節將說明定義這些屬性的 XML。

> [!NOTE]
> 下列各節中的範例來自 PowerShell 安裝目錄（`$PSHOME`）中的預設 `Types.ps1xml` 類型檔案。 如需詳細資訊，請參閱[關於類型. types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)。

## <a name="alias-properties"></a>別名屬性

Alias 屬性會定義現有屬性的新名稱。

在下列範例中， **Count**屬性會加入至[system.object](/dotnet/api/System.Array)類型。 [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty)元素會將擴充屬性定義為別名屬性。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定新的名稱。 而且， [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername)元素會指定別名所參考的現有屬性。 您也可以將 `AliasProperty` 專案新增至[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成員。

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

## <a name="code-properties"></a>程式碼屬性

Code 屬性會參考 .NET Framework 物件的靜態屬性。

在下列範例中， **Mode**屬性會新增至[DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo)類型。 [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty)元素會將擴充屬性定義為程式碼屬性。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定擴充屬性的名稱。 而且， [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference)元素會定義擴充屬性所參考的靜態方法。 您也可以將 `CodeProperty` 專案新增至[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成員。

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

## <a name="note-properties"></a>注意屬性

Note 屬性會定義具有靜態值的屬性。

在下列範例中， **Status**屬性（其值一律為**Success**）會新增至[DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo)類型。 [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty)元素會將擴充屬性定義為附注屬性。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定擴充屬性的名稱。 [Value](/dotnet/api/system.management.automation.psnoteproperty.value)元素會指定擴充屬性的靜態值。 `NoteProperty` 專案也可以加入至[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成員。

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

## <a name="script-properties"></a>腳本屬性

腳本屬性會定義屬性，其值為腳本的輸出。

在下列範例中， **VersionInfo**屬性會新增至[FileInfo](/dotnet/api/System.IO.FileInfo)類型。 [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty)元素會將擴充屬性定義為腳本屬性。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定擴充屬性的名稱。 而且， [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript)元素會指定產生屬性值的腳本。 您也可以將 `ScriptProperty` 專案新增至[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成員。

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

## <a name="property-sets"></a>屬性集

屬性集會定義一組可由集合名稱參考的擴充屬性。
例如，[格式資料表](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**屬性**參數可以指定要顯示的特定屬性集。 當指定屬性集時，只會顯示屬於該集合的屬性。

對於可針對物件定義的屬性集數目並沒有任何限制。 不過，用來定義物件預設顯示內容的屬性集必須在**PSStandardMembers**成員集內指定。 在 `Types.ps1xml` 類型檔案中，預設的屬性集名稱包括**DefaultDisplayProperty**、 **DefaultDisplayPropertySet**和**DefaultKeyPropertySet**。 您加入至**PSStandardMembers**成員集的任何其他屬性集都會被忽略。

在下列範例中， **DefaultDisplayPropertySet**屬性集會加入至[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)類型的**PSStandardMembers**成員集。 [PropertySet](/dotnet/api/system.management.automation.pspropertyset)元素會定義屬性的群組。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素會指定屬性集的名稱。 而且， [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames)元素會指定集合的屬性。 您也可以將 `PropertySet` 元素加入至[Type](/dotnet/api/system.management.automation.pstypename)元素的成員。

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

## <a name="see-also"></a>另請參閱

[關於類型. types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[系統管理自動化](/dotnet/api/System.Management.Automation)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
