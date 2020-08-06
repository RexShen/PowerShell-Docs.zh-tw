---
title: GetProcessSample03 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 09df93792ab611e167279bc35755d8d6c28e7cf3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784209"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="66619-102">GetProcessSample03 範例</span><span class="sxs-lookup"><span data-stu-id="66619-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="66619-103">這個範例示範如何執行可抓取本機電腦上處理常式的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="66619-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="66619-104">它所提供的 `Name` 參數可接受來自管線的物件，或從屬性名稱與參數名稱相同的物件屬性值。</span><span class="sxs-lookup"><span data-stu-id="66619-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="66619-105">此 Cmdlet 是 `Get-Process` Windows PowerShell 2.0 所提供之 Cmdlet 的簡化版本。</span><span class="sxs-lookup"><span data-stu-id="66619-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="66619-106">如何使用 Visual Studio 建立範例。</span><span class="sxs-lookup"><span data-stu-id="66619-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="66619-107">安裝 Windows PowerShell 2.0 SDK 之後，流覽至 GetProcessSample03 資料夾。</span><span class="sxs-lookup"><span data-stu-id="66619-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="66619-108">預設位置為 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03。</span><span class="sxs-lookup"><span data-stu-id="66619-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="66619-109">按兩下方案的圖示 ( .sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="66619-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="66619-110">這會在 Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="66619-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="66619-111">在 [建置]\*\*\*\* 功能表中，選取 [建置方案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66619-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="66619-112">範例的程式庫會建立在預設的 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="66619-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="66619-113">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="66619-113">How to run the sample</span></span>

1. <span data-ttu-id="66619-114">建立下列模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="66619-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="66619-115">將範例元件複製到模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="66619-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="66619-116">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="66619-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="66619-117">執行下列命令，將元件載入 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="66619-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="66619-118">執行下列命令來執行 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="66619-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="66619-119">需求</span><span class="sxs-lookup"><span data-stu-id="66619-119">Requirements</span></span>

<span data-ttu-id="66619-120">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="66619-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="66619-121">示範</span><span class="sxs-lookup"><span data-stu-id="66619-121">Demonstrates</span></span>

<span data-ttu-id="66619-122">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="66619-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="66619-123">使用 Cmdlet 屬性宣告 Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="66619-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="66619-124">使用參數屬性宣告 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="66619-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="66619-125">指定參數的位置。</span><span class="sxs-lookup"><span data-stu-id="66619-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="66619-126">指定參數接受管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="66619-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="66619-127">輸入可以從物件取得，或從屬性名稱與參數名稱相同之物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="66619-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="66619-128">宣告參數輸入的驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="66619-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="66619-129">範例</span><span class="sxs-lookup"><span data-stu-id="66619-129">Example</span></span>

<span data-ttu-id="66619-130">這個範例會示範如何執行包含 `Name` 接受管線輸入之參數的 Get Proc Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="66619-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="66619-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66619-131">See Also</span></span>

[<span data-ttu-id="66619-132">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="66619-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
