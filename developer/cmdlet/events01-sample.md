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
# <a name="events01-sample"></a>Events01 範例

此範例示範如何建立所引發的事件可讓使用者註冊 cmdlet [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)。 使用此 cmdlet，使用者可以註冊的特定目錄下建立檔案時要執行的動作。 此範例衍生自[Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基底類別。

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>如何使用 Visual Studio 建置範例。

1. 安裝 Windows PowerShell 2.0 sdk，瀏覽至 Events01 資料夾。 預設位置是 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01。

2. 按兩下方案 (.sln) 檔案的圖示。 這是 Microsoft Visual Studio 中開啟範例專案。

3. 在 **建置**功能表上，選取**建置方案**。

    如需範例程式庫將建置的預設 \bin 或 \bin\debug 資料夾中。

### <a name="how-to-run-the-sample"></a>如何執行範例

1. 建立下列的模組資料夾：

    `[user]/documents/windowspowershell/modules/events01`

2. 將此範例的程式庫檔案複製到模組資料夾中。

3. 啟動 Windows PowerShell。

4. 執行下列命令以載入 Windows PowerShell cmdlet:

    ```powershell
    import-module events01
    ```

5. 您可以使用 暫存器 FileSystemEvent cmdlet 來註冊 TEMP 目錄下建立檔案時，會寫入一則訊息的動作。

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. TEMP 目錄下建立檔案，並記下會執行此動作 （訊息會顯示）。

這是依照下列步驟所產生的範例輸出。

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

## <a name="requirements"></a>需求

這個範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

此範例示範下列項目。

- 如何撰寫事件註冊 cmdlet。 此 cmdlet 會衍生自[Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)類別，可提供通用參數的支援新增到暫存器-* 事件 cmdlet。 從衍生的 Cmdlet [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)只需要定義其特定的參數，並覆寫`GetSourceObject`和`GetSourceObjectEventName`抽象方法。

## <a name="example"></a>範例

此範例示範如何註冊所引發的事件[System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx)。

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

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)