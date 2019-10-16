---
title: StopProcessSample01 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7bed607-369b-4507-87fa-f6011c2f1970
caps.latest.revision: 9
ms.openlocfilehash: 2ce146df05ef876d9c17f560628ebac2c39e57bf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365297"
---
# <a name="stopprocesssample01-sample"></a><span data-ttu-id="8dd48-102">StopProcessSample01 範例</span><span class="sxs-lookup"><span data-stu-id="8dd48-102">StopProcessSample01 Sample</span></span>

<span data-ttu-id="8dd48-103">這個範例示範如何撰寫 Cmdlet，以在嘗試停止進程之前要求使用者提供意見反應，以及如何執行 `PassThru` 參數，表示使用者想要 Cmdlet 傳回物件。</span><span class="sxs-lookup"><span data-stu-id="8dd48-103">This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter indicating that the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="8dd48-104">此 Cmdlet 類似于 Windows PowerShell 2.0 所提供的 `Stop-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8dd48-104">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="8dd48-105">如何使用 Visual Studio 建立範例。</span><span class="sxs-lookup"><span data-stu-id="8dd48-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="8dd48-106">安裝 Windows PowerShell 2.0 SDK 之後，流覽至 StopProcessSample01 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8dd48-106">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample01 folder.</span></span> <span data-ttu-id="8dd48-107">預設位置為 C:\Program Files （x86） \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01。</span><span class="sxs-lookup"><span data-stu-id="8dd48-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.</span></span>

2. <span data-ttu-id="8dd48-108">按兩下方案（.sln）檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="8dd48-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="8dd48-109">這會在 Microsoft Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="8dd48-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="8dd48-110">在 [**建立**] 功能表中，選取 [**建立方案**]。</span><span class="sxs-lookup"><span data-stu-id="8dd48-110">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="8dd48-111">範例的程式庫會建立在預設的 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="8dd48-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="8dd48-112">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="8dd48-112">How to run the sample</span></span>

1. <span data-ttu-id="8dd48-113">建立下列模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="8dd48-113">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample01`

2. <span data-ttu-id="8dd48-114">將範例元件複製到模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="8dd48-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="8dd48-115">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8dd48-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="8dd48-116">執行下列命令，將元件載入 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="8dd48-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample01`

5. <span data-ttu-id="8dd48-117">執行下列命令來執行 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="8dd48-117">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="8dd48-118">需求</span><span class="sxs-lookup"><span data-stu-id="8dd48-118">Requirements</span></span>

<span data-ttu-id="8dd48-119">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="8dd48-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8dd48-120">演示</span><span class="sxs-lookup"><span data-stu-id="8dd48-120">Demonstrates</span></span>

<span data-ttu-id="8dd48-121">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="8dd48-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="8dd48-122">使用 Cmdlet 屬性宣告 Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="8dd48-122">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="8dd48-123">使用參數屬性宣告 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="8dd48-123">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="8dd48-124">呼叫 ShouldProcess 方法以要求確認。</span><span class="sxs-lookup"><span data-stu-id="8dd48-124">Calling the ShouldProcess method to request confirmation.</span></span>

- <span data-ttu-id="8dd48-125">執行 `PassThru` 參數，指出使用者是否想要 Cmdlet 傳回物件。</span><span class="sxs-lookup"><span data-stu-id="8dd48-125">Implementing a `PassThru` parameter that indicates if the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="8dd48-126">根據預設，此 Cmdlet 不會將物件傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="8dd48-126">By default, this cmdlet does not return an object to the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="8dd48-127">範例</span><span class="sxs-lookup"><span data-stu-id="8dd48-127">Example</span></span>

<span data-ttu-id="8dd48-128">這個範例示範如何執行 `PassThru` 參數，表示使用者想要 Cmdlet 傳回物件，以及如何藉由呼叫 `ShouldProcess` 和 @no__t 2 方法來要求使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="8dd48-128">This sample shows how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object, and how to request user feedback by calls to the `ShouldProcess` and `ShouldContinue` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;    // Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true
       )]
       public string[] Name
       {
           get { return processNames; }
           set { processNames = value; }
       }
       private string[] processNames;

       /// <summary>
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.
               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,"UnableToAccessProcessByName",
                       ErrorCategory.InvalidOperation, name));

                   continue;
               }

               // Try to stop the processes that have been retrieved.
               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                      WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                           ErrorCategory.ReadError, process));
                      continue;
                   }

                   // Confirm the operation with the user first.
                   // This is always false if the WhatIf parameter is set.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,"{0} ({1})", processName,
                               process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that could possibly stop the computer.
                   bool criticalProcess =
                       criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess &&!force)
                   {
                       string message = String.Format
                           (CultureInfo.CurrentCulture,
                                "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                    processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are received as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across multiple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                               ref yesToAll, ref noToAll))
                       {
                           continue;
                       }
                   } // if (criticalProcess...

                   // Stop the named process.
                   try
                   {
                       process.Kill();
                   }
                   catch (Exception e)
                   {
                       if ((e is Win32Exception) || (e is SystemException) ||
                          (e is InvalidOperationException))
                       {
                           // This process could not be stopped so write
                           // a nonterminating error.
                           WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                           ErrorCategory.CloseError, process));
                           continue;
                       } // if ((e is...
                       else throw;
                   } // catch

                   // If the PassThru parameter is
                   // specified, return the terminated process.
                   if (passThru)
                   {
                       WriteObject(process);
                   }
               } // foreach (Process...
           } // foreach (string...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="8dd48-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd48-129">See Also</span></span>

[<span data-ttu-id="8dd48-130">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8dd48-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
