---
title: StopProcessSample02 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 213ca1a4-e9fe-4969-b7d0-2fca070c6142
caps.latest.revision: 10
ms.openlocfilehash: 594c06367baedd1f9bfdbfff9f0e072d579b4099
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369377"
---
# <a name="stopprocesssample02-sample"></a><span data-ttu-id="3f92f-102">StopProcessSample02 範例</span><span class="sxs-lookup"><span data-stu-id="3f92f-102">StopProcessSample02 Sample</span></span>

<span data-ttu-id="3f92f-103">這個範例示範如何撰寫 Cmdlet，以在停止本機電腦上的處理常式時寫入 debug （WriteDebug）、verbose （WriteVerbose）和 warning （WriteWarning）訊息。</span><span class="sxs-lookup"><span data-stu-id="3f92f-103">This sample shows how to write a cmdlet that writes debug (WriteDebug), verbose (WriteVerbose), and warning (WriteWarning) messages while stopping processes on the local computer.</span></span> <span data-ttu-id="3f92f-104">此 Cmdlet 類似于 Windows PowerShell 2.0 所提供的 `Stop-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3f92f-104">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="3f92f-105">如何使用 Visual Studio 建立範例。</span><span class="sxs-lookup"><span data-stu-id="3f92f-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="3f92f-106">開啟 Windows Internet Explorer，然後流覽至範例目錄底下的 StopProcessSample02 目錄。</span><span class="sxs-lookup"><span data-stu-id="3f92f-106">Open Windows Internet Explorer and navigate to the StopProcessSample02 directory under the Samples directory.</span></span>

    <span data-ttu-id="3f92f-107">安裝 Windows PowerShell 2.0 SDK 之後，流覽至 StopProcessSample02 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f92f-107">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample02 folder.</span></span> <span data-ttu-id="3f92f-108">預設位置為 C:\Program Files （x86） \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02。</span><span class="sxs-lookup"><span data-stu-id="3f92f-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span></span>

2. <span data-ttu-id="3f92f-109">按兩下方案（.sln）檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="3f92f-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="3f92f-110">這會在 Microsoft Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="3f92f-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="3f92f-111">在 [建置] 功能表中，選取 [建置方案]。</span><span class="sxs-lookup"><span data-stu-id="3f92f-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="3f92f-112">範例的程式庫會建立在預設的 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3f92f-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="3f92f-113">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="3f92f-113">How to run the sample</span></span>

1. <span data-ttu-id="3f92f-114">建立下列模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="3f92f-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample02`

2. <span data-ttu-id="3f92f-115">將範例元件複製到模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f92f-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="3f92f-116">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3f92f-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="3f92f-117">執行下列命令，將元件載入 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="3f92f-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample02`

5. <span data-ttu-id="3f92f-118">執行下列命令來執行 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="3f92f-118">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="3f92f-119">需求</span><span class="sxs-lookup"><span data-stu-id="3f92f-119">Requirements</span></span>

<span data-ttu-id="3f92f-120">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="3f92f-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3f92f-121">示範</span><span class="sxs-lookup"><span data-stu-id="3f92f-121">Demonstrates</span></span>

<span data-ttu-id="3f92f-122">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="3f92f-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="3f92f-123">使用 Cmdlet 屬性宣告 Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="3f92f-123">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="3f92f-124">使用參數屬性宣告 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="3f92f-124">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="3f92f-125">撰寫詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="3f92f-125">Writing verbose messages.</span></span> <span data-ttu-id="3f92f-126">如需用來撰寫詳細訊息之方法的詳細資訊，請參閱[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)。</span><span class="sxs-lookup"><span data-stu-id="3f92f-126">For more information about the method used to write verbose messages, see [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

- <span data-ttu-id="3f92f-127">寫入錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3f92f-127">Writing error messages.</span></span> <span data-ttu-id="3f92f-128">如需用來撰寫錯誤訊息之方法的詳細資訊，請參閱[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)。</span><span class="sxs-lookup"><span data-stu-id="3f92f-128">For more information about the method used to write error messages, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span></span>

- <span data-ttu-id="3f92f-129">寫入警告訊息。</span><span class="sxs-lookup"><span data-stu-id="3f92f-129">Writing warning messages.</span></span> <span data-ttu-id="3f92f-130">如需用來撰寫警告訊息之方法的詳細資訊，請參閱[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)。</span><span class="sxs-lookup"><span data-stu-id="3f92f-130">For more information about the method used to write warning messages, see [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span></span>

## <a name="example"></a><span data-ttu-id="3f92f-131">範例</span><span class="sxs-lookup"><span data-stu-id="3f92f-131">Example</span></span>

<span data-ttu-id="3f92f-132">這個範例會示範如何使用 `WriteDebug`、`WriteVerbose`和 `WriteWarning` 方法，撰寫 debug、verbose 和 warning 訊息。</span><span class="sxs-lookup"><span data-stu-id="3f92f-132">This sample shows how to write debug, verbose, and warning messages by using the `WriteDebug`, `WriteVerbose`, and `WriteWarning` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;             //Windows PowerShell namespace
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
               string message = null;

               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.

               // Write a user-friendly verbose message to the pipeline. These
               // messages are intended to give the user detailed information
               // on the operations performed by the cmdlet. These messages will
               // appear with the -Verbose option.
               message = String.Format(CultureInfo.CurrentCulture,
                              "Attempting to stop process \"{0}\".", name);
               WriteVerbose(message);

               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,
                                     "UnableToAccessProcessByName",
                                         ErrorCategory.InvalidOperation,
                                             name));
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
                                         ErrorCategory.ObjectNotFound, process));
                       continue;
                   }

                   // Write a debug message to the host that can be used when
                   // troubleshooting a problem. All debug messages will appear
                   // with the -Debug option.
                   message = String.Format(CultureInfo.CurrentCulture,
                                 "Acquired name for pid {0} : \"{1}\"",
                                        process.Id, processName);
                   WriteDebug(message);

                   // Confirm the operation first.
                   // This is always false if the WhatIf parameter is specified.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,
                                        "{0} ({1})",
                                            processName, process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that can possibly stop the computer.
                   bool criticalProcess = criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess && !force)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
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

                   // Display a warning message if the cmdlet is stopping a
                   // critical process.
                   if (criticalProcess)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Stopping the critical process \"{0}\".",
                                          processName);
                       WriteWarning(message);
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
                           WriteError(new ErrorRecord(
                                            e,
                                            "CouldNotStopProcess",
                                            ErrorCategory.CloseError,
                                            process)
                                      );
                           continue;
                       } // if ((e is...
                           else throw;
                   } // catch

                   message = String.Format(CultureInfo.CurrentCulture,
                                  "Stopped process \"{0}\", pid {1}.",
                                        processName, process.Id);

                   WriteVerbose(message);

                   // If the PassThru parameter is specified,
                   // return the terminated process object to the pipeline.
                   if (passThru)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Writing process \"{0}\" to pipeline",
                                          processName);
                       WriteDebug(message);
                       WriteObject(process);
                   } // if (passThru...
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

## <a name="see-also"></a><span data-ttu-id="3f92f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f92f-133">See Also</span></span>

[<span data-ttu-id="3f92f-134">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f92f-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
