---
title: Runspace02 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082714"
---
# <a name="runspace02-sample"></a>Runspace02 範例

此範例示範如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)類別來執行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)並[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet 以同步方式。 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 會傳回[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)每個處理序在本機電腦上執行的物件和`Sort-Object`排序物件根據其[System.Diagnostics.Process.Id*](/dotnet/api/System.Diagnostics.Process.Id)屬性。 這些命令的結果會顯示藉由使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控制項。

## <a name="requirements"></a>需求

這個範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

此範例示範下列項目。

- 建立[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件執行命令。

- 將命令加入至的管線[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。

- 以同步方式執行命令。

- 使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控制項來顯示命令的輸出中的 Windows Forms 應用程式。

## <a name="example"></a>範例

此範例會執行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)並[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)同步中的 Windows PowerShell 所提供的預設 runspace 的 cmdlet。 輸出會顯示在表單中使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控制項。

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 主機應用程式](./writing-a-windows-powershell-host-application.md)