---
title: 將使用者訊息新增至您的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 1e048f6ae94ac226218c18c8f8f7590a4db26226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370067"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>新增使用者訊息到您的 Cmdlet

Cmdlet 可以撰寫數種可由 Windows PowerShell 執行時間向使用者顯示的訊息。 這些訊息包含下列類型：

- 包含一般使用者資訊的詳細訊息。

- 包含疑難排解資訊的偵錯工具訊息。

- 包含通知的警告訊息，指出 Cmdlet 即將執行可能會產生非預期結果的作業。

- 進度報表訊息，其中包含在執行需要很長時間的作業時，Cmdlet 已完成多少工作的相關資訊。

您的 Cmdlet 可以寫入的訊息數目，或 Cmdlet 所寫入的訊息類型沒有任何限制。 每個訊息的撰寫方式是從 Cmdlet 的輸入處理方法中進行特定的呼叫。

## <a name="defining-the-cmdlet"></a>定義 Cmdlet

Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。 任何類型的 Cmdlet 都可以從其輸入處理方法寫入使用者通知;因此，一般而言，您可以使用指示 Cmdlet 執行之系統修改的任何動詞來命名此 Cmdlet。 如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。

停止處理器 Cmdlet 是設計來修改系統;因此，.NET 類別的[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)宣告必須包含 `SupportsShouldProcess` 屬性關鍵字，並設定為 `true`。

下列程式碼是這個停止進程 Cmdlet 類別的定義。 如需有關此定義的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>定義系統修改的參數

Stop-Proc Cmdlet 會定義三個參數： `Name`、`Force` 和 `PassThru`。 如需定義這些參數的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

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

您的 Cmdlet 必須覆寫輸入處理方法，但通常會是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 這個 Stop-Proc Cmdlet 會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)輸入處理方法。 在這種停止進程 Cmdlet 的執行過程中，會呼叫來寫入詳細訊息、debug 訊息和警告訊息。

> [!NOTE]
> 如需有關此方法如何呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的詳細資訊，請參閱[建立可修改系統](./creating-a-cmdlet-that-modifies-the-system.md)的指令程式（Cmdlet）。

## <a name="writing-a-verbose-message"></a>撰寫詳細訊息

[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法是用來撰寫與特定錯誤狀況無關的一般使用者層級資訊。 然後，系統管理員可以使用該資訊繼續處理其他命令。 此外，使用此方法所撰寫的任何資訊都應該視需要當地語系化。

下列來自這個 Stop-Proc Cmdlet 的程式碼會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中，顯示兩次[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的呼叫，。

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>撰寫 Debug 訊息

[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法是用來撰寫可用於疑難排解 Cmdlet 作業的「偵錯工具」（debug）訊息。 呼叫是從輸入處理方法進行。

> [!NOTE]
> Windows PowerShell 也會定義同時提供詳細資訊和偵錯工具資訊的 `Debug` 參數。 如果您的 Cmdlet 支援此參數，則不需要在呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)的相同程式碼中呼叫 System.web. [WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)..。

下列兩個來自 sample WriteDebug 方法的程式碼區段會從 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法的覆寫中，顯示對 [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 方法的呼叫。」（來自）。

此 debug 訊息會在呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)之前立即寫入。

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

此 debug 訊息會在呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)之前立即寫入。

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell 會自動將[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)呼叫路由至追蹤基礎結構和 Cmdlet。 這可讓方法呼叫追蹤至裝載應用程式、檔案或偵錯工具，而不需要在 Cmdlet 內執行任何額外的開發工作。 下列命令列專案會實行追蹤作業。

**PS > 追蹤-運算式停止進程-檔案進程 .log-命令停止-進程記事本**

## <a name="writing-a-warning-message"></a>撰寫警告訊息

當指令程式即將執行可能會產生非預期結果的作業時（例如，覆寫唯讀檔案），會使用[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法來撰寫警告。

下列來自範例 Stop-Proc Cmdlet 的程式碼會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中，顯示對[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法所做的呼叫，。

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>撰寫進度訊息

當 Cmdlet 作業需要很長的時間才能完成時，會使用[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)來寫入進度訊息。 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)的呼叫會將傳送至裝載應用程式的[Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord)物件傳遞給使用者，以供呈現給使用者使用。

> [!NOTE]
> 這個停止進程 Cmdlet 不會包含[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法的呼叫（call）。

下列程式碼範例是由嘗試複製專案的 Cmdlet 所撰寫的進度訊息。

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>程式碼範例

如需完整C#的範例程式碼，請參閱[StopProcessSample02 範例](./stopprocesssample02-sample.md)。

## <a name="define-object-types-and-formatting"></a>定義物件類型和格式

Windows PowerShell 會使用 .NET 物件在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊它。 如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 已向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。 讓我們來測試範例的 Stop-Proc Cmdlet。 如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 下列命令列專案使用停止程式來停止名為 "NOTEPAD" 的進程、提供詳細語音總機，以及列印偵錯工具資訊。

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

下列輸出隨即出現。

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>另請參閱

[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何建立 Windows PowerShell Cmdlet](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
