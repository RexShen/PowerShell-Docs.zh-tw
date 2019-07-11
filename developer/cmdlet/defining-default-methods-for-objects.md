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
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="d2f4d-102">定義物件的預設方法</span><span class="sxs-lookup"><span data-stu-id="d2f4d-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="d2f4d-103">當您擴充.NET Framework 物件時，您可以將程式碼方法和指令碼方法新增至物件。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="d2f4d-104">用來定義這些方法的 XML 是由下列各節所述。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="d2f4d-105">下列各節中的範例是由 Types.ps1xml 類型檔案，在 Windows PowerShell 安裝目錄 (`$pshome`)。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="d2f4d-106">程式碼方法</span><span class="sxs-lookup"><span data-stu-id="d2f4d-106">Code Methods</span></span>

<span data-ttu-id="d2f4d-107">程式碼方法參考.NET Framework 物件的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="d2f4d-108">在下列範例中， **ConvertLargeIntegerToInt64**方法會加入至[System.Xml.Xmlnode 嗎？Displayproperty = Fullname>](/dotnet/api/System.Xml.XmlNode)型別。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="d2f4d-109">[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)項目做為程式碼方法定義的擴充的方法。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="d2f4d-110">[名稱](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)項目會指定擴充方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="d2f4d-111">此外， [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference)項目會指定靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="d2f4d-112">(您也可以加入[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)的成員的項目[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)項目。)</span><span class="sxs-lookup"><span data-stu-id="d2f4d-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="d2f4d-113">指令碼方法</span><span class="sxs-lookup"><span data-stu-id="d2f4d-113">Script Methods</span></span>

<span data-ttu-id="d2f4d-114">指令碼方法定義的方法，其值是指令碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="d2f4d-115">在下列範例中， **ConvertToDateTime**方法會加入至[System.Management.Managementobject 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.ManagementObject)型別。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="d2f4d-116">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)項目做為指令碼方法定義的擴充的方法。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="d2f4d-117">[名稱](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)項目會指定擴充方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="d2f4d-118">此外，[指令碼](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script)項目會指定產生的方法值的指令碼。</span><span class="sxs-lookup"><span data-stu-id="d2f4d-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="d2f4d-119">(您也可以加入[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)的成員的項目[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)項目。)</span><span class="sxs-lookup"><span data-stu-id="d2f4d-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d2f4d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2f4d-120">See Also</span></span>

[<span data-ttu-id="d2f4d-121">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d2f4d-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
