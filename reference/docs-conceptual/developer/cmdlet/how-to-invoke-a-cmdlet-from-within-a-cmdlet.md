---
title: 如何從 Cmdlet 內叫用 Cmdlet |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2d5b0788d3310d0dd7b311f86c497afe8eec9d11
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784141"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>如何從 Cmdlet 內叫用 Cmdlet

這個範例示範如何從另一個 Cmdlet 叫用 Cmdlet，這可讓您將叫用 Cmdlet 的功能新增至您正在開發的 Cmdlet 中。 在此範例中， `Get-Process` 會叫用 Cmdlet 來取得在本機電腦上執行的處理常式。 對 Cmdlet 的呼叫 `Get-Process` 相當於下列命令。 此命令會抓取名稱開頭為 "a" 到 "t" 字元的所有進程。

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> 您只能叫用直接衍生自[system.object](/dotnet/api/System.Management.Automation.Cmdlet)類別的 Cmdlet。 您不能叫用衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別的 Cmdlet。

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>從 Cmdlet 內叫用 Cmdlet

1. 請確定已參考定義要叫用之 Cmdlet 的元件，並已新增適當的 `using` 語句。 在此範例中，會加入下列命名空間。

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. 在 Cmdlet 的輸入處理方法中，建立要叫用之 Cmdlet 的新實例。 在此範例中，會建立[Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand)類型的物件，以及包含叫用 Cmdlet 時所使用之引數的字串。

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. 呼叫[system.web *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法，以叫用 `Get-Process` Cmdlet。

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>範例

在此範例中， `Get-Process` 會從 Cmdlet 的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中叫用 Cmdlet。

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
