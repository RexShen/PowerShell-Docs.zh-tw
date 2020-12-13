---
ms.date: 09/13/2016
ms.topic: reference
title: 如何宣告動態參數
description: 如何宣告動態參數
ms.openlocfilehash: 0f5a8f249b414663aa9702a908ea5c8ca24755ff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667074"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="82e53-103">如何宣告動態參數</span><span class="sxs-lookup"><span data-stu-id="82e53-103">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="82e53-104">此範例示範如何定義在執行時間新增至 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="82e53-104">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="82e53-105">在此範例中， `Department` 每當使用者指定切換參數時，就會將參數新增至 Cmdlet `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="82e53-105">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="82e53-106">如需動態參數的詳細資訊，請參閱 [Cmdlet 動態參數](./cmdlet-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="82e53-106">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="82e53-107">若要定義動態參數</span><span class="sxs-lookup"><span data-stu-id="82e53-107">To define dynamic parameters</span></span>

1. <span data-ttu-id="82e53-108">在 Cmdlet 類別宣告中，加入 [Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) 介面，如下所示。</span><span class="sxs-lookup"><span data-stu-id="82e53-108">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="82e53-109">呼叫 [Idynamicparameters. Getdynamicparameters \*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) 方法，這個方法會傳回定義動態參數的物件。</span><span class="sxs-lookup"><span data-stu-id="82e53-109">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="82e53-110">在此範例中，當指定參數時，會呼叫方法 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="82e53-110">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="82e53-111">宣告定義要加入之動態參數的類別。</span><span class="sxs-lookup"><span data-stu-id="82e53-111">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="82e53-112">您可以使用您用來宣告靜態 Cmdlet 參數的屬性來宣告動態參數。</span><span class="sxs-lookup"><span data-stu-id="82e53-112">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="82e53-113">範例</span><span class="sxs-lookup"><span data-stu-id="82e53-113">Example</span></span>

<span data-ttu-id="82e53-114">在此範例中， `Department` 每當使用者指定參數時，就會加入參數 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="82e53-114">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="82e53-115">`Department`參數是選擇性參數，而 ValidateSet 屬性是用來指定允許的引數。</span><span class="sxs-lookup"><span data-stu-id="82e53-115">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="82e53-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82e53-116">See Also</span></span>

[<span data-ttu-id="82e53-117">Runtimedefinedparameterdictionary。</span><span class="sxs-lookup"><span data-stu-id="82e53-117">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="82e53-118">Idynamicparameters. Getdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="82e53-118">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="82e53-119">Cmdlet 動態參數</span><span class="sxs-lookup"><span data-stu-id="82e53-119">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="82e53-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="82e53-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
