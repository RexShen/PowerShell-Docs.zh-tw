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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360977"
---
# <a name="runspace02-sample"></a>Runspace02 範例

這個範例示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別，以同步方式執行[Get 進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)和[排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)Cmdlet。 [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)[指令程式會](/dotnet/api/System.Diagnostics.Process)針對在本機電腦上執行的每個進程傳回 System.Diagnostics.Process.Id，而 @no__t 2 則會根據其[*](/dotnet/api/System.Diagnostics.Process.Id)屬性來排序物件。 這些命令的結果會使用[system.web](/dotnet/api/System.Windows.Forms.DataGridView)控制項來顯示。

## <a name="requirements"></a>需求

此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>演示

這個範例會示範下列各項。

- 建立要執行命令的[system.web](/dotnet/api/system.management.automation.powershell)物件。

- 將命令新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。

- 同步執行命令。

- 使用[system.web](/dotnet/api/System.Windows.Forms.DataGridView)控制項在 Windows Forms 應用程式中顯示命令的輸出。

## <a name="example"></a>範例

這個範例會在 Windows PowerShell 所提供的預設執行時間中，以同步方式執行「[取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」和「[排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)」 Cmdlet。 輸出會以表單的形式顯示，並使用[system.web](/dotnet/api/System.Windows.Forms.DataGridView)控制項。

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

[撰寫 Windows PowerShell 主應用程式](./writing-a-windows-powershell-host-application.md)