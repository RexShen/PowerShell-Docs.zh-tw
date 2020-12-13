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
# <a name="how-to-declare-dynamic-parameters"></a>如何宣告動態參數

此範例示範如何定義在執行時間新增至 Cmdlet 的動態參數。 在此範例中， `Department` 每當使用者指定切換參數時，就會將參數新增至 Cmdlet `Employee` 。 如需動態參數的詳細資訊，請參閱 [Cmdlet 動態參數](./cmdlet-dynamic-parameters.md)。

## <a name="to-define-dynamic-parameters"></a>若要定義動態參數

1. 在 Cmdlet 類別宣告中，加入 [Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) 介面，如下所示。

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. 呼叫 [Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) 方法，這個方法會傳回定義動態參數的物件。 在此範例中，當指定參數時，會呼叫方法 `Employee` 。

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

3. 宣告定義要加入之動態參數的類別。 您可以使用您用來宣告靜態 Cmdlet 參數的屬性來宣告動態參數。

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

## <a name="example"></a>範例

在此範例中， `Department` 每當使用者指定參數時，就會加入參數 `Employee` 。 `Department`參數是選擇性參數，而 ValidateSet 屬性是用來指定允許的引數。

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

## <a name="see-also"></a>另請參閱

[Runtimedefinedparameterdictionary。](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Cmdlet 動態參數](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
