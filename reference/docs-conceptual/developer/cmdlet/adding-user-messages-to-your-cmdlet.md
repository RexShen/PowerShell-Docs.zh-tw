---
ms.date: 09/13/2016
ms.topic: reference
title: 新增使用者訊息到您的 Cmdlet
description: 新增使用者訊息到您的 Cmdlet
ms.openlocfilehash: de6fcc093af1d01287eed1eb8cc7b81cf5d2fdd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668332"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>新增使用者訊息到您的 Cmdlet

Cmdlet 可以撰寫數種可由 Windows PowerShell 執行時間向使用者顯示的訊息。 這些訊息包含下列類型：

- 包含一般使用者資訊的詳細資訊訊息。

- 包含疑難排解資訊的訊息。

- 警告訊息，其中包含 Cmdlet 即將執行的作業可能會產生非預期結果的通知。

- 進度報告訊息，其中包含在執行需要很長時間的作業時，Cmdlet 已完成多少工作的相關資訊。

您的 Cmdlet 可以寫入的訊息數目，或您的 Cmdlet 所寫入的訊息類型沒有任何限制。 每個訊息都是藉由在 Cmdlet 的輸入處理方法內進行特定呼叫來撰寫。

## <a name="defining-the-cmdlet"></a>定義 Cmdlet

Cmdlet 建立的第一個步驟，一律會命名 Cmdlet 並宣告可執行 Cmdlet 的 .NET 類別。 任何種類的 Cmdlet 都可以從其輸入處理方法寫入使用者通知;因此，一般而言，您可以使用任何指示 Cmdlet 所執行之系統修改的動詞來命名此 Cmdlet。 如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱 [Cmdlet 動詞命令名稱](./approved-verbs-for-windows-powershell-commands.md)。

Stop-Proc Cmdlet 是設計來修改系統;因此，.NET 類別的 [CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 宣告必須包含 `SupportsShouldProcess` attribute 關鍵字，並設定為 `true` 。

下列程式碼是此 Stop-Proc Cmdlet 類別的定義。 如需有關此定義的詳細資訊，請參閱 [建立修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>定義修改系統的參數

Stop-Proc Cmdlet 會定義三個參數： `Name` 、 `Force` 和 `PassThru` 。 如需定義這些參數的詳細資訊，請參閱 [建立修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

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

您的 Cmdlet 必須覆寫輸入處理方法，最常使用的方法就是 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 此 Stop-Proc Cmdlet 會覆寫 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 輸入處理方法。 在此 Stop-Proc Cmdlet 的執行中，會進行呼叫以寫入詳細訊息、偵錯工具訊息和警告訊息。

> [!NOTE]
> 如需這個方法如何呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法的詳細資訊，請參閱 [建立可修改系統的 Cmdlet （可修改系統](./creating-a-cmdlet-that-modifies-the-system.md)）。

## <a name="writing-a-verbose-message"></a>寫入詳細資訊訊息

[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法是用來寫入與特定錯誤狀況不相關的一般使用者層級資訊。 系統管理員接著可以使用該資訊繼續處理其他命令。 此外，使用這個方法所撰寫的任何資訊都應該依照需要當地語系化。

此 Stop-Proc Cmdlet 中的下列程式碼會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中，顯示兩個[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的呼叫：。

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>寫入調試訊息

[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法是用來撰寫可用於疑難排解 Cmdlet 操作的偵錯工具訊息（debug）。 從輸入處理方法進行呼叫。

> [!NOTE]
> Windows PowerShell 也會定義同時 `Debug` 提供詳細資訊和偵錯工具資訊的參數。 如果您的 Cmdlet 支援此參數，則不需要在呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)的相同程式碼中呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) ，而不需要呼叫。

範例 Stop-Proc Cmdlet 中的下列兩個程式碼區段會顯示[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法的呼叫，以進行呼叫的方法。

在呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 之前，會立即寫入此偵錯工具訊息。

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

在呼叫 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 之前，會立即寫入此偵錯工具訊息。

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell 會自動將 [WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 呼叫傳送至追蹤基礎結構和 Cmdlet。 這可讓您不需要在 Cmdlet 內執行任何額外的開發工作，即可將方法呼叫追蹤至主控應用程式、檔案或偵錯工具。 下列命令列專案會執行追蹤作業。

**PS> 追蹤-運算式停止-進程-檔進程：命令停止-進程記事本**

## <a name="writing-a-warning-message"></a>寫入警告訊息

當 Cmdlet 即將執行可能會產生非預期結果的作業（例如，覆寫唯讀檔案）時，會使用 [WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 方法來寫入警告訊息。

下列範例中的程式碼 Stop-Proc Cmdlet 會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中，顯示[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法的呼叫程式碼的呼叫方法。

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>寫入進度訊息

當 Cmdlet 作業需要較長的時間才能完成時，會使用 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 來寫入進度訊息。 對 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 的呼叫會傳遞傳送至主控應用程式的 [Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) 物件，以轉譯給使用者的應用程式使用。

> [!NOTE]
> 這個 Stop-Proc Cmdlet 不會包含 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 方法的呼叫，而不包含呼叫。

下列程式碼是嘗試複製專案之 Cmdlet 所寫入的進度訊息範例。

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

如需完整的 c # 範例程式碼，請參閱 [StopProcessSample02 範例](./stopprocesssample02-sample.md)。

## <a name="define-object-types-and-formatting"></a>定義物件類型和格式

Windows PowerShell 使用 .NET 物件在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新型別或擴充現有類型的詳細資訊，請參閱 [擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊。 如需註冊 Cmdlet 的詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 註冊 Windows PowerShell 時，您可以在命令列上執行它來進行測試。 讓我們測試範例 Stop-Proc Cmdlet。 如需從命令列使用 Cmdlet 的詳細資訊，請參閱 [Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 下列命令列專案會使用 Stop-Proc 來停止名為 "NOTEPAD" 的進程、提供詳細語音總機，以及列印偵錯工具資訊。

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

    即會出現下列輸出。

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

[如何建立 Windows PowerShell Cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[擴充物件類型和格式化](/previous-versions//ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
