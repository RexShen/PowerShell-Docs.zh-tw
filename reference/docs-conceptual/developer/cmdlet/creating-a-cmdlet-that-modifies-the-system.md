---
title: 建立可修改系統的 Cmdlet |Microsoft Docs
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
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365757"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>建立可修改系統的 Cmdlet

有時候，Cmdlet 必須修改系統的執行狀態，而不只是 Windows PowerShell 執行時間的狀態。 在這些情況下，Cmdlet 應該會讓使用者有機會確認是否要進行變更。

若要支援確認，Cmdlet 必須執行兩項動作。

- 宣告此 Cmdlet 會在您指定[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性時，藉由將 SupportsShouldProcess 關鍵字設定為 `true`，來支援確認。

- 執行 Cmdlet 時，請呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) （如下列範例所示）：。

藉由支援確認，Cmdlet 會公開 Windows PowerShell 所提供的 @no__t 0 和 @no__t 1 參數，同時也符合 Cmdlet 的開發指導方針（如需 Cmdlet 開發指導方針的詳細資訊，請參閱[Cmdlet開發指導方針](./cmdlet-development-guidelines.md)）。

## <a name="changing-the-system"></a>變更系統

「變更系統」的動作是指任何可能變更 Windows PowerShell 外部系統狀態的 Cmdlet。 例如，停止處理常式、啟用或停用使用者帳戶，或將資料列加入至資料庫資料表，全都會變更應該確認的系統。 相反地，讀取資料或建立暫時性連線的作業並不會變更系統，而且通常不需要確認。 對於其效果限制在 Windows PowerShell 執行時間內部的動作（例如 `set-variable`），也不需要確認。 可能或可能不會進行持續性變更的 Cmdlet 應該宣告 `SupportsShouldProcess`，並且只在即將進行持續性變更時，才呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 。

> [!NOTE]
> ShouldProcess 確認僅適用于 Cmdlet。 如果命令或腳本藉由直接呼叫 .NET 方法或屬性來修改系統的執行狀態，或在 Windows PowerShell 外部呼叫應用程式，則無法使用這種形式的確認。

## <a name="the-stopproc-cmdlet"></a>StopProc Cmdlet

本主題描述的停止程式 Cmdlet 會嘗試停止使用 Get-Proc Cmdlet 抓取的進程（如[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)所述）。

## <a name="defining-the-cmdlet"></a>定義 Cmdlet

Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。 因為您要撰寫 Cmdlet 來變更系統，所以應該據以命名。 此 Cmdlet 會停止系統進程，因此此處選擇的動詞名稱是 "Stop" （由[Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別所定義），其名詞為 "Proc"，表示 Cmdlet 會停止處理常式。 如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。

以下是這個 Stop-Proc Cmdlet 的類別定義。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

請注意，在[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)宣告中，`SupportsShouldProcess` attribute 關鍵字會設定為 `true`，讓 Cmdlet 能夠呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和，[來執行指令程式。ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的.。 若未設定此關鍵字，使用者將無法使用 `Confirm` 和 @no__t 1 參數。

### <a name="extremely-destructive-actions"></a>極具破壞性的動作

某些作業是非常破壞性的，例如重新格式化使用中的硬碟磁碟分割。 在這些情況下，Cmdlet 應該在宣告[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性時，設定 `ConfirmImpact` @ no__t-1 @ no__t-2。 此設定會強制 Cmdlet 要求使用者確認，即使使用者尚未指定 `Confirm` 參數也一樣。 不過，Cmdlet 開發人員應該避免只有可能會破壞性的作業（例如，刪除使用者帳戶）超 `ConfirmImpact`。 請記住，如果 `ConfirmImpact` 設定為[ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**。

同樣地，某些作業不太可能會成為破壞性，雖然它們在理論上會修改 Windows PowerShell 外部系統的執行狀態。 這類 Cmdlet 可以將 `ConfirmImpact` 設定為[Confirmimpact。](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0) 這會略過使用者要求確認僅限中度影響和高影響作業的確認要求。

## <a name="defining-parameters-for-system-modification"></a>定義系統修改的參數

本節說明如何定義 Cmdlet 參數，包括支援系統修改所需的參數。 如果您需要定義參數的一般資訊，請參閱[新增處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)。

Stop-Proc Cmdlet 會定義三個參數： `Name`、`Force` 和 `PassThru`。

@No__t-0 參數會對應至處理常式輸入物件的 `Name` 屬性。 請注意，此範例中的 `Name` 參數是強制性的，因為如果 Cmdlet 沒有已命名的進程可停止，就會失敗。

@No__t-0 參數可讓使用者覆寫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的呼叫。 事實上，任何呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的 Cmdlet 都應該有一個 `Force` 參數，因此當指定 `Force` 時，Cmdlet 會略過[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的呼叫，而將並繼續操作。 請注意，這不會影響[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的呼叫。

@No__t-0 參數可讓使用者指出 Cmdlet 是否透過管線傳遞輸出物件，在此情況下，在處理常式停止後。 請注意，此參數會系結至 Cmdlet 本身，而不是系結至輸入物件的屬性。

以下是 Stop-Proc Cmdlet 的參數宣告。

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

Cmdlet 必須覆寫輸入處理方法。 下列程式碼說明範例 Stop-Proc Cmdlet 中使用的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)覆寫。 這個方法會針對每個要求的進程名稱，確保進程不是特殊進程、嘗試停止進程，然後在指定 `PassThru` 參數時傳送輸出物件。

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

您的 Cmdlet 的輸入處理方法應呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，以在變更（例如刪除檔案）之前確認作業執行，以進行系統的執行中狀態。 這可讓 Windows PowerShell 執行時間在 shell 中提供正確的「WhatIf」和「確認」行為。

> [!NOTE]
> 如果 Cmdlet 所支援的指令程式應處理且無法進行[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫，使用者可能會意外地修改系統。

[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的呼叫會將要變更的資源名稱傳送給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數列入決定應該會向使用者顯示。

下列範例會示範如何呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ，從範例停止執行 Cmdlet 的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中進行的覆寫，以進行。

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>呼叫 ShouldContinue 方法

對[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的呼叫會將次要訊息傳送給使用者。 此呼叫是在呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)之後，如果 `Force` 參數未設定為 `true`，則會傳回 `true`。 然後，使用者可以提供意見反應，以指出是否應該繼續操作。 您的 Cmdlet 會呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)做為額外檢查是否有潛在危險的系統修改，或當您想要為使用者提供「全部都是」和「無」所有選項時。

下列範例會示範如何呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ，從範例停止執行 Cmdlet 的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中進行的覆寫，以進行。

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

## <a name="stopping-input-processing"></a>停止輸入處理

進行系統修改之 Cmdlet 的輸入處理方法必須提供一種方法來停止處理輸入。 在此停止處理指示程式的情況下，會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法呼叫至 System.servicemodel. Process.......[進程. Kill *](/dotnet/api/System.Diagnostics.Process.Kill)方法。 因為 `PassThru` 參數設定為 `true`，所以[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)也會呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) ，將處理常式物件傳送至管線，以將進程物件。

## <a name="code-sample"></a>程式碼範例

如需完整C#的範例程式碼，請參閱[StopProcessSample01 範例](./stopprocesssample01-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

Windows PowerShell 會使用 .Net 物件在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊它。 如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 已向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。 以下是測試停止程式 Cmdlet 的數個測試。 如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 啟動 Windows PowerShell，並使用 Stop-Proc Cmdlet 來停止處理，如下所示。 因為 Cmdlet 會將 `Name` 參數指定為強制性，所以 Cmdlet 會查詢參數。

    ```powershell
    PS> stop-proc
    ```

下列輸出隨即出現。

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- 現在讓我們使用 Cmdlet 來停止名為 "NOTEPAD" 的進程。 Cmdlet 會要求您確認此動作。

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

- 如所示使用停止程式，以停止名為 "WINLOGON" 的關鍵進程。 系統會提示您執行此動作，並對其發出警告，因為這會導致作業系統重新開機。

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

- 現在讓我們嘗試停止 WINLOGON 進程，而不收到警告。 請注意，此命令專案會使用 `Force` 參數來覆寫警告。

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

[新增可處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)

[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)