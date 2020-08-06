---
title: 定義物件的預設方法 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 10917de9e897fc1eed362430d63ff5b9cb7e813d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774587"
---
# <a name="defining-default-methods-for-objects"></a>定義物件的預設方法

當您擴充 .NET Framework 物件時，您可以將程式碼方法和腳本方法加入至物件。
下列各節將說明用來定義這些方法的 XML。

> [!NOTE]
> 下列各節中的範例來自 `Types.ps1xml` Windows PowerShell 安裝目錄中的類型檔案 (`$PSHOME`) 。 如需詳細資訊，請參閱[關於 Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)。

## <a name="code-methods"></a>程式碼方法

程式碼方法會參考 .NET Framework 物件的靜態方法。

在下列範例中， **ToString**方法會加入至[System.Xml.Xml節點](/dotnet/api/System.Xml.XmlNode)類型。 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素會將擴充的方法定義為程式碼方法。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素會指定擴充方法的名稱。 而且， [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference)元素會指定靜態方法。 您也可以將[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素新增至[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素的成員。

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>腳本方法

腳本方法會定義一個方法，其值為腳本的輸出。 在下列範例中， **ConvertToDateTime**方法會新增至[system.management.managementobject](/dotnet/api/System.Management.ManagementObject)類型。 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素會將擴充的方法定義為腳本方法。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素會指定擴充方法的名稱。 而且， [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script)元素會指定產生方法值的腳本。 您也可以將[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素新增至[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素的成員。

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
