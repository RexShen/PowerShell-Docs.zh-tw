---
title: 如何撰寫一個簡單的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067734"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="377f4-102">如何撰寫 cmdlet</span><span class="sxs-lookup"><span data-stu-id="377f4-102">How to write a cmdlet</span></span>

<span data-ttu-id="377f4-103">這篇文章會示範如何撰寫的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="377f4-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="377f4-104">`Send-Greeting` Cmdlet 會取得單一使用者名稱作為輸入，並接著將祝賀詞寫入該使用者。</span><span class="sxs-lookup"><span data-stu-id="377f4-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="377f4-105">此 cmdlet 不會執行的工作，雖然此範例會示範指令程式的主要區段。</span><span class="sxs-lookup"><span data-stu-id="377f4-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="377f4-106">若要撰寫的 cmdlet 的步驟</span><span class="sxs-lookup"><span data-stu-id="377f4-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="377f4-107">若要將類別宣告為 cmdlet，使用**Cmdlet**屬性。</span><span class="sxs-lookup"><span data-stu-id="377f4-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="377f4-108">**Cmdlet**屬性會指定動詞與名詞的 cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="377f4-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="377f4-109">如需詳細資訊**Cmdlet**屬性，請參閱[CmdletAttribute 宣告](cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="377f4-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="377f4-110">指定類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="377f4-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="377f4-111">指定此 cmdlet 會衍生自下列類別之一：</span><span class="sxs-lookup"><span data-stu-id="377f4-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="377f4-112">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="377f4-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="377f4-113">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="377f4-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="377f4-114">若要定義此 cmdlet 的參數，請使用**參數**屬性。</span><span class="sxs-lookup"><span data-stu-id="377f4-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="377f4-115">在此情況下，只有一個必須指定參數。</span><span class="sxs-lookup"><span data-stu-id="377f4-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="377f4-116">如需詳細資訊**參數**屬性，請參閱[ParameterAttribute 宣告](parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="377f4-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="377f4-117">覆寫的輸入處理方法，以處理輸入。</span><span class="sxs-lookup"><span data-stu-id="377f4-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="377f4-118">在此情況下， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)會覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="377f4-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="377f4-119">撰寫問候，使用的方法[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)。</span><span class="sxs-lookup"><span data-stu-id="377f4-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="377f4-120">問候語會顯示以下列格式：</span><span class="sxs-lookup"><span data-stu-id="377f4-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="377f4-121">範例</span><span class="sxs-lookup"><span data-stu-id="377f4-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="377f4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="377f4-122">See also</span></span>

[<span data-ttu-id="377f4-123">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="377f4-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="377f4-124">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="377f4-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="377f4-125">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="377f4-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="377f4-126">System.Management.Automation.Cmdlet.WriteObject</span><span class="sxs-lookup"><span data-stu-id="377f4-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="377f4-127">CmdletAttribute Declaration</span><span class="sxs-lookup"><span data-stu-id="377f4-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="377f4-128">ParameterAttribute 宣告</span><span class="sxs-lookup"><span data-stu-id="377f4-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="377f4-129">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="377f4-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)