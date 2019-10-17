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
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365687"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="46837-102">定義物件的預設方法</span><span class="sxs-lookup"><span data-stu-id="46837-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="46837-103">當您擴充 .NET Framework 物件時，您可以將程式碼方法和腳本方法加入至物件。</span><span class="sxs-lookup"><span data-stu-id="46837-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="46837-104">下列各節將說明用來定義這些方法的 XML。</span><span class="sxs-lookup"><span data-stu-id="46837-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="46837-105">下列各節中的範例來自 Windows PowerShell 安裝目錄中的 `Types.ps1xml` 類型檔案（`$PSHOME`）。</span><span class="sxs-lookup"><span data-stu-id="46837-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="46837-106">如需詳細資訊，請參閱[關於類型. types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="46837-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="46837-107">程式碼方法</span><span class="sxs-lookup"><span data-stu-id="46837-107">Code methods</span></span>

<span data-ttu-id="46837-108">程式碼方法會參考 .NET Framework 物件的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="46837-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="46837-109">在下列範例中， **ToString**方法會加入至[system.object](/dotnet/api/System.Xml.XmlNode)類型。</span><span class="sxs-lookup"><span data-stu-id="46837-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="46837-110">[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素會將擴充的方法定義為程式碼方法。</span><span class="sxs-lookup"><span data-stu-id="46837-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="46837-111">[Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素會指定擴充方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="46837-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="46837-112">而且， [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference)元素會指定靜態方法。</span><span class="sxs-lookup"><span data-stu-id="46837-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="46837-113">您也可以將[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素新增至[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素的成員。</span><span class="sxs-lookup"><span data-stu-id="46837-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="46837-114">腳本方法</span><span class="sxs-lookup"><span data-stu-id="46837-114">Script methods</span></span>

<span data-ttu-id="46837-115">腳本方法會定義一個方法，其值為腳本的輸出。</span><span class="sxs-lookup"><span data-stu-id="46837-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="46837-116">在下列範例中， **ConvertToDateTime**方法會新增至[system.management.managementobject](/dotnet/api/System.Management.ManagementObject)類型。</span><span class="sxs-lookup"><span data-stu-id="46837-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="46837-117">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素會將擴充的方法定義為腳本方法。</span><span class="sxs-lookup"><span data-stu-id="46837-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="46837-118">[Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素會指定擴充方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="46837-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="46837-119">而且， [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script)元素會指定產生方法值的腳本。</span><span class="sxs-lookup"><span data-stu-id="46837-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="46837-120">您也可以將[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素新增至[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素的成員。</span><span class="sxs-lookup"><span data-stu-id="46837-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="46837-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46837-121">See also</span></span>

[<span data-ttu-id="46837-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="46837-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)