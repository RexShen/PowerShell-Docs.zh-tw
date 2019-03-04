---
title: GetProcessSample04 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861874"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="3a8a9-102">GetProcessSample04 範例</span><span class="sxs-lookup"><span data-stu-id="3a8a9-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="3a8a9-103">此範例示範如何實作的 cmdlet，擷取本機電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="3a8a9-104">如果在擷取處理序時發生錯誤，它會產生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="3a8a9-105">這個指令程式是一個簡化的版的`Get-Process`Windows PowerShell 2.0 所提供的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="3a8a9-106">如何使用 Visual Studio 建置範例。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="3a8a9-107">安裝 Windows PowerShell 2.0 sdk，瀏覽至 GetProcessSample04 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="3a8a9-108">預設位置是 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="3a8a9-109">按兩下方案 (.sln) 檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="3a8a9-110">這是在 Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="3a8a9-111">在 **建置**功能表上，選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="3a8a9-112">如需範例程式庫將建置的預設 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="3a8a9-113">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="3a8a9-113">How to run the sample</span></span>

1. <span data-ttu-id="3a8a9-114">建立下列的模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="3a8a9-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="3a8a9-115">將範例組件複製到模組資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="3a8a9-116">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="3a8a9-117">執行下列命令，以將組件載入 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3a8a9-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="3a8a9-118">執行下列命令來執行 cmdlet:</span><span class="sxs-lookup"><span data-stu-id="3a8a9-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="3a8a9-119">需求</span><span class="sxs-lookup"><span data-stu-id="3a8a9-119">Requirements</span></span>

<span data-ttu-id="3a8a9-120">這個範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3a8a9-121">示範</span><span class="sxs-lookup"><span data-stu-id="3a8a9-121">Demonstrates</span></span>

<span data-ttu-id="3a8a9-122">此範例示範下列項目。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="3a8a9-123">宣告 cmdlet 類別使用 Cmdlet 屬性。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="3a8a9-124">宣告 cmdlet 參數使用的參數屬性。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="3a8a9-125">指定參數的位置。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="3a8a9-126">指定此參數只接受從管線輸入。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="3a8a9-127">輸入可以取自物件或物件的屬性名稱為參數名稱相同的屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="3a8a9-128">宣告參數輸入的驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="3a8a9-129">補捉非終止錯誤和錯誤資料流中寫入一則錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="3a8a9-130">範例</span><span class="sxs-lookup"><span data-stu-id="3a8a9-130">Example</span></span>

<span data-ttu-id="3a8a9-131">此範例示範如何建立 cmdlet 會處理非終止錯誤，並將錯誤訊息寫入到錯誤資料流。</span><span class="sxs-lookup"><span data-stu-id="3a8a9-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
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
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="3a8a9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a8a9-132">See Also</span></span>

[<span data-ttu-id="3a8a9-133">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3a8a9-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
