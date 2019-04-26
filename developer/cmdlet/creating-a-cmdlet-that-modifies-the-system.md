---
title: 建立 Cmdlet 會修改系統 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068422"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>建立可修改系統的 Cmdlet

有時候指令程式必須修改系統，而不只是 Windows PowerShell 執行階段狀態的執行狀態。 在這些情況下，此 cmdlet 應該允許使用者有機會確認要進行變更。

若要支援確認 cmdlet 必須做兩件事。

- 此 cmdlet 會支援確認，當您指定的宣告[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性設為 SupportsShouldProcess 關鍵字`true`。

- 呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) （如下列範例所示），此指令程式執行期間。

藉由支援確認，cmdlet 會公開`Confirm`和`WhatIf`所提供的 Windows PowerShell，又能滿足的開發指導方針 cmdlet 的參數 （如需有關 cmdlet 開發指導方針的詳細資訊，請參閱[Cmdlet 開發指導方針](./cmdlet-development-guidelines.md)。)。

## <a name="changing-the-system"></a>變更系統

「 變更系統 」 動作是指任何可能會變更系統狀態的外部 Windows PowerShell 的 cmdlet。 例如，停止處理序，啟用或停用使用者帳戶，或加入至資料庫資料表的資料列都應該確認系統的所有變更。 相反地，作業讀取資料，或建立暫時性的連線不會變更系統，和通常不需要確認。 其效果僅限於內部，Windows PowerShell 執行階段中，這類的動作也不需要確認`set-variable`。 指令程式，可能或可能不會進行持續性的變更應該宣告`SupportsShouldProcess`並呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)只有他們即將進行持續性的變更。

> [!NOTE]
> ShouldProcess 確認僅適用於 cmdlet。 如果命令或指令碼修改系統的執行狀態，方法是直接呼叫.NET 方法或屬性，或呼叫應用程式在 Windows PowerShell 之外，將無法使用這種形式的確認。

## <a name="the-stopproc-cmdlet"></a>StopProc Cmdlet

本主題描述嘗試停止處理程序，可使用 Get-proc cmdlet 來擷取停止程序 cmdlet (中所述[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))。

在本節中的主題包括下列各項：

- [定義此指令程式](#Defining-the-Cmdlet)

- [修改系統定義的參數](#Defining-Parameters-for-System-Modification)

- [覆寫輸入處理方法](#Overriding-an-Input-Processing-Method)

- [呼叫 ShouldProcess 方法](#Calling-the-ShouldProcess-Method)

- [呼叫 ShouldContinue 方法](#Calling-the-ShouldContinue-Method)

- [正在停止的輸入的處理](#Stopping-Input-Processing)

- [程式碼範例](#Code-Sample)

- [定義物件類型和格式設定](#Defining-Object-Types-and-Formatting)

- [建置此指令程式](#Building-the-Cmdlet)

- [測試 Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>定義此指令程式

Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。 因為您正在撰寫的 cmdlet，來變更系統，它應該命名。 此 cmdlet 會停止系統處理序，所以在這裡選擇的指令動詞名稱是 「 停止 」，由[System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別，和名詞"Proc"，以指出此 cmdlet 會停止處理程序。 如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。

以下是這個處理序停止外指令程式的類別定義。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

請注意，在[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)宣告，`SupportsShouldProcess`屬性關鍵字設定為`true`若要啟用對進行呼叫 cmdlet [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。 這個關鍵字設定時，沒有`Confirm`和`WhatIf`參數不會提供給使用者。

### <a name="extremely-destructive-actions"></a>極度破壞性動作

有些作業是極度破壞性，例如重新格式化的作用中的硬碟磁碟分割。 在這些情況下，此 cmdlet 應該設定`ConfirmImpact`  =  `ConfirmImpact.High`宣告時[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性。 此設定會強制此 cmdlet 來要求使用者確認使用者尚未指定，即使`Confirm`參數。 不過，cmdlet 開發人員應避免過度使用`ConfirmImpact`為只可能破壞性，例如刪除使用者帳戶的作業。 請注意，如果`ConfirmImpact`設定為[System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High)。

同樣地，某些作業不太可能會破壞性的雖然他們不要理論上修改 Windows PowerShell 外部系統的執行狀態。 此類指令程式可以設定`ConfirmImpact`要[System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0)。 這將會略過確認要求已要求使用者確認只有中度影響和具有強烈影響的作業。

## <a name="defining-parameters-for-system-modification"></a>修改系統定義的參數

本章節描述如何定義 cmdlet 參數，包括所需的支援系統修改。 請參閱[加入參數，該程序的命令列輸入](./adding-parameters-that-process-command-line-input.md)如果您需要定義參數的一般資訊。

停止處理序的指令程式會定義三個參數： `Name`， `Force`，和`PassThru`。

`Name`參數會對應至`Name`處理程序的輸入物件的屬性。 請注意，`Name`在此範例中的參數是必要項目，為指令程式將會失敗，如果它沒有具名的處理序停止。

`Force`參數可讓使用者覆寫來呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。 事實上，任何 cmdlet，會呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)應有`Force`參數，讓當`Force`指定，此 cmdlet 會略過呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ，並繼續處理作業。 請注意這不會影響呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)。

`PassThru`參數可讓使用者指出是否 cmdlet 會傳遞輸出物件透過管線，在此情況下，停止處理程序之後。 請注意，此參數繫結至 cmdlet 本身而不是屬性的輸入物件。

以下是停止程序 cmdlet 的參數宣告。

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

此指令程式，必須覆寫輸入處理方法。 下列程式碼說明[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)範例停止程序 cmdlet 中使用的覆寫。 每個要求處理程序名稱，此方法可確保程序不是特殊的處理程序，嘗試停止處理程序，並接著會傳送輸出物件，如果`PassThru`指定參數。

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>呼叫 ShouldProcess 方法

輸入處理方法，您的指令程式應該呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)前進行確認執行作業 （例如，刪除檔案） 變更為執行中狀態的方法在系統中。 這可讓 Windows PowerShell 執行階段提供正確的 「 WhatIf 」 和 「 確認 」 行為，在殼層中。

> [!NOTE]
> 如果 cmdlet 可讓您指出它支援應該處理，並無法做出[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫時，使用者可能會意外地修改系統。

若要在呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)傳送給使用者，使用 Windows PowerShell 執行階段的任何命令列設定或喜好設定變數，請考慮變更資源的名稱在決定應該顯示給使用者。

下列範例示範呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)從的覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)範例中的方法停止處理序 cmdlet。

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>呼叫 ShouldContinue 方法

若要在呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法會將第二個訊息傳送給使用者。 此呼叫之後呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)會傳回`true`如果`Force`參數未設定為`true`。 接著，使用者可以提供意見反應，表示作業是否應該繼續。 您 cmdlet 會呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)為有潛在危險的系統修改，或想要提供給使用者的全部是和否-all 選項時的其他檢查。

下列範例示範呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)從的覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)範例中的方法停止處理序 cmdlet。

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>正在停止的輸入的處理

輸入處理方法的 cmdlet，可讓系統修改必須提供一種停止處理的輸入。 在此停止程序 cmdlet 的情況下進行呼叫，從[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法來[System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill)方法。 因為`PassThru`參數設定為`true`， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)也會呼叫[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)傳送管線處理程序物件。

## <a name="code-sample"></a>程式碼範例

完整C#程式碼範例，請參閱 < [StopProcessSample01 範例](./stopprocesssample01-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式設定

Windows PowerShell cmdlet 使用.Net 物件之間傳遞資訊。 因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。 如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>建置此指令程式

在實作之後的 cmdlet，它必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。 如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。 以下是測試停止程序 cmdlet 的數個測試。 如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 啟動 Windows PowerShell，並使用停止程序 cmdlet 來停止處理，如下所示。 因為 cmdlet 會指定`Name`為必要的參數，cmdlet 查詢參數。

    ```powershell
    PS> stop-proc
    ```

下列輸出隨即出現。

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- 現在讓我們使用 cmdlet 來停止名為"NOTEPAD"的處理序。 此 cmdlet 會要求您確認動作。

    ```powershell
    PS> stop-proc -Name notepad
    ```

下列輸出隨即出現。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 若要停止名為"WINLOGON 」 的重要程序使用停止程序所示。 您會出現提示，看到有關執行此動作，因為它會造成重新啟動作業系統的警告。

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

下列輸出隨即出現。

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- 讓我們現在試著停止 WINLOGON 處理程序，而不會收到一則警告。 請注意，此命令項目會使用`Force`參數來覆寫此警告。

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

下列輸出隨即出現。

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另請參閱

[加入處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)

[擴充物件類型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)