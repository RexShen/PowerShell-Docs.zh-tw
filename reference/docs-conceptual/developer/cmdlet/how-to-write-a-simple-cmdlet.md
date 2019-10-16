---
title: 如何撰寫簡單的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365467"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="945fa-102">如何撰寫 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="945fa-102">How to write a cmdlet</span></span>

<span data-ttu-id="945fa-103">本文說明如何撰寫 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="945fa-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="945fa-104">@No__t-0 Cmdlet 會使用單一使用者名稱做為輸入，然後將問候語寫入該使用者。</span><span class="sxs-lookup"><span data-stu-id="945fa-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="945fa-105">雖然此 Cmdlet 不會執行太多工作，但此範例會示範 Cmdlet 的主要區段。</span><span class="sxs-lookup"><span data-stu-id="945fa-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="945fa-106">撰寫 Cmdlet 的步驟</span><span class="sxs-lookup"><span data-stu-id="945fa-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="945fa-107">若要將類別宣告為 Cmdlet，請使用**Cmdlet**屬性。</span><span class="sxs-lookup"><span data-stu-id="945fa-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="945fa-108">**Cmdlet**屬性會指定 Cmdlet 名稱的動詞和名詞。</span><span class="sxs-lookup"><span data-stu-id="945fa-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="945fa-109">如需**Cmdlet**屬性的詳細資訊，請參閱[CmdletAttribute](cmdlet-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="945fa-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="945fa-110">指定類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="945fa-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="945fa-111">指定 Cmdlet 衍生自下列其中一個類別：</span><span class="sxs-lookup"><span data-stu-id="945fa-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * <span data-ttu-id="945fa-112">[[系統管理]。 Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="945fa-112">[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)</span></span>
   * [<span data-ttu-id="945fa-113">PSCmdlet。</span><span class="sxs-lookup"><span data-stu-id="945fa-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="945fa-114">若要定義 Cmdlet 的參數，請使用**參數**屬性。</span><span class="sxs-lookup"><span data-stu-id="945fa-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="945fa-115">在此情況下，只會指定一個必要的參數。</span><span class="sxs-lookup"><span data-stu-id="945fa-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="945fa-116">如需**參數**屬性的詳細資訊，請參閱[ParameterAttribute](parameter-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="945fa-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="945fa-117">覆寫處理輸入的輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="945fa-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="945fa-118">在此情況下，會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="945fa-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="945fa-119">若要寫入問候語，請使用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="945fa-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="945fa-120">此問候語會以下列格式顯示：</span><span class="sxs-lookup"><span data-stu-id="945fa-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="945fa-121">範例</span><span class="sxs-lookup"><span data-stu-id="945fa-121">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="945fa-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="945fa-122">See also</span></span>

<span data-ttu-id="945fa-123">[[系統管理]。 Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="945fa-123">[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)</span></span>

[<span data-ttu-id="945fa-124">PSCmdlet。</span><span class="sxs-lookup"><span data-stu-id="945fa-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="945fa-125">ProcessRecord 的管理元件</span><span class="sxs-lookup"><span data-stu-id="945fa-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="945fa-126">WriteObject 的管理元件</span><span class="sxs-lookup"><span data-stu-id="945fa-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="945fa-127">CmdletAttribute 宣告</span><span class="sxs-lookup"><span data-stu-id="945fa-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="945fa-128">ParameterAttribute 宣告</span><span class="sxs-lookup"><span data-stu-id="945fa-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="945fa-129">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="945fa-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)