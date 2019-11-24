---
title: 必要的開發指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369517"
---
# <a name="required-development-guidelines"></a>必要的開發指導方針

當您撰寫 Cmdlet 時，必須遵循下列指導方針。 它們會分成設計 Cmdlet 的指導方針，以及撰寫 Cmdlet 程式碼的指導方針。 如果您未遵循這些指導方針，您的 Cmdlet 可能會失敗，且您的使用者在使用您的 Cmdlet 時可能會有不佳的體驗。

## <a name="in-this-topic"></a>本主題內容

### <a name="design-guidelines"></a>設計指導方針

- [只使用核准的動詞（RD01）](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet 名稱：無法使用的字元（RD02）](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [無法使用的參數名稱（RD03）](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [支援確認要求（RD04）](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [互動式會話的支援強制參數（RD05）](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [檔輸出物件（RD06）](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>程式碼方針

- [衍生自 Cmdlet 或 PSCmdlet 類別（RC01）](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [指定 Cmdlet 屬性（RC02）](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [覆寫輸入處理方法（RC03）](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [指定 OutputType 屬性（RC04）](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [不要保留輸出物件的控制碼（RC05）](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [穩定處理錯誤（RC06）](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [使用 Windows PowerShell 模組來部署您的 Cmdlet （RC07）](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>設計指導方針

設計 Cmdlet 時必須遵循下列指導方針，以確保使用您的 Cmdlet 和其他 Cmdlet 的使用者體驗一致。 當您找到適用于您情況的設計指導方針時，請務必查看類似方針的程式碼方針。

### <a name="use-only-approved-verbs-rd01"></a>只使用核准的動詞（RD01）

Cmdlet 屬性中指定的動詞必須來自 Windows PowerShell 所提供的一組可辨識動詞。 不得為其中一個禁止的同義字。 使用下列列舉所定義的常數位串來指定 Cmdlet 動詞：

- [VerbsCommon。](/dotnet/api/System.Management.Automation.VerbsCommon)

- [VerbsCommunications。](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [VerbsData。](/dotnet/api/System.Management.Automation.VerbsData)

- [VerbsDiagnostic。](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [VerbsLifeCycle。](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [VerbsSecurity。](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [VerbsOther。](/dotnet/api/System.Management.Automation.VerbsOther)

如需已核准動詞名稱的詳細資訊，請參閱[Cmdlet 動詞](./approved-verbs-for-windows-powershell-commands.md)。

使用者需要一組可探索且預期的 Cmdlet 名稱。 使用適當的動詞，讓使用者可以快速評估 Cmdlet 的用途，並輕鬆地探索系統的功能。 例如，下列命令列命令會取得系統上名稱開頭為 "start" 的所有命令清單： `get-command start-*`。 使用 Cmdlet 中的名詞來區分您的 Cmdlet 與其他 Cmdlet。 名詞表示將在其上執行作業的資源。 作業本身是以動詞來表示。

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet 名稱：無法使用的字元（RD02）

當您命名 Cmdlet 時，請勿使用下列任何特殊字元。

|字母|Name|
|---------------|----------|
|#|數位記號|
|、|千|
|()|後|
|{}|成對|
|[]|內|
|&|字元|
|-|連字號**附注：** 連字號可以用來分隔動詞和名詞，但不能用在名詞或動詞內。|
|/|斜線|
|\\| 反斜線|
|$|貨幣符號|
|^|插入號|
|;|均|
|:|加|
|"|雙引號|
|'|單引號|
|<>|角括弧|
|&#124;|分隔號|
|?|問號|
|@|at sign|
|`|反向刻度（抑音符號）|
|*|代表|
|%|百分比符號|
|+|加號|
|=|等號|
|~|線|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>無法使用的參數名稱（RD03）

Windows PowerShell 提供一組通用的參數給所有 Cmdlet，再加上在特定情況下新增的其他參數。 在設計您自己的 Cmdlet 時，您無法使用下列名稱： Confirm、Debug、ErrorAction、ErrorVariable、OutBuffer、OutVariable、WarningAction、WarningVariable、WhatIf、UseTransaction 和 Verbose。 如需這些參數的詳細資訊，請參閱[一般參數名稱](./common-parameter-names.md)。

### <a name="support-confirmation-requests-rd04"></a>支援確認要求（RD04）

對於執行修改系統之作業的 Cmdlet，它們應該呼叫[ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法來要求確認，而在特殊情況下，則會呼叫[ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，而這會是。 （只有在呼叫[ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之後，才應呼叫[ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法）。）。（& i）

若要進行這些呼叫，Cmdlet 必須藉由設定 Cmdlet 屬性的 `SupportsShouldProcess` 關鍵字來指定它支援確認要求。 如需設定此屬性的詳細資訊，請參閱[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告。

> [!NOTE]
> 如果 Cmdlet 類別的 Cmdlet 屬性指出此 Cmdlet 支援[ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的呼叫，而此 Cmdlet 無法呼叫[ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，則使用者可能會非預期地修改系統，而無法對系統進行錯誤的程式。

針對任何系統修改，請使用[ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 使用者喜好設定和 `WhatIf` 參數，會控制[ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 相反地， [ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)呼叫會執行額外的檢查，以進行潛在的危險修改。 這個方法不是由任何使用者喜好設定或 `WhatIf` 參數所控制。 如果您的 Cmdlet 呼叫[ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，它應該會有一個 `Force` 參數，可略過這兩個方法的呼叫，並繼續進行作業。 這很重要，因為它可讓您的 Cmdlet 用於非互動式腳本和主機。

如果您的 Cmdlet 支援這些呼叫，使用者可以決定是否要實際執行動作。 例如，[停止進程](/powershell/module/microsoft.powershell.management/stop-process)Cmdlet 會先呼叫[ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，再停止一組重要的進程，包括系統、Winlogon 和 spoolsv.exe 進程。

如需有關支援這些方法的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>互動式會話的支援強制參數（RD05）

如果您的 Cmdlet 以互動方式使用，請一律提供 Force 參數來覆寫互動式動作，例如提示或讀取輸入的行）。 這很重要，因為它可讓您的 Cmdlet 用於非互動式腳本和主機。 下列方法可由互動式主機來執行。

- [PSHostUserInterface。提示字元（*）](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [Pshostuserinterface. PromptForChoice （系統管理）](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [Ihostuisupportsmultiplechoiceselection. PromptForChoice （系統管理）](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.web. Pshostuserinterface. PromptForCredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [Pshostuserinterface. ReadLine * 的 *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.web. Pshostuserinterface. ReadLineAsSecureString *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>檔輸出物件（RD06）

Windows PowerShell 會使用寫入管線的物件。 為了讓使用者能夠充分利用每個 Cmdlet 所傳回的物件，您必須記載傳回的物件，而且您必須記載這些傳回物件的成員會用於哪些內容。

## <a name="code-guidelines"></a>程式碼方針

撰寫 Cmdlet 程式碼時，必須遵循下列指導方針。 當您找到適用于您情況的程式碼指導方針時，請務必查看類似方針的設計方針。

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>衍生自 Cmdlet 或 PSCmdlet 類別（RC01）

Cmdlet 必須衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基類，或從系統. 管理[元件](/dotnet/api/System.Management.Automation.Cmdlet)衍生而來。 衍生自[system.object](/dotnet/api/System.Management.Automation.Cmdlet)類別的 Cmdlet 不會相依于 Windows PowerShell 執行時間。 可以直接從任何 Microsoft .NET Framework 語言呼叫。 衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別的 Cmdlet 取決於 Windows PowerShell 執行時間。 因此，它們會在運行空間內執行。

您所執行的所有 Cmdlet 類別都必須是公用類別。 如需這些 Cmdlet 類別的詳細資訊，請參閱[Cmdlet 總覽](./cmdlet-overview.md)。

### <a name="specify-the-cmdlet-attribute-rc02"></a>指定 Cmdlet 屬性（RC02）

為了讓 Windows PowerShell 能夠辨識 Cmdlet，其 .NET Framework 類別必須以 Cmdlet 屬性裝飾。 這個屬性會指定 Cmdlet 的下列功能。

- 識別 Cmdlet 的動詞和名詞配對。

- 當指定多個參數集時，所使用的預設參數集。 當 Windows PowerShell 沒有足夠的資訊來判斷要使用哪個參數集時，會使用預設的參數集。

- 指出此 Cmdlet 是否支援對[ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的呼叫。 這個方法會在 Cmdlet 對系統進行變更之前，向使用者顯示確認訊息。 如需有關如何提出確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

- 指出與確認訊息相關聯之動作的影響層級（或嚴重性）。 在大部分情況下，應該使用預設值 Medium。 如需影響層級如何影響向使用者顯示的確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

如需如何宣告 Cmdlet 屬性的詳細資訊，請參閱[CmdletAttribute](./cmdlet-attribute-declaration.md)宣告。

### <a name="override-an-input-processing-method-rc03"></a>覆寫輸入處理方法（RC03）

若要讓 Cmdlet 參與 Windows PowerShell 環境，它必須至少覆寫下列其中一個*輸入處理方法*。

[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)會呼叫這個方法一次，並使用它來提供前置處理功能。」

[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)會多次呼叫這個方法，而且它會用來提供記錄式的記錄功能。

將會[呼叫這個方法](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)一次，並使用它來提供後置處理功能。

### <a name="specify-the-outputtype-attribute-rc04"></a>指定 OutputType 屬性（RC04）

OutputType 屬性（在 Windows PowerShell 2.0 中引進）會指定您的 Cmdlet 傳回給管線的 .NET Framework 類型。 藉由指定 Cmdlet 的輸出類型，您可以讓 Cmdlet 傳回的物件更容易被其他 Cmdlet 探索。 如需使用此屬性裝飾 Cmdlet 類別的詳細資訊，請參閱[OutputType 屬性](./outputtype-attribute-declaration.md)宣告。

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>不要保留輸出物件的控制碼（RC05）

您的 Cmdlet 不應保留傳遞至[WriteObject *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法之物件的任何控制碼。 這些物件會傳遞至管線中的下一個 Cmdlet，或由腳本使用。 如果您保留物件的控制碼，兩個實體會擁有每個物件，這會造成錯誤。

### <a name="handle-errors-robustly-rc06"></a>穩定處理錯誤（RC06）

系統管理環境原本就會偵測並對您所管理的系統進行重要變更。 因此，Cmdlet 會正確處理錯誤。 如需錯誤記錄的詳細資訊，請參閱[Windows PowerShell 錯誤報表](./error-reporting-concepts.md)。

- 當錯誤阻止 Cmdlet 繼續處理任何其他記錄時，就會發生終止錯誤。 此 Cmdlet 必須呼叫[ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法，此方法會參考[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件，而此方法會參考。 如果 Cmdlet 未攔截到例外狀況，Windows PowerShell 執行時間本身會擲回包含較少資訊的終止錯誤。

- 針對不會在來自管線的下一筆記錄（例如，由不同進程所產生的記錄）上停止作業的非終止錯誤，此 Cmdlet 必須呼叫[WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，此方法會參考[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件的資訊。 非終止錯誤的範例就是當特定進程無法停止時，所發生的錯誤。 呼叫[WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法可讓使用者一致地執行所要求的動作，並保留特定動作失敗的資訊。 您的 Cmdlet 應該盡可能獨立處理每一筆記錄。

- [ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)和[WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法所參考的[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件，在其核心時需要例外狀況（exception），而不會有例外狀況（exception）。 當您判斷要使用的例外狀況時，請遵循 .NET Framework 的設計方針。 如果錯誤在語義上與現有的例外狀況相同，請使用該例外狀況或衍生自該例外狀況。 否則，請直接從[system.exception 類型衍生](/dotnet/api/System.Exception)新的例外狀況或例外狀況階層。

[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件也需要將使用者的錯誤分組的錯誤分類。 使用者可以將 `$ErrorView` shell 變數的值設定為 CategoryView，以根據類別來查看錯誤。 可能的類別是由[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉所定義。

- 如果 Cmdlet 會建立新的執行緒，而且如果在該執行緒中執行的程式碼擲回未處理的例外狀況，Windows PowerShell 將不會攔截錯誤，並會終止進程。

- 如果物件在其析構函式中有程式碼造成未處理的例外狀況，Windows PowerShell 將不會攔截錯誤，並會終止進程。 如果物件呼叫造成未處理例外狀況的 Dispose 方法，也會發生這種情況。

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>使用 Windows PowerShell 模組來部署您的 Cmdlet （RC07）

建立 Windows PowerShell 模組來封裝和部署 Cmdlet。 Windows PowerShell 2.0 中引進模組的支援。 您可以直接使用包含 Cmdlet 類別的元件做為二進位模組檔案（這在測試 Cmdlet 時非常有用），或者您也可以建立參考 Cmdlet 元件的模組資訊清單。 （使用模組時，您也可以新增現有的嵌入式管理單元元件）。如需模組的詳細資訊，請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

## <a name="see-also"></a>另請參閱

[強烈建議的開發指導方針](./strongly-encouraged-development-guidelines.md)

[諮詢開發指導方針](./advisory-development-guidelines.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
