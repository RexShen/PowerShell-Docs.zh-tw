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
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="d4e1a-103">定義物件的預設方法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-103">Defining Default Methods for Objects</span></span>

<span data-ttu-id="d4e1a-104">當您擴充 .NET Framework 物件時，您可以將程式碼方法和腳本方法加入至物件。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-104">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="d4e1a-105">下列各節將說明用來定義這些方法的 XML。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-105">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="d4e1a-106">下列各節中的範例是來自 `Types.ps1xml` Windows PowerShell 安裝目錄中的類型檔案 (`$PSHOME`) 。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-106">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="d4e1a-107">如需詳細資訊，請參閱 [關於 Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-107">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="d4e1a-108">程式碼方法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-108">Code methods</span></span>

<span data-ttu-id="d4e1a-109">程式碼方法會參考 .NET Framework 物件的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-109">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="d4e1a-110">在下列範例中， **ToString** 方法會加入 [System.Xml.Xml節點](/dotnet/api/System.Xml.XmlNode) 類型中。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-110">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="d4e1a-111">[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素會將擴充方法定義為程式碼方法。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-111">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="d4e1a-112">[Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name)元素會指定擴充方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-112">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="d4e1a-113">而且， [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference#System_Management_Automation_PSCodeMethod_CodeReference) 元素會指定靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-113">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="d4e1a-114">您也可以將 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) 元素加入至 [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) 元素的成員。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-114">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="d4e1a-115">腳本方法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-115">Script methods</span></span>

<span data-ttu-id="d4e1a-116">腳本方法會定義一個方法，其值為腳本的輸出。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-116">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="d4e1a-117">在下列範例中， **ConvertToDateTime** 方法會新增至 [system.management.managementobject](/dotnet/api/System.Management.ManagementObject) 類型。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-117">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="d4e1a-118">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod)元素會將擴充方法定義為腳本方法。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-118">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) element defines the extended method as a script method.</span></span> <span data-ttu-id="d4e1a-119">[Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name)元素會指定擴充方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-119">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="d4e1a-120">而且， [script](/dotnet/api/system.management.automation.psscriptmethod.script#System_Management_Automation_PSScriptMethod_Script) 元素會指定產生方法值的腳本。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-120">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="d4e1a-121">您也可以將 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) 元素加入至 [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) 元素的成員。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-121">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d4e1a-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="d4e1a-122">See also</span></span>

[<span data-ttu-id="d4e1a-123">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d4e1a-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
