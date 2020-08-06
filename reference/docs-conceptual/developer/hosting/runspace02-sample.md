---
title: Runspace02 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7a2dce436aceb1d8744377c37671a66398614851
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784957"
---
# <a name="runspace02-sample"></a><span data-ttu-id="eb5f3-102">Runspace02 範例</span><span class="sxs-lookup"><span data-stu-id="eb5f3-102">Runspace02 Sample</span></span>

<span data-ttu-id="eb5f3-103">這個範例示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別，以同步方式執行[Get 進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)和[排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="eb5f3-104">[取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式會針對在本機電腦上執行的每個進程傳回[system.web](/dotnet/api/System.Diagnostics.Process)物件，並 `Sort-Object` 根據物件的[System.Diagnostics.Process.Id \*](/dotnet/api/System.Diagnostics.Process.Id)屬性來排序物件。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="eb5f3-105">這些命令的結果會使用[system.web](/dotnet/api/System.Windows.Forms.DataGridView)控制項來顯示。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb5f3-106">需求</span><span class="sxs-lookup"><span data-stu-id="eb5f3-106">Requirements</span></span>

<span data-ttu-id="eb5f3-107">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="eb5f3-108">示範</span><span class="sxs-lookup"><span data-stu-id="eb5f3-108">Demonstrates</span></span>

<span data-ttu-id="eb5f3-109">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="eb5f3-110">建立要執行命令的[system.web](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="eb5f3-111">將命令新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="eb5f3-112">同步執行命令。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="eb5f3-113">使用[system.web](/dotnet/api/System.Windows.Forms.DataGridView)控制項在 Windows Forms 應用程式中顯示命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="eb5f3-114">範例</span><span class="sxs-lookup"><span data-stu-id="eb5f3-114">Example</span></span>

<span data-ttu-id="eb5f3-115">這個範例會在 Windows PowerShell 所提供的預設執行時間中，以同步方式執行「[取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」和「[排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)」 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="eb5f3-116">輸出會以表單的形式顯示，並使用[system.web](/dotnet/api/System.Windows.Forms.DataGridView)控制項。</span><span class="sxs-lookup"><span data-stu-id="eb5f3-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eb5f3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb5f3-117">See Also</span></span>

[<span data-ttu-id="eb5f3-118">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="eb5f3-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
