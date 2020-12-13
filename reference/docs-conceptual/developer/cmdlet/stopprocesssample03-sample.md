---
ms.date: 09/13/2016
ms.topic: reference
title: StopProcessSample03 範例
description: StopProcessSample03 範例
ms.openlocfilehash: b633161dd7a329dffa076d828862ee39fb256429
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650165"
---
# <a name="stopprocesssample03-sample"></a><span data-ttu-id="ba651-103">StopProcessSample03 範例</span><span class="sxs-lookup"><span data-stu-id="ba651-103">StopProcessSample03 Sample</span></span>

<span data-ttu-id="ba651-104">此範例示範如何撰寫參數具有別名且參數支援萬用字元的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba651-104">This sample shows how to write a cmdlet whose parameters have aliases and whose parameters support wildcard characters.</span></span> <span data-ttu-id="ba651-105">此 Cmdlet 類似于 `Stop-Process` Windows PowerShell 2.0 所提供的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba651-105">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="ba651-106">如何使用 Visual Studio 來建立範例。</span><span class="sxs-lookup"><span data-stu-id="ba651-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="ba651-107">安裝 Windows PowerShell 2.0 SDK 之後，請流覽至 StopProcessSample03 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba651-107">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample03 folder.</span></span> <span data-ttu-id="ba651-108">預設位置為 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample03。</span><span class="sxs-lookup"><span data-stu-id="ba651-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample03.</span></span>

2. <span data-ttu-id="ba651-109">按兩下方案 ( .sln) 檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="ba651-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="ba651-110">這會在 Microsoft Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="ba651-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="ba651-111">在 [建置] 功能表中，選取 [建置方案]。</span><span class="sxs-lookup"><span data-stu-id="ba651-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="ba651-112">範例的程式庫會建立在預設的 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ba651-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="ba651-113">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="ba651-113">How to run the sample</span></span>

1. <span data-ttu-id="ba651-114">建立下列模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="ba651-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample03`

2. <span data-ttu-id="ba651-115">將範例元件複製到模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba651-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="ba651-116">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ba651-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="ba651-117">執行下列命令，將元件載入 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="ba651-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample03`

5. <span data-ttu-id="ba651-118">執行下列命令以執行 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="ba651-118">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="ba651-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="ba651-119">Requirements</span></span>

<span data-ttu-id="ba651-120">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="ba651-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ba651-121">示範</span><span class="sxs-lookup"><span data-stu-id="ba651-121">Demonstrates</span></span>

<span data-ttu-id="ba651-122">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="ba651-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ba651-123">使用 Cmdlet 屬性宣告 Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="ba651-123">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="ba651-124">使用參數屬性宣告 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="ba651-124">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="ba651-125">正在將別名加入參數宣告中。</span><span class="sxs-lookup"><span data-stu-id="ba651-125">Adding aliases to parameter declarations..</span></span>

- <span data-ttu-id="ba651-126">將萬用字元支援新增至參數。</span><span class="sxs-lookup"><span data-stu-id="ba651-126">Adding wildcard support to parameters.</span></span>

## <a name="example"></a><span data-ttu-id="ba651-127">範例</span><span class="sxs-lookup"><span data-stu-id="ba651-127">Example</span></span>

<span data-ttu-id="ba651-128">這個範例會示範如何宣告參數別名和支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ba651-128">This sample shows how to declare parameter aliases and support wildcards.</span></span>

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
          ValueFromPipelineByPropertyName = true,
          HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
       )]
       [Alias("ProcessName")]
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
       [Parameter(
          ValueFromPipelineByPropertyName = true,
          HelpMessage = "If set, the process(es) will be passed to the pipeline after stopped."
       )]
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
           Process[] processes = null;

           try
           {
               processes = Process.GetProcesses();
           }
           catch (InvalidOperationException ioe)
           {
               base.ThrowTerminatingError(new ErrorRecord(ioe,
                         "UnableToAccessProcessList",
                             ErrorCategory.InvalidOperation,
                                 null));
           }

           // For every process name passed to the cmdlet, get the associated
           // processes.
           // Write a nonterminating error for failure to retrieve
           // a process.
           foreach (string name in processNames)
           {
               // Write a user-friendly verbose message to the pipeline. These
               // messages are intended to give the user detailed information
               // on the operations performed by the cmdlet. These messages will
               // appear with the -Verbose option.
               string message = String.Format(CultureInfo.CurrentCulture,
                                    "Attempting to stop process \"{0}\".", name);
               WriteVerbose(message);

               // Validate the process name against a wildcard pattern.
               // If the name does not contain any wildcard patterns, it
               // will be treated as an exact match.
               WildcardOptions options = WildcardOptions.IgnoreCase |
                                         WildcardOptions.Compiled;
               WildcardPattern wildcard = new WildcardPattern(name,options);

               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                       WriteError(new ErrorRecord(
                                              e, "ProcessNameNotFound",
                                                ErrorCategory.ObjectNotFound,
                                                  process)
                                 );
                       continue;
                   }

                   // Write a debug message to the host that can be used when
                   // troubleshooting a problem. All debug messages will appear
                   // with the -Debug option.
                   message = String.Format(CultureInfo.CurrentCulture,
                                "Acquired name for pid {0} : \"{1}\"",
                                      process.Id, processName);
                   WriteDebug(message);

                   // Check to see if this process matches the current process
                   // name pattern. Skip this process if it does not.
                   if (!wildcard.IsMatch(processName))
                   {
                       continue;
                   }

                   // Stop the process.
                   SafeStopProcess(process);
               } // foreach (Process...
           } // foreach (string...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Helper Methods

       /// <summary>
       /// Safely stops a named process.  Used as standalone function
       /// to declutter the ProcessRecord method.
       /// </summary>
       /// <param name="process">The process to stop.</param>
       private void SafeStopProcess(Process process)
       {
           string processName = null;
           try
           {
               processName = process.ProcessName;
           }
           catch (Win32Exception e)
           {
               WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                 ErrorCategory.ObjectNotFound, process));
               return;
           }

           string message = null;

           // Confirm the operation first.
           // This is always false if the WhatIf parameter is specified.
           if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,
                    "{0} ({1})", processName, process.Id)))
           {
               return;
           }

           // Make sure that the user really wants to stop a critical
           // process that could possibly stop the computer.
           bool criticalProcess = criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

           if (criticalProcess && !force)
           {
               message = String.Format(CultureInfo.CurrentCulture,
                            "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                processName);

               // It is possible that ProcessRecord is called multiple
               // when objects are received as inputs from a pipeline.
               // So, to retain YesToAll and NoToAll input that the
               // user may enter across multiple calls to this
               // function, they are stored as private members of the
               // Cmdlet.
               if (!ShouldContinue(message, "Warning!",
                            ref yesToAll, ref noToAll))
               {
                   return;
               }
           } // if (criticalProcess...

           // Display a warning message if stopping a critical
           // process.
           if (criticalProcess)
           {
               message = String.Format(CultureInfo.CurrentCulture,
                            "Stopping the critical process \"{0}\".",
                                processName);
               WriteWarning(message);
           } // if (criticalProcess...

           try
           {
               // Stop the process.
               process.Kill();
           }
           catch (Exception e)
           {
               if ((e is Win32Exception) || (e is SystemException) ||
                   (e is InvalidOperationException))
               {
                   // This process could not be stopped so write
                   // a non-terminating error.
                   WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                    ErrorCategory.CloseError,
                                    process)
                              );
                   return;
               } // if ((e is...
               else throw;
           } // catch

           message = String.Format(CultureInfo.CurrentCulture,
                        "Stopped process \"{0}\", pid {1}.",
                              processName, process.Id);

           WriteVerbose(message);

           // If the PassThru parameter is specified,
           // return the terminated process to the pipeline.
           if (passThru)
           {
               message = String.Format(CultureInfo.CurrentCulture,
                            "Writing process \"{0}\" to pipeline",
                                processName);
               WriteDebug(message);
               WriteObject(process);
           } // if (passThru...
       } // SafeStopProcess

       #endregion Helper Methods

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of the critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
} // namespace Microsoft.Samples.PowerShell.Commands
```

## <a name="see-also"></a><span data-ttu-id="ba651-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba651-129">See Also</span></span>

[<span data-ttu-id="ba651-130">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ba651-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
