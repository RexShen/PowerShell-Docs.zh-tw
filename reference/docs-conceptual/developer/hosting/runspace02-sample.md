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
# <a name="runspace02-sample"></a><span data-ttu-id="28a71-103">Runspace02 範例</span><span class="sxs-lookup"><span data-stu-id="28a71-103">Runspace02 Sample</span></span>

<span data-ttu-id="28a71-104">這個範例會示範如何使用 system.string [類別，](/dotnet/api/system.management.automation.powershell) 以同步方式執行 [Get 進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 和 [排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="28a71-104">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="28a71-105">[取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式會傳回在本機電腦上執行之每個處理[程式的處理常式](/dotnet/api/System.Diagnostics.Process)物件，並 `Sort-Object` 根據物件的[System.Diagnostics.Process.Id \*](/dotnet/api/System.Diagnostics.Process.Id)屬性來排序物件。</span><span class="sxs-lookup"><span data-stu-id="28a71-105">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="28a71-106">這些命令的結果會使用 [ [system.object](/dotnet/api/System.Windows.Forms.DataGridView) ] 控制項來顯示。</span><span class="sxs-lookup"><span data-stu-id="28a71-106">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="28a71-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="28a71-107">Requirements</span></span>

<span data-ttu-id="28a71-108">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="28a71-108">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="28a71-109">示範</span><span class="sxs-lookup"><span data-stu-id="28a71-109">Demonstrates</span></span>

<span data-ttu-id="28a71-110">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="28a71-110">This sample demonstrates the following.</span></span>

- <span data-ttu-id="28a71-111">建立要執行命令的 [系統. 管理. Powershell](/dotnet/api/system.management.automation.powershell) 物件。</span><span class="sxs-lookup"><span data-stu-id="28a71-111">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="28a71-112">將命令加入至 [system.object](/dotnet/api/system.management.automation.powershell) 物件的管線。</span><span class="sxs-lookup"><span data-stu-id="28a71-112">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="28a71-113">以同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="28a71-113">Running the commands synchronously.</span></span>

- <span data-ttu-id="28a71-114">使用 [ [system.object](/dotnet/api/System.Windows.Forms.DataGridView) ] 控制項，在 Windows Forms 應用程式中顯示命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="28a71-114">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="28a71-115">範例</span><span class="sxs-lookup"><span data-stu-id="28a71-115">Example</span></span>

<span data-ttu-id="28a71-116">此範例會在 Windows PowerShell 所提供的預設執行空間中，同步執行 [Get 進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 和 [排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="28a71-116">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="28a71-117">輸出會以表單顯示在表單[中。](/dotnet/api/System.Windows.Forms.DataGridView)</span><span class="sxs-lookup"><span data-stu-id="28a71-117">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="28a71-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28a71-118">See Also</span></span>

[<span data-ttu-id="28a71-119">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="28a71-119">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
