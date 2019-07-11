---
title: 定義物件的預設方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733989"
---
# <a name="defining-default-methods-for-objects"></a>定義物件的預設方法

當您擴充.NET Framework 物件時，您可以將程式碼方法和指令碼方法新增至物件。 用來定義這些方法的 XML 是由下列各節所述。

> [!NOTE]
> 下列各節中的範例是由 Types.ps1xml 類型檔案，在 Windows PowerShell 安裝目錄 (`$pshome`)。

## <a name="code-methods"></a>程式碼方法

程式碼方法參考.NET Framework 物件的靜態方法。

在下列範例中， **ConvertLargeIntegerToInt64**方法會加入至[System.Xml.Xmlnode 嗎？Displayproperty = Fullname>](/dotnet/api/System.Xml.XmlNode)型別。 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)項目做為程式碼方法定義的擴充的方法。 [名稱](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)項目會指定擴充方法的名稱。 此外， [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference)項目會指定靜態方法。 (您也可以加入[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)的成員的項目[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)項目。)

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>指令碼方法

指令碼方法定義的方法，其值是指令碼的輸出。 在下列範例中， **ConvertToDateTime**方法會加入至[System.Management.Managementobject 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.ManagementObject)型別。 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)項目做為指令碼方法定義的擴充的方法。 [名稱](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)項目會指定擴充方法的名稱。 此外，[指令碼](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script)項目會指定產生的方法值的指令碼。 (您也可以加入[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)的成員的項目[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)項目。)

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
