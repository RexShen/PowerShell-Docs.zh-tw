---
title: 如何將動態參數宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067910"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="dd924-102">如何宣告動態參數</span><span class="sxs-lookup"><span data-stu-id="dd924-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="dd924-103">此範例示範如何定義會新增至 cmdlet，在執行階段的動態參數。</span><span class="sxs-lookup"><span data-stu-id="dd924-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="dd924-104">在此範例中，`Department`參數加入 cmdlet，每當使用者指定`Employee`切換參數。</span><span class="sxs-lookup"><span data-stu-id="dd924-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="dd924-105">如需有關動態參數的詳細資訊，請參閱[Cmdlet 的動態參數](./cmdlet-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="dd924-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="dd924-106">若要定義的動態參數</span><span class="sxs-lookup"><span data-stu-id="dd924-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="dd924-107">在 cmdlet 類別宣告中，新增[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)介面所示。</span><span class="sxs-lookup"><span data-stu-id="dd924-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="dd924-108">呼叫[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)方法，以傳回已定義的動態參數的物件。</span><span class="sxs-lookup"><span data-stu-id="dd924-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="dd924-109">在此範例中，此方法時，會呼叫`Employee`指定參數。</span><span class="sxs-lookup"><span data-stu-id="dd924-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

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

3. <span data-ttu-id="dd924-110">宣告一個類別來定義要新增的動態參數。</span><span class="sxs-lookup"><span data-stu-id="dd924-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="dd924-111">您可以使用您用來宣告靜態的 cmdlet 參數宣告的動態參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="dd924-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

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

## <a name="example"></a><span data-ttu-id="dd924-112">範例</span><span class="sxs-lookup"><span data-stu-id="dd924-112">Example</span></span>

<span data-ttu-id="dd924-113">在此範例中，`Department`參數會加入使用者指定每當`Employee`參數。</span><span class="sxs-lookup"><span data-stu-id="dd924-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="dd924-114">`Department`參數是選擇性參數，和 ValidateSet 屬性用來指定允許的引數。</span><span class="sxs-lookup"><span data-stu-id="dd924-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dd924-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd924-115">See Also</span></span>

[<span data-ttu-id="dd924-116">System.Management.Automation.Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="dd924-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="dd924-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="dd924-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="dd924-118">Cmdlet 的動態參數</span><span class="sxs-lookup"><span data-stu-id="dd924-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="dd924-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dd924-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)