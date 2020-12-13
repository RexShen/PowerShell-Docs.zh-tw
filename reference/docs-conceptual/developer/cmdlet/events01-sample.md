---
ms.date: 09/13/2016
ms.topic: reference
title: Events01 範例
description: Events01 範例
ms.openlocfilehash: ed8b7903537504609602e27693351847d322f904
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390400"
---
# <a name="events01-sample"></a><span data-ttu-id="d6867-103">Events01 範例</span><span class="sxs-lookup"><span data-stu-id="d6867-103">Events01 Sample</span></span>

<span data-ttu-id="d6867-104">這個範例會示範如何建立 Cmdlet，讓使用者註冊 [FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="d6867-104">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="d6867-105">使用此 Cmdlet 時，使用者可以在特定目錄下建立檔案時，註冊要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="d6867-105">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="d6867-106">此範例會衍生自 [ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 基類。</span><span class="sxs-lookup"><span data-stu-id="d6867-106">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="d6867-107">如何使用 Visual Studio 來建立範例。</span><span class="sxs-lookup"><span data-stu-id="d6867-107">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="d6867-108">安裝 Windows PowerShell 2.0 SDK 之後，請流覽至 Events01 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d6867-108">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="d6867-109">預設位置為 `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`。</span><span class="sxs-lookup"><span data-stu-id="d6867-109">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="d6867-110">按兩下方案 ( .sln) 檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="d6867-110">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="d6867-111">這會在 Microsoft Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="d6867-111">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="d6867-112">在 [建置] 功能表中，選取 [建置方案]。</span><span class="sxs-lookup"><span data-stu-id="d6867-112">In the **Build** menu, select **Build Solution**.</span></span> <span data-ttu-id="d6867-113">範例的程式庫會建立在預設 `\bin` 或 `\bin\debug` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d6867-113">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="d6867-114">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="d6867-114">How to run the sample</span></span>

1. <span data-ttu-id="d6867-115">建立下列模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="d6867-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="d6867-116">將範例的程式庫檔案複製到模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="d6867-116">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="d6867-117">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d6867-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="d6867-118">執行下列命令，以將 Cmdlet 載入 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="d6867-118">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="d6867-119">使用 Register-FileSystemEvent Cmdlet 註冊在臨時目錄下建立檔案時，將會寫入訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="d6867-119">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="d6867-120">在臨時目錄下建立檔案，並請注意， () 顯示訊息時，就會執行此動作。</span><span class="sxs-lookup"><span data-stu-id="d6867-120">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="d6867-121">這是依照下列步驟所產生的範例輸出。</span><span class="sxs-lookup"><span data-stu-id="d6867-121">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="d6867-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="d6867-122">Requirements</span></span>

<span data-ttu-id="d6867-123">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="d6867-123">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d6867-124">示範</span><span class="sxs-lookup"><span data-stu-id="d6867-124">Demonstrates</span></span>

<span data-ttu-id="d6867-125">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="d6867-125">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="d6867-126">如何撰寫事件註冊的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6867-126">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="d6867-127">Cmdlet 衍生自 [ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 類別，其提供 Cmdlet 通用參數的支援， `Register-*Event` 。</span><span class="sxs-lookup"><span data-stu-id="d6867-127">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span> <span data-ttu-id="d6867-128">衍生自 [ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 的 Cmdlet 只需要定義其特定參數，並覆寫 `GetSourceObject` 和 `GetSourceObjectEventName` 抽象方法。</span><span class="sxs-lookup"><span data-stu-id="d6867-128">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="d6867-129">範例</span><span class="sxs-lookup"><span data-stu-id="d6867-129">Example</span></span>

<span data-ttu-id="d6867-130">這個範例會示範如何註冊 [FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="d6867-130">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

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
        /// Deleted, Disposed, Error, and Renamed. Check the documentation of
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

## <a name="see-also"></a><span data-ttu-id="d6867-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6867-131">See Also</span></span>

[<span data-ttu-id="d6867-132">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6867-132">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
