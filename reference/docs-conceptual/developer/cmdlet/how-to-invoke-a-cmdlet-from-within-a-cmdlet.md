---
title: 如何從 Cmdlet 內叫用 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365547"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="a0458-102">如何從 Cmdlet 內叫用 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a0458-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="a0458-103">這個範例示範如何從另一個 Cmdlet 叫用 Cmdlet，這可讓您將叫用 Cmdlet 的功能新增至您正在開發的 Cmdlet 中。</span><span class="sxs-lookup"><span data-stu-id="a0458-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="a0458-104">在此範例中，會叫用 `Get-Process` Cmdlet 來取得在本機電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="a0458-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="a0458-105">呼叫 `Get-Process` Cmdlet 相當於下列命令。</span><span class="sxs-lookup"><span data-stu-id="a0458-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="a0458-106">此命令會抓取名稱開頭為 "a" 到 "t" 字元的所有進程。</span><span class="sxs-lookup"><span data-stu-id="a0458-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="a0458-107">您只能叫用直接衍生自[system.object](/dotnet/api/System.Management.Automation.Cmdlet)類別的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0458-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="a0458-108">您不能叫用衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0458-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="a0458-109">從 Cmdlet 內叫用 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a0458-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="a0458-110">請確定已參考定義要叫用之 Cmdlet 的元件，並已新增適當的 `using` 語句。</span><span class="sxs-lookup"><span data-stu-id="a0458-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="a0458-111">在此範例中，會加入下列命名空間。</span><span class="sxs-lookup"><span data-stu-id="a0458-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="a0458-112">在 Cmdlet 的輸入處理方法中，建立要叫用之 Cmdlet 的新實例。</span><span class="sxs-lookup"><span data-stu-id="a0458-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="a0458-113">在此範例中，會建立[Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand)類型的物件，以及包含叫用 Cmdlet 時所使用之引數的字串。</span><span class="sxs-lookup"><span data-stu-id="a0458-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="a0458-114">呼叫[system.web \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法，以叫用 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0458-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="a0458-115">範例</span><span class="sxs-lookup"><span data-stu-id="a0458-115">Example</span></span>

<span data-ttu-id="a0458-116">在此範例中，會從 Cmdlet 的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中叫用 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0458-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a0458-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0458-117">See Also</span></span>

[<span data-ttu-id="a0458-118">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a0458-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
