---
title: 將非終止錯誤報表新增至您的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: ec29d1cffa083e4cce667d3e1efbd4eeecbffb51
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870110"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>新增非終止錯誤報告到您的 Cmdlet

Cmdlet 可以藉由呼叫[WriteError 的管理元件][]方法來報告非終止錯誤，並繼續在目前的輸入物件或進一步的傳入管線物件上操作。 本節說明如何建立 Cmdlet，以從其輸入處理方法報告非終止錯誤。

對於非終止錯誤（以及終止錯誤），Cmdlet 必須傳遞識別錯誤的[ErrorRecord。][]物件。 每個錯誤記錄都是由稱為「錯誤識別碼」的唯一字串所識別。 除了識別碼以外，每個錯誤的類別都是由[ErrorCategory。][]列舉所定義的常數所指定。 使用者可以將 `$ErrorView` 變數設定為 "CategoryView"，以根據其類別來查看錯誤。

如需錯誤記錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。

## <a name="defining-the-cmdlet"></a>定義 Cmdlet

Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。 此 Cmdlet 會抓取處理常式資訊，因此此處選擇的動詞名稱是 "Get"。 （幾乎任何能夠抓取資訊的 Cmdlet 都可以處理命令列輸入）。如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](approved-verbs-for-windows-powershell-commands.md)。

以下是此 `Get-Proc` Cmdlet 的定義。 [建立您的第一個 Cmdlet](creating-a-cmdlet-without-parameters.md)會提供此定義的詳細資料。

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>定義參數

如有需要，您的 Cmdlet 必須定義用來處理輸入的參數。 此 Get Proc Cmdlet 會定義**名稱**參數，如[新增處理命令列輸入的參數](adding-parameters-that-process-command-line-input.md)中所述。

以下是這個 Get-Proc Cmdlet 的**Name**參數的參數宣告。

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a>覆寫輸入處理方法

所有 Cmdlet 都必須至少覆寫由[[系統管理]。 Cmdlet][]類別所提供的其中一個輸入處理方法。 [建立您的第一個 Cmdlet](creating-a-cmdlet-without-parameters.md)中會討論這些方法。

> [!NOTE]
> 您的 Cmdlet 應該盡可能獨立處理每一筆記錄。

此 Proc 指令程式會覆寫[ProcessRecord 的管理元件][]方法，以處理使用者或腳本所提供之輸入的**名稱**參數。 如果未提供任何名稱，這個方法會取得每個要求的進程名稱或所有進程的進程。 [建立您的第一個 Cmdlet](creating-a-cmdlet-without-parameters.md)會提供此覆寫的詳細資料。

### <a name="things-to-remember-when-reporting-errors"></a>報告錯誤時要記住的事項

Cmdlet 在寫入錯誤時所傳遞的[ErrorRecord。][]物件，在其核心上需要例外狀況。 判斷要使用的例外狀況時，請遵循 .NET 指導方針。
基本上，如果錯誤在語義上與現有的例外狀況相同，則 Cmdlet 應使用或衍生自該例外狀況。 否則，它應該直接從 system.exception 類別衍生新的例外狀況或[Exception][]階層。

建立錯誤識別碼（透過 ErrorRecord 類別的 FullyQualifiedErrorId 屬性存取）時，請記住下列事項。

- 使用以診斷為目標的字串，以便在檢查完整識別碼時，您可以判斷錯誤是什麼，以及錯誤的來源。

- 正確格式的完整錯誤識別碼可能如下所示。

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

請注意，在上一個範例中，錯誤識別碼（第一個 token）會指定錯誤的內容，而其餘部分則會指出錯誤的來源。

- 針對更複雜的案例，錯誤識別碼可以是以點分隔的標記，可以在檢查時進行剖析。 這可讓您在錯誤識別碼的部分，以及錯誤識別碼和錯誤分類中，進行分支。

Cmdlet 應該將特定的錯誤識別碼指派給不同的程式碼路徑。 請記住下列資訊來指派錯誤識別碼：

- 在整個 Cmdlet 生命週期中，錯誤識別碼應該保持不變。 請勿變更 Cmdlet 版本之間錯誤識別碼的語法。
- 針對 tersely 對應至所回報錯誤的錯誤識別碼，請使用文字。 請勿使用空白字元或標點符號。
- 讓您的 Cmdlet 只產生可重現的錯誤識別碼。 例如，它不應該產生包含進程識別碼的識別碼。 只有當使用者對應到其他遇到相同問題的使用者所看到的識別碼時，錯誤識別碼才會很有用。

在下列情況下，PowerShell 不會攔截到未處理的例外狀況：

- 如果 Cmdlet 建立新的執行緒，且該執行緒中執行的程式碼擲回未處理的例外狀況，則 PowerShell 將不會攔截錯誤，並會終止進程。
- 如果物件在其析構函式或處置方法中有程式碼造成未處理的例外狀況，則 PowerShell 不會攔截錯誤，並會終止進程。

## <a name="reporting-nonterminating-errors"></a>報告非終止錯誤

任何一個輸入處理方法都可以使用[WriteError 的管理元件][]方法，將非終止錯誤報表到輸出資料流程。

以下是來自這個 WriteError 指令程式的程式碼範例，其中說明如何從[ProcessRecord 的管理元件][]方法的覆寫中呼叫[WriteError 的管理元件][]，以從該 Cmdlet 中取得。 在此情況下，如果 Cmdlet 找不到指定之處理序識別碼的進程，就會進行呼叫。

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
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
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>撰寫非終止錯誤時應記住的事項

針對非終止錯誤，此 Cmdlet 必須為每個特定的輸入物件產生特定的錯誤識別碼。

Cmdlet 經常需要修改非終止錯誤所產生的 PowerShell 動作。 它可以藉由定義 `ErrorAction` 和 `ErrorVariable` 參數來達到這個目的。 如果定義 `ErrorAction` 參數，此 Cmdlet 會顯示[ActionPreference。][]的使用者選項，您也可以藉由設定 `$ErrorActionPreference` 變數直接影響動作。

Cmdlet 可以使用 `ErrorVariable` 參數，將非終止錯誤儲存至變數，這不會受到 `ErrorAction`設定的影響。 您可以藉由在變數名稱前面加上加號（+），將失敗附加至現有的錯誤變數。

## <a name="code-sample"></a>程式碼範例

如需完整C#的範例程式碼，請參閱[GetProcessSample04 範例](./getprocesssample04-sample.md)。

## <a name="define-object-types-and-formatting"></a>定義物件類型和格式

PowerShell 會使用 .NET 物件在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，您必須透過 Windows powershell 嵌入式管理單元向 Windows PowerShell 註冊它。 如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 已向 PowerShell 註冊時，您可以在命令列上執行它來進行測試。 讓我們測試範例 Get-Proc Cmdlet，以查看它是否報告錯誤：

- 啟動 PowerShell，並使用 Get-help Cmdlet 來抓取名為 "TEST" 的處理常式。

  ```powershell
  get-proc -name test
  ```

  下列輸出隨即出現。

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a>另請參閱

[加入處理管線輸入的參數](./adding-parameters-that-process-pipeline-input.md)

[新增可處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)

[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell 參考](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)

[Exception]: /dotnet/api/System.Exception
[ActionPreference。]: /dotnet/api/System.Management.Automation.ActionPreference
[ProcessRecord 的管理元件]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[WriteError 的管理元件]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[[系統管理]。 Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[ErrorCategory。]: /dotnet/api/System.Management.Automation.ErrorCategory
[ErrorRecord。]: /dotnet/api/System.Management.Automation.ErrorRecord
