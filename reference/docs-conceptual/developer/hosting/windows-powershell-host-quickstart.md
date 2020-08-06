---
title: Windows PowerShell 主機快速入門 |Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: fea6bd5ae49ecf552c583271ee9d869b1ccebae8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779398"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell 主機快速入門

若要在您的應用程式中裝載 Windows PowerShell，請使用[system.web](/dotnet/api/System.Management.Automation.PowerShell)類別。
這個類別會提供方法來建立命令的管線，然後在運行空間中執行這些命令。
建立主應用程式的最簡單方式是使用預設的運行時。
預設的執行時間包含所有核心 Windows PowerShell 命令。
如果您想要讓應用程式只公開部分的 Windows PowerShell 命令，您必須建立自訂的執行時間。

## <a name="using-the-default-runspace"></a>使用預設的運行空間

首先，我們將使用預設的執行時間，並使用[system.web](/dotnet/api/System.Management.Automation.PowerShell)類別的方法，將命令、參數、語句和腳本新增至管線。

### <a name="addcommand"></a>AddCommand

您可以使用[AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法，將命令新增至管線。
例如，假設您想要取得電腦上正在執行的進程清單。
執行此命令的方式如下所示。

1. 建立一個[system.web](/dotnet/api/System.Management.Automation.PowerShell)物件。

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

如果您在呼叫[AddCommand 方法之前](/dotnet/api/System.Management.Automation.PowerShell.Invoke)多次呼叫，則第一個命令的結果會以管道傳送至第二個命令，依此類推。
如果您不想要使用管線將上一個命令的結果傳送至命令，請改為呼叫[AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)來加入它。

### <a name="addparameter"></a>AddParameter

上一個範例會執行不含任何參數的單一命令。
您可以使用[PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法，將參數新增至命令。
例如，下列程式碼會取得在電腦上執行且名為的所有處理常式清單 `PowerShell` 。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

您可以重複呼叫 AddParameter 方法，以新增其他參數。

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

您也可以藉由呼叫[AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法，加入參數名稱和值的字典。

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

您可以使用[AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法來模擬批次處理，這會將額外的語句新增至管線的結尾。
下列程式碼會取得名稱為的執行中進程清單 `PowerShell` ，然後取得正在執行的服務清單。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

您可以藉由呼叫[AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法來執行現有的腳本。
下列範例會將腳本新增至管線並加以執行。
這個範例假設在名為的資料夾中已經有名為的腳本 `MyScript.ps1` `D:\PSScripts` 。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

另外還有一個版本的 AddScript 方法，它會採用名為的布林參數 `useLocalScope` 。
如果此參數設定為 `true` ，則腳本會在本機範圍中執行。
下列程式碼會在本機範圍中執行腳本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>建立自訂運行空間

雖然先前範例中使用的預設執行時間會載入所有核心 Windows PowerShell 命令，但是您可以建立自訂的執行時間，只載入所有命令的指定子集。
您可能想要這麼做，以改善效能 (載入較大量的命令是) 的效能，或限制使用者執行作業的能力。
只公開有限數目的命令的運行空間稱為受限制的運行空間。
若要建立受條件約束的執行空間，您可以使用 tialSessionState 類別和[System.Management.Automation.Runspaces.Ini](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)的執行[空間](/dotnet/api/System.Management.Automation.Runspaces.Runspace)。

### <a name="creating-an-initialsessionstate-object"></a>建立 InitialSessionState 物件

若要建立自訂的運行時，您必須先建立[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。
在下列範例中，我們會使用[RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) ，在建立預設 InitialSessionState 物件後建立運行空間。

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>限制運行空間

在上述範例中，我們建立了預設的[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，它會載入所有內建的核心 Windows PowerShell。
我們也可以呼叫[System.Management.Automation.Runspaces.InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法來建立 InitialSessionState 物件，它只會載入中的命令。
若要建立更受限制的運行時，您必須藉由呼叫[System.Management.Automation.Runspaces.InitialSessionState. create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法來建立空的 InitialSessionState 物件，然後將命令新增至 InitialSessionState。

使用只載入您指定之命令的運行空間，可以大幅提升效能。

您可以使用[SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)類別的方法，來定義初始會話狀態的 Cmdlet。
下列範例會建立空的初始會話狀態，然後定義和命令，並將其新增 `Get-Command` `Import-Module` 至初始會話狀態。
接著，我們會建立該初始會話狀態所限制的運行時，並執行該運行空間中的命令。

建立初始會話狀態。

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

定義並將命令新增至初始會話狀態。

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

建立並開啟該運行空間。

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

執行命令並顯示結果。

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

執行時，此程式碼的輸出看起來會像這樣。

```powershell
Get-Command
Import-Module
```
