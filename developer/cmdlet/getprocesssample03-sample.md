---
title: GetProcessSample03 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068040"
---
# <a name="getprocesssample03-sample"></a>GetProcessSample03 範例

此範例示範如何實作的 cmdlet，擷取本機電腦上的處理程序。 它提供`Name`可以接受來自管線的物件或從屬性名稱是參數名稱與相同物件的屬性值的參數。 這個指令程式是一個簡化的版的`Get-Process`Windows PowerShell 2.0 所提供的 cmdlet。

## <a name="how-to-build-the-sample-using-visual-studio"></a>如何使用 Visual Studio 建置範例。

1. 安裝 Windows PowerShell 2.0 sdk，瀏覽至 GetProcessSample03 資料夾。 預設位置是 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03。

2. 按兩下方案 (.sln) 檔案的圖示。 這是在 Visual Studio 中開啟範例專案。

3. 在 **建置**功能表上，選取**建置方案**。

    如需範例程式庫將建置的預設 \bin 或 \bin\debug 資料夾中。

### <a name="how-to-run-the-sample"></a>如何執行範例

1. 建立下列的模組資料夾：

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. 將範例組件複製到模組資料夾中。

3. 啟動 Windows PowerShell。

4. 執行下列命令，以將組件載入 Windows PowerShell:

    `Import-module getprossessample03`

5. 執行下列命令來執行 cmdlet:

    `get-proc`

## <a name="requirements"></a>需求

這個範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

此範例示範下列項目。

- 宣告 cmdlet 類別使用 Cmdlet 屬性。

- 宣告 cmdlet 參數使用的參數屬性。

- 指定參數的位置。

- 指定此參數只接受從管線輸入。 輸入可以取自物件或物件的屬性名稱為參數名稱相同的屬性的值。

- 宣告參數輸入的驗證屬性。

## <a name="example"></a>範例

此範例示範如何實作的 Get-proc cmdlet，其中包含`Name`接受來自管線的輸入參數。

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

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
