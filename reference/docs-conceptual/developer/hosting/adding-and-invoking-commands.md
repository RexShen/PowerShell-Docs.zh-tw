---
title: 加入和叫用命令 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367637"
---
# <a name="adding-and-invoking-commands"></a>新增及叫用命令

建立執行時間之後，您可以將 Windows PowerShellcommands 和腳本新增至管線，然後以同步或非同步方式叫用管線。

## <a name="creating-a-pipeline"></a>建立管線

 [System.web](/dotnet/api/system.management.automation.powershell)類別提供數種方法，可將命令、參數和腳本新增至管線。 您可以呼叫[Begininvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) [的多](/dotnet/api/System.Management.Automation.PowerShell.Invoke)載，或是以非同步方式叫用管線，方法是呼叫[Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法的多載，或以非同步方式叫用該管線。」（可能為系統管理）。

### <a name="addcommand"></a>AddCommand

1. 建立一個[system.web](/dotnet/api/system.management.automation.powershell)物件。

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. 新增您想要執行的命令。

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. 叫用命令。

   ```csharp
   ps.Invoke();
   ```

 如果您在呼叫 system.servicemodel [*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法之前多次呼叫[Addcommand *](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法，第一個命令的結果會以管道傳送至第二個，依此類推，而是以管線傳送的。 如果您不想要使用管線將上一個命令的結果傳送至命令，請改為呼叫[Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)來新增它。

### <a name="addparameter"></a>AddParameter

 上一個範例會執行不含任何參數的單一命令。 例如，您可以使用[Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法將參數新增至命令，下列程式碼會取得在電腦上執行之所有名為 `PowerShell` 的處理常式清單。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 您可以藉由重複呼叫[Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)來新增其他參數。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 您也可以藉由呼叫[Addparameters *](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法，加入參數名稱和值的字典。

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 您可以使用[Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法來模擬批次處理，這會將額外的語句新增至管線的結尾，下列程式碼會取得名稱為 `PowerShell`的執行中進程清單，然後取得正在執行的服務清單。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 您可以藉由呼叫[Addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法，來執行現有的腳本。 下列範例會將腳本新增至管線並加以執行。 這個範例假設名為 `D:\PSScripts`的資料夾中已經有名為 `MyScript.ps1` 的腳本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 另外還有一個[Addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法的版本，它會採用名為 `useLocalScope`的布林參數。 如果此參數設定為 `true`，則腳本會在本機範圍中執行。 下列程式碼會在本機範圍中執行腳本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>同步叫用管線

 將元素新增至管線之後，您就可以叫用它。 若要同步叫用管線，您可以呼叫[system.object](/dotnet/api/System.Management.Automation.PowerShell.Invoke)的多載。 下列範例顯示如何同步叫用管線。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>非同步叫用管線

 您可以藉由呼叫[Begininvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)的多載來非同步叫用管線，以建立[IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx)物件，然後再呼叫[Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法來進行此工作。

 下列範例顯示如何以非同步方式叫用管線。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>另請參閱

 [建立 InitialSessionState](./creating-an-initialsessionstate.md)

 [建立受條件約束的運行空間](./creating-a-constrained-runspace.md)
