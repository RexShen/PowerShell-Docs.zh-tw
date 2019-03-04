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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854284"
---
# <a name="runspace02-sample"></a><span data-ttu-id="b921a-102">Runspace02 範例</span><span class="sxs-lookup"><span data-stu-id="b921a-102">Runspace02 Sample</span></span>

<span data-ttu-id="b921a-103">此範例示範如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)類別來執行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)並[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet 以同步方式。</span><span class="sxs-lookup"><span data-stu-id="b921a-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="b921a-104">[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 會傳回[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)每個處理序在本機電腦上執行的物件和`Sort-Object`排序物件根據其[System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id)屬性。</span><span class="sxs-lookup"><span data-stu-id="b921a-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="b921a-105">這些命令的結果會顯示藉由使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控制項。</span><span class="sxs-lookup"><span data-stu-id="b921a-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="b921a-106">需求</span><span class="sxs-lookup"><span data-stu-id="b921a-106">Requirements</span></span>

<span data-ttu-id="b921a-107">這個範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="b921a-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b921a-108">示範</span><span class="sxs-lookup"><span data-stu-id="b921a-108">Demonstrates</span></span>

<span data-ttu-id="b921a-109">此範例示範下列項目。</span><span class="sxs-lookup"><span data-stu-id="b921a-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="b921a-110">建立[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件執行命令。</span><span class="sxs-lookup"><span data-stu-id="b921a-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="b921a-111">將命令加入至的管線[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="b921a-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="b921a-112">以同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="b921a-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="b921a-113">使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控制項來顯示命令的輸出中的 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b921a-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="b921a-114">範例</span><span class="sxs-lookup"><span data-stu-id="b921a-114">Example</span></span>

<span data-ttu-id="b921a-115">此範例會執行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)並[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)同步中的 Windows PowerShell 所提供的預設 runspace 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b921a-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="b921a-116">輸出會顯示在表單中使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控制項。</span><span class="sxs-lookup"><span data-stu-id="b921a-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b921a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b921a-117">See Also</span></span>

[<span data-ttu-id="b921a-118">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="b921a-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)