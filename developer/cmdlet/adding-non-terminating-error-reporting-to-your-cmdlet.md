---
title: 新增非終止錯誤報告到您的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984233"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>新增非終止錯誤報告到您的 Cmdlet

指令程式可以藉由呼叫報告非終止錯誤[System.Management.Automation.Cmdlet.WriteError][]方法還是繼續執行進一步的連入或目前的輸入物件上的作業和管線的物件。
本節說明如何建立 cmdlet 會報告非終止錯誤，從其輸入的處理方法。

非終止錯誤 （以及終止錯誤），此指令程式必須通過[System.Management.Automation.ErrorRecord][]識別錯誤的物件。
每個錯誤記錄是由稱為 「 錯誤識別碼 」 的唯一字串識別。
除了識別項，每個錯誤類別目錄由所定義的常數[System.Management.Automation.ErrorCategory][]列舉型別。
使用者可以檢視根據其類別，藉由設定錯誤`$ErrorView`變數設為"CategoryView 」。

如需詳細的錯誤記錄的詳細資訊，請參閱[Windows PowerShell 的錯誤記錄](./windows-powershell-error-records.md)。

## <a name="defining-the-cmdlet"></a>定義此指令程式

Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。
此 cmdlet 可擷取處理序資訊，因此在這裡選擇的指令動詞名稱是 「 Get 」。
（幾乎任何一種能夠擷取資訊的指令程式可以處理命令列輸入）。如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](approved-verbs-for-windows-powershell-commands.md)。

以下是此 Get-proc cmdlet 的定義。
會提供此定義的詳細資料[建立您的第一個 Cmdlet](creating-a-cmdlet-without-parameters.md)。

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

如有必要，您的 cmdlet 必須定義來處理輸入的參數。
定義此 Get-proc cmdlet**名稱**參數中所述[加入參數，該程序的命令列輸入](adding-parameters-that-process-command-line-input.md)。

以下是參數宣告**名稱**此 Get-proc cmdlet 的參數。

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

所有 cmdlet 必須覆都寫的輸入處理所提供的方法之一[System.Management.Automation.Cmdlet][]類別。
這些方法中會討論[建立您的第一個 Cmdlet](creating-a-cmdlet-without-parameters.md)。

> [!NOTE]
> 您的 cmdlet 應該盡可能獨立處理每一筆記錄。

此 Get-proc cmdlet 會覆寫[System.Management.Automation.Cmdlet.ProcessRecord][]方法來處理**名稱**參數提供的使用者或指令碼輸入。
如果未提供名稱，這個方法會取得每個要求的處理序名稱或所有處理程序的程序。
此覆寫的詳細資料指定於[建立您的第一個 Cmdlet](creating-a-cmdlet-without-parameters.md)。

### <a name="things-to-remember-when-reporting-errors"></a>報告錯誤時的注意事項

[System.Management.Automation.ErrorRecord][]物件寫入錯誤需要在本質上發生例外狀況時，將傳遞此 cmdlet。
決定要使用的例外狀況時，請遵循的.NET 指導方針。
基本上，如果發生錯誤語意上與現有的例外狀況相同，則指令程式應該使用，或衍生自該例外狀況。
否則，它應該衍生新的例外狀況或例外狀況階層架構，直接從[System.Exception][]類別。

建立錯誤 （透過 ErrorRecord 類別 FullyQualifiedErrorId 屬性存取） 的識別項時請下列記住。

- 使用目標和診斷之用，以便檢查完整的識別碼時，您就可以判斷哪些錯誤是錯誤的來源位置的字串。

- 格式正確且完整的錯誤識別碼可能如下所示。

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

請注意，在上述範例中，錯誤識別碼 （第一個語彙基元） 將指定的錯誤訊息的是，其餘部分會指出錯誤的來源。

- 更複雜的情況下，錯誤識別碼可以是可剖析在檢查點分隔權杖。
  這可讓您太分支上的部分錯誤識別項以及錯誤的識別碼和錯誤分類。

此指令程式應該將特定的錯誤識別碼指派給不同的程式碼路徑。
記住下列資訊進行指派的錯誤識別碼：

- 錯誤識別碼應該維持在 cmdlet 生命週期。
  不會變更錯誤識別項 cmdlet 版本之間的語意。

- 使用文字 tersely 對應到所回報的錯誤之錯誤識別項。
  請勿使用空格或標點符號。

- 有 cmdlet 產生的可重現錯誤識別碼。
  比方說，它不應該產生識別碼，其中包含處理序識別碼。
  這些對應會遇到相同問題的其他使用者所看到的識別項時，才，錯誤識別碼很實用的使用者。

PowerShell 不會攔截未處理例外狀況在下列條件：

- 如果 cmdlet 會建立新的執行緒，並執行，因為執行緒擲回未處理的例外狀況的程式碼，PowerShell 不會攔截錯誤，並將會終止處理序。

- 如果物件有其解構函式或 Dispose 方法中造成未處理的例外狀況的程式碼，PowerShell 不會攔截錯誤，並將會終止處理序。

## <a name="reporting-nonterminating-errors"></a>報告非終止錯誤

輸入處理方法的任何一個可以回報給輸出資料流使用的非終止錯誤[System.Management.Automation.Cmdlet.WriteError][]方法。

以下是程式碼範例說明如何呼叫這個 Get-proc cmdlet [System.Management.Automation.Cmdlet.WriteError][]從內的覆寫[System.Management.Automation.Cmdlet.ProcessRecord][]方法。
在此情況下，如果此 cmdlet 找不到處理程序指定的處理序識別碼可以進行呼叫。

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>要寫入非終止錯誤，必須注意的事項

對於非終止錯誤，此指令程式必須產生每個特定的輸入物件的特定錯誤識別碼。

Cmdlet 經常需要修改 PowerShell 動作所產生的非終止錯誤。
其做法是定義`ErrorAction`和`ErrorVariable`參數。
如果定義`ErrorAction`參數，cmdlet 會顯示 user options [System.Management.Automation.ActionPreference][]，您可以設定，以也會直接影響動作`$ErrorActionPreference`變數。

Cmdlet 可以儲存為變數使用的非終止錯誤`ErrorVariable`參數，它的設定不會影響`ErrorAction`。
失敗可以附加至現有的錯誤變數加上加號 （+） 的變數名稱前面。

## <a name="code-sample"></a>程式碼範例

完整C#程式碼範例，請參閱 < [GetProcessSample04 範例](./getprocesssample04-sample.md)。

## <a name="define-object-types-and-formatting"></a>定義物件類型和格式設定

PowerShell 會使用.NET 物件的 cmdlet 之間傳遞資訊。
因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。
如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>建置此指令程式

在實作之後的 cmdlet，您必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。
如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當尚未註冊 PowerShell cmdlet 時，您可以藉由在命令列上執行它來進行測試。
讓我們測試範例 Get-proc cmdlet，以查看它是否會報告錯誤：

- 啟動 PowerShell，然後使用 Get-proc cmdlet 來擷取名為"TEST"的處理程序。

    ```powershell
    PS> get-proc -name test
    ```

下列輸出隨即出現。

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>另請參閱

[新增處理程序管線輸入的參數](./adding-parameters-that-process-pipeline-input.md)

[加入處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)

[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 參考](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
