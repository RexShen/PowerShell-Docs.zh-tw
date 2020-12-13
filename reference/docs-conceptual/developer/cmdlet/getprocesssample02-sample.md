---
ms.date: 09/13/2016
ms.topic: reference
title: GetProcessSample02 範例
description: GetProcessSample02 範例
ms.openlocfilehash: a0f43806b707359cb454817341f2c4972033c46a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660526"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="6d637-103">GetProcessSample02 範例</span><span class="sxs-lookup"><span data-stu-id="6d637-103">GetProcessSample02 Sample</span></span>

<span data-ttu-id="6d637-104">此範例示範如何撰寫可在本機電腦上抓取進程的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6d637-104">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="6d637-105">它會提供一個 `Name` 參數，可用來指定要抓取的進程。</span><span class="sxs-lookup"><span data-stu-id="6d637-105">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="6d637-106">此 Cmdlet 是 `Get-Process` Windows PowerShell 2.0 提供的簡化版 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6d637-106">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="6d637-107">如何使用 Visual Studio 建立範例。</span><span class="sxs-lookup"><span data-stu-id="6d637-107">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="6d637-108">安裝 Windows PowerShell 2.0 SDK 之後，請流覽至 >getprocesssample02 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d637-108">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="6d637-109">預設位置為 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02。</span><span class="sxs-lookup"><span data-stu-id="6d637-109">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="6d637-110">按兩下方案 ( .sln) 檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="6d637-110">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="6d637-111">這會在 Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="6d637-111">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="6d637-112">在 [建置] 功能表中，選取 [建置方案]。</span><span class="sxs-lookup"><span data-stu-id="6d637-112">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="6d637-113">範例的程式庫會建立在預設的 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6d637-113">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="6d637-114">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="6d637-114">How to run the sample</span></span>

1. <span data-ttu-id="6d637-115">建立下列模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="6d637-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="6d637-116">將範例元件複製到模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d637-116">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="6d637-117">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6d637-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="6d637-118">執行下列命令，將元件載入 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="6d637-118">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="6d637-119">執行下列命令以執行 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="6d637-119">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="6d637-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="6d637-120">Requirements</span></span>

<span data-ttu-id="6d637-121">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="6d637-121">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6d637-122">示範</span><span class="sxs-lookup"><span data-stu-id="6d637-122">Demonstrates</span></span>

<span data-ttu-id="6d637-123">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="6d637-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="6d637-124">使用 Cmdlet 屬性宣告 Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="6d637-124">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="6d637-125">使用參數屬性宣告 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="6d637-125">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="6d637-126">指定參數的位置。</span><span class="sxs-lookup"><span data-stu-id="6d637-126">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="6d637-127">宣告參數輸入的驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="6d637-127">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="6d637-128">範例</span><span class="sxs-lookup"><span data-stu-id="6d637-128">Example</span></span>

<span data-ttu-id="6d637-129">此範例顯示包含參數的 Get-Proc Cmdlet 的執行 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="6d637-129">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="6d637-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d637-130">See Also</span></span>

[<span data-ttu-id="6d637-131">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6d637-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
