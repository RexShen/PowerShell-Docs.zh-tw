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
ms.openlocfilehash: 3edbcabeff0c8d84831823df11749d152b347566
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863334"
---
# <a name="events01-sample"></a><span data-ttu-id="bb99d-102">Events01 範例</span><span class="sxs-lookup"><span data-stu-id="bb99d-102">Events01 Sample</span></span>

<span data-ttu-id="bb99d-103">此範例示範如何建立所引發的事件可讓使用者註冊 cmdlet [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)。</span><span class="sxs-lookup"><span data-stu-id="bb99d-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="bb99d-104">使用此 cmdlet，使用者可以註冊的特定目錄下建立檔案時要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="bb99d-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="bb99d-105">此範例衍生自[Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基底類別。</span><span class="sxs-lookup"><span data-stu-id="bb99d-105">This sample derives from the [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="bb99d-106">如何使用 Visual Studio 建置範例。</span><span class="sxs-lookup"><span data-stu-id="bb99d-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="bb99d-107">安裝 Windows PowerShell 2.0 sdk，瀏覽至 Events01 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bb99d-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="bb99d-108">預設位置是 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01。</span><span class="sxs-lookup"><span data-stu-id="bb99d-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span></span>

2. <span data-ttu-id="bb99d-109">按兩下方案 (.sln) 檔案的圖示。</span><span class="sxs-lookup"><span data-stu-id="bb99d-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="bb99d-110">這是 Microsoft Visual Studio 中開啟範例專案。</span><span class="sxs-lookup"><span data-stu-id="bb99d-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="bb99d-111">在 **建置**功能表上，選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="bb99d-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="bb99d-112">如需範例程式庫將建置的預設 \bin 或 \bin\debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bb99d-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="bb99d-113">如何執行範例</span><span class="sxs-lookup"><span data-stu-id="bb99d-113">How to run the sample</span></span>

1. <span data-ttu-id="bb99d-114">建立下列的模組資料夾：</span><span class="sxs-lookup"><span data-stu-id="bb99d-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="bb99d-115">將此範例的程式庫檔案複製到模組資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bb99d-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="bb99d-116">啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bb99d-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="bb99d-117">執行下列命令以載入 Windows PowerShell cmdlet:</span><span class="sxs-lookup"><span data-stu-id="bb99d-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="bb99d-118">您可以使用 暫存器 FileSystemEvent cmdlet 來註冊 TEMP 目錄下建立檔案時，會寫入一則訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="bb99d-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="bb99d-119">TEMP 目錄下建立檔案，並記下會執行此動作 （訊息會顯示）。</span><span class="sxs-lookup"><span data-stu-id="bb99d-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="bb99d-120">這是依照下列步驟所產生的範例輸出。</span><span class="sxs-lookup"><span data-stu-id="bb99d-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="bb99d-121">需求</span><span class="sxs-lookup"><span data-stu-id="bb99d-121">Requirements</span></span>

<span data-ttu-id="bb99d-122">這個範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="bb99d-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bb99d-123">示範</span><span class="sxs-lookup"><span data-stu-id="bb99d-123">Demonstrates</span></span>

<span data-ttu-id="bb99d-124">此範例示範下列項目。</span><span class="sxs-lookup"><span data-stu-id="bb99d-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="bb99d-125">如何撰寫事件註冊 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb99d-125">How to write a cmdlet for event registration.</span></span> <span data-ttu-id="bb99d-126">此 cmdlet 會衍生自[Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)類別，可提供通用參數的支援新增到暫存器-\* 事件 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb99d-126">The cmdlet derives from the [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the Register-\*Event cmdlets.</span></span> <span data-ttu-id="bb99d-127">從衍生的 Cmdlet [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)只需要定義其特定的參數，並覆寫`GetSourceObject`和`GetSourceObjectEventName`抽象方法。</span><span class="sxs-lookup"><span data-stu-id="bb99d-127">Cmdlets that are derived from [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="bb99d-128">範例</span><span class="sxs-lookup"><span data-stu-id="bb99d-128">Example</span></span>

<span data-ttu-id="bb99d-129">此範例示範如何註冊所引發的事件[System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="bb99d-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bb99d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb99d-130">See Also</span></span>

[<span data-ttu-id="bb99d-131">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bb99d-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)