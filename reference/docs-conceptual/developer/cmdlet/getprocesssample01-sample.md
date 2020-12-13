---
ms.date: 09/13/2016
ms.topic: reference
title: GetProcessSample01 範例
description: GetProcessSample01 範例
ms.openlocfilehash: 159c277d17a8551d2b5c52377a230babacafc9ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652764"
---
# <a name="getprocesssample01-sample"></a>GetProcessSample01 範例

此範例示範如何執行可在本機電腦上抓取進程的 Cmdlet。 此 Cmdlet 是 `Get-Process` Windows PowerShell 2.0 提供的 Cmdlet 簡化版本。

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>如何使用 Visual Studio 來建立範例。

1. 安裝 Windows PowerShell 2.0 SDK 之後，請流覽至 >getprocesssample01 資料夾。 預設位置為 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01。

2. 按兩下方案 ( .sln) 檔案的圖示。 這會在 Microsoft Visual Studio 中開啟範例專案。

3. 在 [建置] 功能表中，選取 [建置方案]。

  範例的程式庫會建立在預設的 \bin 或 \bin\debug 資料夾中。

### <a name="how-to-run-the-sample"></a>如何執行範例

1. 開啟命令提示字元視窗。

2. 流覽至包含範例 .dll 檔案的目錄。

3. 執行 installutil.exe "GetProcessSample01.dll"。

4. 啟動 Windows PowerShell。

5. 執行下列命令，將嵌入式管理單元新增至 shell。

   `Add-PSSnapin GetProcPSSnapIn01`

6. 輸入下列命令來執行 Cmdlet。 `get-proc`

   `get-proc`

   這是遵循下列步驟所產生的範例輸出。

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

## <a name="requirements"></a>規格需求

此範例需要 Windows PowerShell 1.0 或更新版本。

## <a name="demonstrates"></a>示範

這個範例會示範下列各項。

- 建立基本的範例 Cmdlet。

- 使用 Cmdlet 屬性定義 Cmdlet 類別。

- 建立適用于 Windows PowerShell 1.0 和 Windows PowerShell 2.0 的嵌入式管理單元。 後續的範例會使用模組（而不是嵌入式管理單元），因此需要 Windows PowerShell 2.0。

## <a name="example"></a>範例

此範例說明如何建立簡單的 Cmdlet 和其嵌入式管理單元。

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

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
