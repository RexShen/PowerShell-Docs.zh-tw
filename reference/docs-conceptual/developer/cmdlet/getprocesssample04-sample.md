---
title: GetProcessSample04 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365707"
---
# <a name="getprocesssample04-sample"></a>GetProcessSample04 範例

這個範例示範如何執行可抓取本機電腦上處理常式的 Cmdlet。 如果在抓取進程時發生錯誤，就會產生非終止錯誤。 此 Cmdlet 是 Windows PowerShell 2.0 所提供的 `Get-Process` Cmdlet 的簡化版本。

## <a name="how-to-build-the-sample-using-visual-studio"></a>如何使用 Visual Studio 建立範例。

1. 安裝 Windows PowerShell 2.0 SDK 之後，流覽至 GetProcessSample04 資料夾。 預設位置為 C:\Program Files （x86） \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04。

2. 按兩下方案（.sln）檔案的圖示。 這會在 Visual Studio 中開啟範例專案。

3. 在 [**建立**] 功能表中，選取 [**建立方案**]。

    範例的程式庫會建立在預設的 \bin 或 \bin\debug 資料夾中。

### <a name="how-to-run-the-sample"></a>如何執行範例

1. 建立下列模組資料夾：

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. 將範例元件複製到模組資料夾。

3. 啟動 Windows PowerShell。

4. 執行下列命令，將元件載入 Windows PowerShell：

    `Import-module getprossessample04`

5. 執行下列命令來執行 Cmdlet：

    `get-proc`

## <a name="requirements"></a>需求

此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>演示

這個範例會示範下列各項。

- 使用 Cmdlet 屬性宣告 Cmdlet 類別。

- 使用參數屬性宣告 Cmdlet 參數。

- 指定參數的位置。

- 指定參數接受管線的輸入。 輸入可以從物件取得，或從屬性名稱與參數名稱相同之物件的屬性值。

- 宣告參數輸入的驗證屬性。

- 捕捉非終止錯誤，並將錯誤訊息寫入錯誤資料流程。

## <a name="example"></a>範例

這個範例示範如何建立 Cmdlet 來處理非終止錯誤，並將錯誤訊息寫入錯誤資料流程。

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

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
