---
title: Windows PowerShell 主應用程式快速入門 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: cc014487a680747ad59437052f79d4576154a1cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082544"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell 主機快速入門

若要在您的應用程式中裝載 Windows PowerShell，使用[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)類別。 這個類別提供建立命令的管線，然後在 runspace 中執行這些命令的方法。 建立主應用程式的最簡單方式是使用預設的 runspace。 預設的 runspace 中包含所有的核心 Windows PowerShell 命令。 如果您想您的應用程式公開 （expose） 的 Windows PowerShell 命令的子集，您必須建立自訂的 runspace。

## <a name="using-the-default-runspace"></a>使用預設的 runspace

若要開始，我們將使用預設的 runspace，並使用的方法[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)類別將命令、 參數、 陳述式和指令碼新增至管線。

### <a name="addcommand"></a>AddCommand

您使用[System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)將命令新增至管線的類別。 例如，假設您想要取得的電腦上執行的處理序清單。 若要執行此命令的方式如下所示。

1. 建立[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)物件。

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

如果您呼叫[System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法超過一次，然後再呼叫[System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法、 結果第一個命令會輸送到第二個，依此類推。 如果您不想透過管道傳送命令前一個命令的結果，會將它加入藉由呼叫[System.Management.Automation.Powershell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)改。

### <a name="addparameter"></a>AddParameter

前一個範例會執行不含任何參數的單一命令。 可以透過將參數新增至命令[System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法，例如下列程式碼會取得一份所有程序會在名為`PowerShell`上執行機器。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

您可以新增額外的參數，藉由呼叫[System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)重複。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

您也可以藉由呼叫來新增參數名稱和值的字典[System.Management.Automation.PowerShell.AddParameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法。

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

您可以使用批次處理來模擬[System.Management.Automation.PowerShell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法，將其他的陳述式加入至管線，下列程式碼會取得執行程序名稱的清單結尾`PowerShell`，然後取得執行中服務的清單。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

您可以執行現有的指令碼，藉由呼叫[System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法。 下列範例會將指令碼新增至管線，並執行它。 這個範例假設已經有名稱為指令碼`MyScript.ps1`在名為的資料夾中`D:\PSScripts`。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

另外還有一份[System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法接受名為的布林參數`useLocalScope`。 如果此參數設為`true`，則指令碼會執行本機範圍內。 下列程式碼會在本機的範圍內執行指令碼。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>建立自訂的 runspace

雖然先前的範例中使用的預設 runspace 載入所有的核心 Windows PowerShell 命令，您可以建立自訂的 runspace 可載入的指定的子集的所有命令。 您可能想要這樣做可以改善效能 （載入大量的命令會影響效能），或限制使用者能夠執行作業。 會公開有限的數目的命令的 runspace 稱為受限的 runspace。 若要建立受限的 runspace，您使用[System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace)並[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)類別。

### <a name="creating-an-initialsessionstate-object"></a>建立 InitialSessionState 物件

若要建立自訂的 runspace，您必須先建立[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。 在下列範例中，我們會使用[System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory)後建立的預設值建立 runspace [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>限制的 runspace

在上述範例中，我們已建立預設值[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)載入所有內建的核心 Windows PowerShell 的物件。 我們可能也會有稱為[System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法用來建立 InitialSessionState 物件，會載入只有 Microsoft.PowerShell.Core 中的命令嵌入式管理單元。 若要建立更受限的 runspace，您必須建立空[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)藉由呼叫物件[System.Management.Automation.Runspaces.InitialSessionState.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法，然後將命令新增至 InitialSessionState。

使用您指定的命令會載入 runspace 提供大幅改善的效能。

您使用的方法[System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)類別來定義初始工作階段狀態的 cmdlet。 下列範例會建立空的初始工作階段狀態，然後定義並加入`Get-Command`和`Import-Module`命令來初始工作階段狀態。 然後，我們會建立 runspace，受到初始工作階段狀態，並在該 runspace 中執行命令。

建立初始工作階段狀態。

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

定義，並將命令加入至初始工作階段狀態。

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

建立並開啟 runspace。

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

執行命令，並顯示結果。

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

當執行時，此程式碼的輸出會看起來像這樣。

```powershell
Get-Command
Import-Module
```
