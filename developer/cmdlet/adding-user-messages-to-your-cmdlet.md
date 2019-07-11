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
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733764"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>新增使用者訊息到您的 Cmdlet

Cmdlet 可以撰寫數種可在 Windows PowerShell 執行階段向使用者顯示的訊息。 這些訊息包括下列類型：

- 包含使用者的一般資訊的詳細資訊訊息。

- 偵錯包含疑難排解資訊的訊息。

- 警告訊息，它包含一則通知，此指令程式即將執行的作業，可以有未預期的結果。

- 執行時間較長的作業時，已完成進度報表訊息包含多少相關資訊的運作方式的 cmdlet。

沒有任何限制，您的 cmdlet 可寫入的訊息數目，或您 cmdlet 會寫入的訊息類型。 每個訊息會寫入藉由從特定呼叫內的輸入處理方法的 cmdlet。

## <a name="defining-the-cmdlet"></a>定義此指令程式

Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。 任何類型的指令程式可以從其輸入處理方法，寫入使用者通知因此，在一般情況下，您可以命名使用任何指令動詞，指出此 cmdlet 會執行哪些系統修改此指令程式。 如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。

停止處理序 cmdlet 被設計來修改系統;因此， [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .NET 類別的宣告必須包含`SupportsShouldProcess`屬性關鍵字，並設定為`true`。

下列程式碼是此停止程序 cmdlet 類別定義。 如需有關此定義的詳細資訊，請參閱[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>修改系統定義的參數

停止處理序的指令程式會定義三個參數： `Name`， `Force`，和`PassThru`。 如需有關如何定義這些參數的詳細資訊，請參閱 <<c0> [ 建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。

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

您的 cmdlet 必須覆寫輸入處理方法，通常就會[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 此處理序停止外 cmdlet 會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)輸入處理方法。 在此停止程序 cmdlet 實作中，會呼叫寫入詳細資訊訊息、 偵錯訊息和警告訊息。

> [!NOTE]
> 如需有關如何呼叫這個方法[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，請參閱[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="writing-a-verbose-message"></a>寫入詳細資訊訊息

[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法用來撰寫與特定的錯誤情況不相關的一般使用者層級資訊。 系統管理員接著可以使用該資訊以繼續處理其他命令。 此外，視需要應該當地語系化使用這個方法所撰寫的任何資訊。

下列程式碼從這個停止程序的指令程式會顯示兩個呼叫[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的覆寫從[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>撰寫偵錯訊息

[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法用來撰寫可以用來疑難排解 cmdlet 作業的偵錯訊息。 從輸入處理方法進行呼叫。

> [!NOTE]
> Windows PowerShell 也會定義`Debug`參數顯示兩者的詳細資訊，及偵錯資訊。 如果您的 cmdlet 會支援這個參數，它不需要呼叫[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)在相同的程式碼會呼叫[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).

下列兩個範例停止程序 cmdlet 中的程式碼區段會顯示呼叫[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法的覆寫從[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。

此偵錯訊息寫入之前，立即[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫。

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

此偵錯訊息寫入之前，立即[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)呼叫。

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell 會自動路由傳送任何[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)呼叫追蹤基礎結構和 cmdlet。 這可讓方法呼叫來追蹤主控應用程式、 檔案，或偵錯工具，而不需要執行此指令程式中任何額外的開發工作。 下列命令列的項目會實作追蹤作業。

**PS > 追蹤運算式停止程序-檔案 proc.log-命令停止程序 [記事本]**

## <a name="writing-a-warning-message"></a>寫入一則警告訊息

[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法用來執行的作業可能會有非預期的結果，例如覆寫唯讀檔案，此 cmdlet 時，寫入一個警告。

Cmdlet 範例停止程序的下列程式碼會示範呼叫[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法的覆寫從[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。

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

[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)用來寫入進度訊息，當 cmdlet 作業會需要更的長的時間才能完成。 呼叫[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)通過[System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord)傳送至裝載的應用程式呈現給使用者的物件。

> [!NOTE]
> 此處理序停止外 cmdlet 不包含呼叫[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。

下列程式碼是由指令程式來嘗試複製項目寫入進度訊息的範例。

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

完整C#程式碼範例，請參閱 < [StopProcessSample02 範例](./stopprocesssample02-sample.md)。

## <a name="define-object-types-and-formatting"></a>定義物件類型和格式設定

Windows PowerShell cmdlet 使用.NET 物件之間傳遞資訊。 因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。 如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建置此指令程式

在實作之後的 cmdlet，它必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。 如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。 我們來測試範例停止程序 cmdlet。 如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 下列命令列的項目使用停止程序來停止名為"NOTEPAD"的處理序、 提供詳細的通知，並列印偵錯資訊。

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

[建立修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何建立 Windows PowerShell Cmdlet](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
