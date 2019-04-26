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
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067819"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>如何從 Cmdlet 內叫用 Cmdlet

此範例示範如何叫用另一個 cmdlet，可讓您叫用的指令程式的功能新增至您正在開發的 cmdlet 中的 cmdlet。 在此範例中， `Get-Process` cmdlet 會取得本機電腦執行的處理程序叫用。 若要呼叫`Get-Process`cmdlet 相當於下列的命令。 此命令會擷取名稱的字元"a"到"t"開頭的所有處理程序。

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> 您可以叫用直接衍生自這些指令程式[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別。 您無法叫用的 cmdlet，衍生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別。

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>若要叫用 cmdlet 中的 cmdlet

1. 請確認已經參考該組件會定義要叫用 cmdlet 且適當`using`加入陳述式。 在此範例中，會加入下列命名空間。

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. 在輸入處理方法的 cmdlet 中，建立要叫用 cmdlet 的新執行個體。 在此範例中，類型的物件[Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand)建立以及包含此指令程式會叫用時所使用的引數的字串。

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. 呼叫[System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法來叫用`Get-Process`cmdlet。

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>範例

在此範例中， `Get-Process` cmdlet 會從叫用[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)指令程式的方法。

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

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
