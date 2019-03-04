---
title: GetProcessSample02 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859854"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="cf90c-102">GetProcessSample02 範例</span><span class="sxs-lookup"><span data-stu-id="cf90c-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="cf90c-103">此範例示範如何撰寫 cmdlet 來擷取本機電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="cf90c-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="cf90c-104">它提供`Name`可用來指定要擷取的處理程序的參數。</span><span class="sxs-lookup"><span data-stu-id="cf90c-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="cf90c-105">這個指令程式是一個簡化的版的`Get-Process`Windows PowerShell 2.0 所提供的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf90c-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="cf90c-106">如何使用 Visual Studio 建置範例。</span><span class="sxs-lookup"><span data-stu-id="cf90c-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="cf90c-107">安裝 Windows PowerShell 2.0 sdk，瀏覽至 GetProcessSample02 資料夾。</span><span class="sxs-lookup"><span data-stu-id="cf90c-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="cf90c-108">預設位置是 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02。</span><span class="sxs-lookup"><span data-stu-id="cf90c-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="cf90c-109">按兩下方案 (.sln) 檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="cf90c-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="cf90c-110">這是在 Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="cf90c-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="cf90c-111">在 **建置**功能表上，選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="cf90c-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="cf90c-112">如需範例程式庫將建置的預設 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="cf90c-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="cf90c-113">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="cf90c-113">How to run the sample</span></span>

1. <span data-ttu-id="cf90c-114">建立下列的模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="cf90c-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="cf90c-115">將範例組件複製到模組資料夾中。</span><span class="sxs-lookup"><span data-stu-id="cf90c-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="cf90c-116">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cf90c-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="cf90c-117">執行下列命令，以將組件載入 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="cf90c-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="cf90c-118">執行下列命令來執行 cmdlet:</span><span class="sxs-lookup"><span data-stu-id="cf90c-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="cf90c-119">需求</span><span class="sxs-lookup"><span data-stu-id="cf90c-119">Requirements</span></span>

<span data-ttu-id="cf90c-120">這個範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="cf90c-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cf90c-121">示範</span><span class="sxs-lookup"><span data-stu-id="cf90c-121">Demonstrates</span></span>

<span data-ttu-id="cf90c-122">此範例示範下列項目。</span><span class="sxs-lookup"><span data-stu-id="cf90c-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="cf90c-123">宣告 cmdlet 類別使用 Cmdlet 屬性。</span><span class="sxs-lookup"><span data-stu-id="cf90c-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="cf90c-124">宣告 cmdlet 參數使用的參數屬性。</span><span class="sxs-lookup"><span data-stu-id="cf90c-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="cf90c-125">指定參數的位置。</span><span class="sxs-lookup"><span data-stu-id="cf90c-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="cf90c-126">宣告參數輸入的驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="cf90c-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="cf90c-127">範例</span><span class="sxs-lookup"><span data-stu-id="cf90c-127">Example</span></span>

<span data-ttu-id="cf90c-128">此範例示範如何實作的 Get-proc cmdlet，其中包含`Name`參數。</span><span class="sxs-lookup"><span data-stu-id="cf90c-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cf90c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf90c-129">See Also</span></span>

[<span data-ttu-id="cf90c-130">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cf90c-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
