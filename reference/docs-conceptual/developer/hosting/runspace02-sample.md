---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace02 範例
description: Runspace02 範例
ms.openlocfilehash: 0206e1a80f3e5488fd2dd5628985756a5ca343c8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657901"
---
# <a name="runspace02-sample"></a>Runspace02 範例

這個範例會示範如何使用 system.string [類別，](/dotnet/api/system.management.automation.powershell) 以同步方式執行 [Get 進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 和 [排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlet。 [取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式會傳回在本機電腦上執行之每個處理[程式的處理常式](/dotnet/api/System.Diagnostics.Process)物件，並 `Sort-Object` 根據物件的[System.Diagnostics.Process.Id *](/dotnet/api/System.Diagnostics.Process.Id)屬性來排序物件。 這些命令的結果會使用 [ [system.object](/dotnet/api/System.Windows.Forms.DataGridView) ] 控制項來顯示。

## <a name="requirements"></a>規格需求

此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

這個範例會示範下列各項。

- 建立要執行命令的 [系統. 管理. Powershell](/dotnet/api/system.management.automation.powershell) 物件。

- 將命令加入至 [system.object](/dotnet/api/system.management.automation.powershell) 物件的管線。

- 以同步方式執行命令。

- 使用 [ [system.object](/dotnet/api/System.Windows.Forms.DataGridView) ] 控制項，在 Windows Forms 應用程式中顯示命令的輸出。

## <a name="example"></a>範例

此範例會在 Windows PowerShell 所提供的預設執行空間中，同步執行 [Get 進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 和 [排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlet。 輸出會以表單顯示在表單[中。](/dotnet/api/System.Windows.Forms.DataGridView)

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
