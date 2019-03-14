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
ms.openlocfilehash: be31d03b02394cb1694909cf7b65bbc2a29f6976
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795431"
---
# <a name="extending-properties-for-objects"></a>延伸物件的屬性

當您擴充.NET Framework 物件時，您可以新增別名屬性，程式碼屬性、 附註屬性、 指令碼屬性和屬性集的物件。 用來定義這些屬性的 XML 是由下列各節所述。

> [!NOTE]
> 下列各節中的範例是從 Windows PowerShell 安裝目錄中預設 Types.ps1xml 類型檔案 (`$pshome`)。

## <a name="alias-properties"></a>別名屬性

別名屬性定義的現有屬性的新名稱。

在下列範例中，`Count`屬性會加入至[System.Array？Displayproperty = Fullname>](/dotnet/api/System.Array)型別。 [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1)項目會定義為別名屬性的擴充的屬性。 [名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定新的名稱。 此外， [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a)項目會指定現有的屬性所參考的別名。 (您也可以加入[AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1)的成員的項目[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)

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

程式碼屬性參考.NET Framework 物件的靜態屬性。

在下列範例中，`Node`屬性會加入至[System.IO.Directoryinfo？Displayproperty = Fullname>](/dotnet/api/System.IO.DirectoryInfo)型別。 [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db)項目會定義為程式碼屬性的擴充的屬性。 [名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定擴充屬性的名稱。 此外， [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0)項目會定義擴充屬性所參考的靜態方法。 (您也可以加入[CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db)的成員的項目[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)

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

## <a name="note-properties"></a>附註屬性

附註屬性會定義具有靜態值的屬性。

在下列範例中， `Status` （其值一律是 「 成功 」） 的屬性會加入至[System.IO.Directoryinfo？Displayproperty = Fullname>](/dotnet/api/System.IO.DirectoryInfo)型別。 [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb)項目為附註屬性，定義擴充的屬性[名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目指定名稱的擴充屬性，而[值](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c)項目指定的擴充屬性的靜態值。 ( [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb)元素也可以加入的成員[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)

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

## <a name="script-properties"></a>指令碼屬性

指令碼屬性定義的屬性，且值為指令碼的輸出。

在下列範例中，`VersionInfo`屬性會加入至[System.IO.Fileinfo？Displayproperty = Fullname>](/dotnet/api/System.IO.FileInfo)型別。 [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350)項目會定義為指令碼屬性的擴充的屬性。 [名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定擴充屬性的名稱。 此外， [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c)項目會指定產生的屬性值的指令碼。 (您也可以加入[ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350)的成員的項目[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)

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

屬性集定義一組可參考的集合名稱的擴充屬性。 例如，`Property`的參數[Format-table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)指令程式可以指定將特定的屬性設定為顯示。 當指定屬性集時，會顯示只有屬於集合的屬性。

可以針對物件定義的屬性集的數目沒有限制。 不過，必須指定用來定義物件的預設顯示屬性的屬性集 PSStandardMembers 成員集內。 在 Types.ps1xml 類型檔案中，預設屬性集名稱會包含 DefaultDisplayProperty、 DefaultDisplayPropertySet 和 DefaultKeyPropertySet。 您將新增至 PSStandardMembers 成員集的任何額外的屬性集都會被忽略。

在下列範例中，DefaultDisplayPropertySet 屬性集新增至 PSStandardMembers 成員集的[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)型別。 [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188)項目定義的屬性群組。 [名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定屬性集的名稱。 此外， [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786)項目會指定集合的屬性。 (您也可以加入[PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188)的成員的項目[型別](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe)項目。)

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

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
