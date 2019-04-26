---
title: 新增和叫用命令 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083020"
---
# <a name="adding-and-invoking-commands"></a>新增及叫用命令

建立 runspace 之後, 您可以將 Windows PowerShellcommands 和指令碼新增至管線中，並接著在同步或非同步方式叫用管線。

## <a name="creating-a-pipeline"></a>建立管線

 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)類別提供數種方法來將命令、 參數和指令碼新增至管線。 您可以叫用管線以同步方式呼叫的多載[System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法，或以非同步方式呼叫的多載[System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) ，然後[System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。

### <a name="addcommand"></a>AddCommand

1. 建立[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。

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

 如果您呼叫[System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法超過一次，然後再呼叫[System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法、 結果第一個命令會輸送到第二個，依此類推。 如果您不想透過管道傳送命令前一個命令的結果，會將它加入藉由呼叫[System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)改。

### <a name="addparameter"></a>AddParameter

 前一個範例會執行不含任何參數的單一命令。 可以透過將參數新增至命令[System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法，例如下列程式碼會取得一份所有程序會在名為`PowerShell`上執行機器。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 您可以新增額外的參數，藉由呼叫[System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)重複。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 您也可以藉由呼叫來新增參數名稱和值的字典[System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法。

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 您可以使用批次處理來模擬[System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法，將其他的陳述式加入至管線，下列程式碼會取得執行程序名稱的清單結尾`PowerShell`，然後取得執行中服務的清單。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 您可以執行現有的指令碼，藉由呼叫[System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法。 下列範例會將指令碼新增至管線，並執行它。 這個範例假設已經有名稱為指令碼`MyScript.ps1`在名為的資料夾中`D:\PSScripts`。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 另外還有一份[System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法接受名為的布林參數`useLocalScope`。 如果此參數設為`true`，則指令碼會執行本機範圍內。 下列程式碼會在本機的範圍內執行指令碼。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>以同步方式叫用管線

 您將項目新增至管線之後，您叫用它。 若要以同步方式叫用管線時，您會呼叫的多載[System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法。 下列範例示範如何以同步方式叫用管線。

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

### <a name="invoking-a-pipeline-asynchronously"></a>以非同步方式叫用管線

 您叫用管線以非同步方式呼叫的多載[System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)來建立[IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx)物件，並接著呼叫[System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。

 下列範例會示範如何以非同步方式叫用管線。

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

 [建立受限的 runspace](./creating-a-constrained-runspace.md)
