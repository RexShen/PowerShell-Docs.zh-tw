---
title: 如何叫用 Cmdlet 中的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: d4564b51b74422cdaec3878b227ffc6be7c97949
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855884"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="eb774-102">如何從 Cmdlet 內叫用 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb774-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="eb774-103">此範例示範如何叫用另一個 cmdlet，可讓您叫用的指令程式的功能新增至您正在開發的 cmdlet 中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eb774-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="eb774-104">在此範例中， `Get-Process` cmdlet 會取得本機電腦執行的處理程序叫用。</span><span class="sxs-lookup"><span data-stu-id="eb774-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="eb774-105">若要呼叫`Get-Process`cmdlet 相當於下列的命令。</span><span class="sxs-lookup"><span data-stu-id="eb774-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="eb774-106">此命令會擷取名稱的字元"a"到"t"開頭的所有處理程序。</span><span class="sxs-lookup"><span data-stu-id="eb774-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="eb774-107">您可以叫用直接衍生自這些指令程式[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別。</span><span class="sxs-lookup"><span data-stu-id="eb774-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="eb774-108">您無法叫用的 cmdlet，衍生自[System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別。</span><span class="sxs-lookup"><span data-stu-id="eb774-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="eb774-109">若要叫用 cmdlet 中的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb774-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="eb774-110">請確認已經參考該組件會定義要叫用 cmdlet 且適當`using`加入陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb774-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="eb774-111">在此範例中，會加入下列命名空間。</span><span class="sxs-lookup"><span data-stu-id="eb774-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="eb774-112">在輸入處理方法的 cmdlet 中，建立要叫用 cmdlet 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="eb774-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="eb774-113">在此範例中，類型的物件[Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand)建立以及包含此指令程式會叫用時所使用的引數的字串。</span><span class="sxs-lookup"><span data-stu-id="eb774-113">In this example, an object of type [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="eb774-114">呼叫[System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法來叫用`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eb774-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="eb774-115">範例</span><span class="sxs-lookup"><span data-stu-id="eb774-115">Example</span></span>

<span data-ttu-id="eb774-116">在此範例中， `Get-Process` cmdlet 會從叫用[System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)指令程式的方法。</span><span class="sxs-lookup"><span data-stu-id="eb774-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

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

## <a name="see-also"></a><span data-ttu-id="eb774-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb774-117">See Also</span></span>

[<span data-ttu-id="eb774-118">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb774-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
