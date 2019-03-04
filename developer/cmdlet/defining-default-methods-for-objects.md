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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861404"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="ade76-102">定義物件的預設方法</span><span class="sxs-lookup"><span data-stu-id="ade76-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="ade76-103">當您擴充.NET Framework 物件時，您可以將程式碼方法和指令碼方法新增至物件。</span><span class="sxs-lookup"><span data-stu-id="ade76-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="ade76-104">用來定義這些方法的 XML 是由下列各節所述。</span><span class="sxs-lookup"><span data-stu-id="ade76-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="ade76-105">下列各節中的範例是由 Types.ps1xml 類型檔案，在 Windows PowerShell 安裝目錄 (`$pshome`)。</span><span class="sxs-lookup"><span data-stu-id="ade76-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="ade76-106">程式碼方法</span><span class="sxs-lookup"><span data-stu-id="ade76-106">Code Methods</span></span>

<span data-ttu-id="ade76-107">程式碼方法參考.NET Framework 物件的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="ade76-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="ade76-108">在下列範例中， **ConvertLargeIntegerToInt64**方法會加入至[System.Xml.Xmlnode 嗎？Displayproperty = Fullname>](/dotnet/api/System.Xml.XmlNode)型別。</span><span class="sxs-lookup"><span data-stu-id="ade76-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="ade76-109">[CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05)項目做為程式碼方法定義的擴充的方法。</span><span class="sxs-lookup"><span data-stu-id="ade76-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="ade76-110">[名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定擴充方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="ade76-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="ade76-111">此外， [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b)項目會指定靜態方法。</span><span class="sxs-lookup"><span data-stu-id="ade76-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="ade76-112">(您也可以加入[CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05)的成員的項目[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)</span><span class="sxs-lookup"><span data-stu-id="ade76-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="ade76-113">指令碼方法</span><span class="sxs-lookup"><span data-stu-id="ade76-113">Script Methods</span></span>

<span data-ttu-id="ade76-114">指令碼方法定義的方法，其值是指令碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="ade76-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="ade76-115">在下列範例中， **ConvertToDateTime**方法會加入至[System.Management.Managementobject 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.ManagementObject)型別。</span><span class="sxs-lookup"><span data-stu-id="ade76-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="ade76-116">[ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c)項目做為指令碼方法定義的擴充的方法。</span><span class="sxs-lookup"><span data-stu-id="ade76-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="ade76-117">[名稱](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)項目會指定擴充方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="ade76-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="ade76-118">此外，[指令碼](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f)項目會指定產生的方法值的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ade76-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="ade76-119">(您也可以加入[ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c)的成員的項目[成員組](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)項目。)</span><span class="sxs-lookup"><span data-stu-id="ade76-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ade76-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade76-120">See Also</span></span>

[<span data-ttu-id="ade76-121">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ade76-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)