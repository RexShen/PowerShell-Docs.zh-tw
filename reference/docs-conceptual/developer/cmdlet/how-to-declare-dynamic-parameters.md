---
title: 如何宣告動態參數 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8839aa8841bf94a9b7f8f930ca315fe0ccedb30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784175"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="a12b8-102">如何宣告動態參數</span><span class="sxs-lookup"><span data-stu-id="a12b8-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="a12b8-103">這個範例示範如何定義在執行時間新增至 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="a12b8-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="a12b8-104">在此範例中， `Department` 每當使用者指定切換參數時，都會將參數新增至 Cmdlet `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="a12b8-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="a12b8-105">如需動態參數的詳細資訊，請參閱[Cmdlet 動態參數](./cmdlet-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a12b8-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="a12b8-106">若要定義動態參數</span><span class="sxs-lookup"><span data-stu-id="a12b8-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="a12b8-107">在 Cmdlet 類別宣告中，新增[Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)介面，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a12b8-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="a12b8-108">呼叫[Idynamicparameters. Getdynamicparameters \*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)方法，它會傳回已定義動態參數的物件。</span><span class="sxs-lookup"><span data-stu-id="a12b8-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="a12b8-109">在此範例中，當指定參數時，會呼叫方法 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="a12b8-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

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

3. <span data-ttu-id="a12b8-110">宣告定義要加入之動態參數的類別。</span><span class="sxs-lookup"><span data-stu-id="a12b8-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="a12b8-111">您可以使用您用來宣告靜態 Cmdlet 參數的屬性，以宣告動態參數。</span><span class="sxs-lookup"><span data-stu-id="a12b8-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

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

## <a name="example"></a><span data-ttu-id="a12b8-112">範例</span><span class="sxs-lookup"><span data-stu-id="a12b8-112">Example</span></span>

<span data-ttu-id="a12b8-113">在此範例中， `Department` 每當使用者指定參數時，就會新增參數 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="a12b8-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="a12b8-114">`Department`參數是選擇性參數，而 ValidateSet 屬性則是用來指定允許的引數。</span><span class="sxs-lookup"><span data-stu-id="a12b8-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a12b8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a12b8-115">See Also</span></span>

[<span data-ttu-id="a12b8-116">Runtimedefinedparameterdictionary。</span><span class="sxs-lookup"><span data-stu-id="a12b8-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="a12b8-117">Idynamicparameters. Getdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="a12b8-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="a12b8-118">Cmdlet 動態參數</span><span class="sxs-lookup"><span data-stu-id="a12b8-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="a12b8-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a12b8-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
