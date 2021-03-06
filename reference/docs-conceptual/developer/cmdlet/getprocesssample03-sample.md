---
ms.date: 09/13/2016
ms.topic: reference
title: GetProcessSample03 範例
description: GetProcessSample03 範例
ms.openlocfilehash: 7827247238f3dad2018b55e396b73d1fa434eb97
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660722"
---
# <a name="getprocesssample03-sample"></a>GetProcessSample03 範例

此範例示範如何執行可在本機電腦上抓取進程的 Cmdlet。 它提供的 `Name` 參數可接受來自管線的物件，或屬性名稱與參數名稱相同之物件的屬性值。 此 Cmdlet 是 `Get-Process` Windows PowerShell 2.0 提供的簡化版 Cmdlet。

## <a name="how-to-build-the-sample-using-visual-studio"></a>如何使用 Visual Studio 建立範例。

1. 安裝 Windows PowerShell 2.0 SDK 之後，請流覽至 GetProcessSample03 資料夾。 預設位置為 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03。

2. 按兩下方案 ( .sln) 檔案的圖示。 這會在 Visual Studio 中開啟範例專案。

3. 在 [建置] 功能表中，選取 [建置方案]。

    範例的程式庫會建立在預設的 \bin 或 \bin\debug 資料夾中。

### <a name="how-to-run-the-sample"></a>如何執行範例

1. 建立下列模組資料夾：

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. 將範例元件複製到模組資料夾。

3. 啟動 Windows PowerShell。

4. 執行下列命令，將元件載入 Windows PowerShell：

    `Import-module getprossessample03`

5. 執行下列命令以執行 Cmdlet：

    `get-proc`

## <a name="requirements"></a>規格需求

此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

這個範例會示範下列各項。

- 使用 Cmdlet 屬性宣告 Cmdlet 類別。

- 使用參數屬性宣告 Cmdlet 參數。

- 指定參數的位置。

- 指定參數接受來自管線的輸入。 輸入可以從物件取得，或從屬性名稱與參數名稱相同的物件屬性取得值。

- 宣告參數輸入的驗證屬性。

## <a name="example"></a>範例

此範例示範 Get-Proc Cmdlet 的執行，其中包含 `Name` 可接受管線輸入的參數。

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
