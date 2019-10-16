---
title: Events01 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369737"
---
# <a name="events01-sample"></a><span data-ttu-id="52892-102">Events01 範例</span><span class="sxs-lookup"><span data-stu-id="52892-102">Events01 Sample</span></span>

<span data-ttu-id="52892-103">這個範例會示範如何建立 Cmdlet，讓使用者註冊[FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="52892-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="52892-104">使用此 Cmdlet 時，使用者可以註冊在特定目錄下建立檔案時要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="52892-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="52892-105">這個範例是衍生自[自 objecteventregistrationbase Cmdlet](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基類。</span><span class="sxs-lookup"><span data-stu-id="52892-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="52892-106">如何使用 Visual Studio 建立範例。</span><span class="sxs-lookup"><span data-stu-id="52892-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="52892-107">安裝 Windows PowerShell 2.0 SDK 之後，流覽至 Events01 資料夾。</span><span class="sxs-lookup"><span data-stu-id="52892-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="52892-108">預設位置為 `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`。</span><span class="sxs-lookup"><span data-stu-id="52892-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="52892-109">按兩下方案（.sln）檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="52892-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="52892-110">這會在 Microsoft Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="52892-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="52892-111">在 [**建立**] 功能表中，選取 [**建立方案**]。</span><span class="sxs-lookup"><span data-stu-id="52892-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="52892-112">範例的程式庫會建立在預設 `\bin` 或 @no__t 1 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="52892-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="52892-113">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="52892-113">How to run the sample</span></span>

1. <span data-ttu-id="52892-114">建立下列模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="52892-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="52892-115">將範例的程式庫檔案複製到模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="52892-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="52892-116">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="52892-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="52892-117">執行下列命令，將 Cmdlet 載入 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="52892-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="52892-118">使用 FileSystemEvent 指令程式註冊在臨時目錄下建立檔案時，將會寫入訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="52892-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="52892-119">在 TEMP 目錄下建立檔案，並請注意動作會執行（顯示訊息）。</span><span class="sxs-lookup"><span data-stu-id="52892-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="52892-120">這是依照下列步驟所產生的範例輸出。</span><span class="sxs-lookup"><span data-stu-id="52892-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="52892-121">需求</span><span class="sxs-lookup"><span data-stu-id="52892-121">Requirements</span></span>

<span data-ttu-id="52892-122">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="52892-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="52892-123">演示</span><span class="sxs-lookup"><span data-stu-id="52892-123">Demonstrates</span></span>

<span data-ttu-id="52892-124">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="52892-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="52892-125">如何撰寫事件註冊的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="52892-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="52892-126">此 Cmdlet 衍生自[自 objecteventregistrationbase Cmdlet](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)類別，可提供 `Register-*Event` Cmdlet 通用的參數支援。</span><span class="sxs-lookup"><span data-stu-id="52892-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="52892-127">衍生自[自 objecteventregistrationbase Cmdlet](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)的 Cmdlet 只需要定義其特定參數，並覆寫 `GetSourceObject` 和 @no__t 2 抽象方法。</span><span class="sxs-lookup"><span data-stu-id="52892-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="52892-128">範例</span><span class="sxs-lookup"><span data-stu-id="52892-128">Example</span></span>

<span data-ttu-id="52892-129">這個範例示範如何註冊[FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="52892-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="52892-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52892-130">See Also</span></span>

[<span data-ttu-id="52892-131">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="52892-131">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)