---
ms.date: 09/13/2016
ms.topic: reference
title: 定義物件的預設方法
description: 定義物件的預設方法
ms.openlocfilehash: c65ca91a7038f32d8c3ef62cfe7881e5ad4dba5a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355522"
---
# <a name="defining-default-methods-for-objects"></a>定義物件的預設方法

當您擴充 .NET Framework 物件時，您可以將程式碼方法和腳本方法加入至物件。
下列各節將說明用來定義這些方法的 XML。

> [!NOTE]
> 下列各節中的範例是來自 `Types.ps1xml` Windows PowerShell 安裝目錄中的類型檔案 (`$PSHOME`) 。 如需詳細資訊，請參閱 [關於 Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)。

## <a name="code-methods"></a>程式碼方法

程式碼方法會參考 .NET Framework 物件的靜態方法。

在下列範例中， **ToString** 方法會加入 [System.Xml.Xml節點](/dotnet/api/System.Xml.XmlNode) 類型中。 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素會將擴充方法定義為程式碼方法。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name)元素會指定擴充方法的名稱。 而且， [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference#System_Management_Automation_PSCodeMethod_CodeReference) 元素會指定靜態方法。 您也可以將 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) 元素加入至 [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) 元素的成員。

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

腳本方法會定義一個方法，其值為腳本的輸出。 在下列範例中， **ConvertToDateTime** 方法會新增至 [system.management.managementobject](/dotnet/api/System.Management.ManagementObject) 類型。 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod)元素會將擴充方法定義為腳本方法。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name)元素會指定擴充方法的名稱。 而且， [script](/dotnet/api/system.management.automation.psscriptmethod.script#System_Management_Automation_PSScriptMethod_Script) 元素會指定產生方法值的腳本。 您也可以將 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) 元素加入至 [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) 元素的成員。

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

## <a name="see-also"></a>請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
