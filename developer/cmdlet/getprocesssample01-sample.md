---
title: GetProcessSample01 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068057"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="6fe9c-102">GetProcessSample01 範例</span><span class="sxs-lookup"><span data-stu-id="6fe9c-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="6fe9c-103">此範例示範如何實作的 cmdlet，擷取本機電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="6fe9c-104">這個指令程式是一個簡化的版的`Get-Process`Windows PowerShell 2.0 所提供的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="6fe9c-105">如何使用 Visual Studio 建置範例。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="6fe9c-106">安裝 Windows PowerShell 2.0 sdk，瀏覽至 GetProcessSample01 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="6fe9c-107">預設位置是 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="6fe9c-108">按兩下方案 (.sln) 檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="6fe9c-109">這是 Microsoft Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="6fe9c-110">在 **建置**功能表上，選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="6fe9c-111">如需範例程式庫將建置的預設 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="6fe9c-112">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="6fe9c-112">How to run the sample</span></span>

1. <span data-ttu-id="6fe9c-113">開啟命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="6fe9c-114">瀏覽至包含範例.dll 檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="6fe9c-115">執行 installutil"GetProcessSample01.dll 」。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="6fe9c-116">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="6fe9c-117">執行下列命令以新增嵌入式管理單元到殼層。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="6fe9c-118">輸入下列命令來執行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="6fe9c-119">這是範例輸出所產生的下列步驟。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-119">This is a sample output that results from following these steps.</span></span>

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a><span data-ttu-id="6fe9c-120">需求</span><span class="sxs-lookup"><span data-stu-id="6fe9c-120">Requirements</span></span>

<span data-ttu-id="6fe9c-121">這個範例需要 Windows PowerShell 1.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6fe9c-122">示範</span><span class="sxs-lookup"><span data-stu-id="6fe9c-122">Demonstrates</span></span>

<span data-ttu-id="6fe9c-123">此範例示範下列項目。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="6fe9c-124">建立基本的範例指令程式。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="6fe9c-125">使用 Cmdlet 屬性，以定義 cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="6fe9c-126">建立一個嵌入式管理單元，可搭配 Windows PowerShell 1.0 和 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="6fe9c-127">後續的範例使用而不是嵌入式管理單元模組，因此他們需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="6fe9c-128">範例</span><span class="sxs-lookup"><span data-stu-id="6fe9c-128">Example</span></span>

<span data-ttu-id="6fe9c-129">此範例示範如何建立簡單的 cmdlet 和其嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="6fe9c-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a><span data-ttu-id="6fe9c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fe9c-130">See Also</span></span>

[<span data-ttu-id="6fe9c-131">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6fe9c-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)