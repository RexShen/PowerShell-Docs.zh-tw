---
title: GetProcessSample03 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068040"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="bcfb0-102">GetProcessSample03 範例</span><span class="sxs-lookup"><span data-stu-id="bcfb0-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="bcfb0-103">此範例示範如何實作的 cmdlet，擷取本機電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="bcfb0-104">它提供`Name`可以接受來自管線的物件或從屬性名稱是參數名稱與相同物件的屬性值的參數。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="bcfb0-105">這個指令程式是一個簡化的版的`Get-Process`Windows PowerShell 2.0 所提供的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="bcfb0-106">如何使用 Visual Studio 建置範例。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="bcfb0-107">安裝 Windows PowerShell 2.0 sdk，瀏覽至 GetProcessSample03 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="bcfb0-108">預設位置是 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="bcfb0-109">按兩下方案 (.sln) 檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="bcfb0-110">這是在 Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="bcfb0-111">在 **建置**功能表上，選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="bcfb0-112">如需範例程式庫將建置的預設 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="bcfb0-113">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="bcfb0-113">How to run the sample</span></span>

1. <span data-ttu-id="bcfb0-114">建立下列的模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="bcfb0-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="bcfb0-115">將範例組件複製到模組資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="bcfb0-116">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="bcfb0-117">執行下列命令，以將組件載入 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bcfb0-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="bcfb0-118">執行下列命令來執行 cmdlet:</span><span class="sxs-lookup"><span data-stu-id="bcfb0-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="bcfb0-119">需求</span><span class="sxs-lookup"><span data-stu-id="bcfb0-119">Requirements</span></span>

<span data-ttu-id="bcfb0-120">這個範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bcfb0-121">示範</span><span class="sxs-lookup"><span data-stu-id="bcfb0-121">Demonstrates</span></span>

<span data-ttu-id="bcfb0-122">此範例示範下列項目。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="bcfb0-123">宣告 cmdlet 類別使用 Cmdlet 屬性。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="bcfb0-124">宣告 cmdlet 參數使用的參數屬性。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="bcfb0-125">指定參數的位置。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="bcfb0-126">指定此參數只接受從管線輸入。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="bcfb0-127">輸入可以取自物件或物件的屬性名稱為參數名稱相同的屬性的值。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="bcfb0-128">宣告參數輸入的驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="bcfb0-129">範例</span><span class="sxs-lookup"><span data-stu-id="bcfb0-129">Example</span></span>

<span data-ttu-id="bcfb0-130">此範例示範如何實作的 Get-proc cmdlet，其中包含`Name`接受來自管線的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="bcfb0-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
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
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
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
    /// associated processes to the pipeline.
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
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="bcfb0-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcfb0-131">See Also</span></span>

[<span data-ttu-id="bcfb0-132">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bcfb0-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
