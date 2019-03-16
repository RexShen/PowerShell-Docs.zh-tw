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
ms.openlocfilehash: 3f6bcd2e4ef4d9c404b3a5deeaa9f25d3fa42ec1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056510"
---
# <a name="required-development-guidelines"></a>必要的開發指導方針

當您撰寫您的 cmdlet 時，必須遵循下列指導方針。 分成設計的 cmdlet 和撰寫程式的指令程式碼的指導方針的指導方針。 如果您未遵循這些指導方針，cmdlet 可能會失敗，並在使用您的 cmdlet 時，您的使用者可能有不佳的體驗。

## <a name="in-this-topic"></a>本主題內容

### <a name="design-guidelines"></a>設計指導方針

- [只使用核准的動詞命令 (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet 名稱：無法使用的字元 (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [無法使用的參數名稱 (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [支援確認要求 (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [針對互動式工作階段 (RD05) 支援 Force 參數](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [文件輸出物件 (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>程式碼的指導方針

- [衍生自的 Cmdlet 或 PSCmdlet 類別 (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [指定 Cmdlet 屬性 (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [覆寫輸入處理方法 (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [指定 OutputType 屬性 (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [不會保留輸出物件 (RC05) 的控制代碼](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [穩固處理錯誤 (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [使用 Windows PowerShell 模組來部署您的 Cmdlet (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>設計指導方針

設計以確保一致的使用者經驗之間使用您的 cmdlet 和其他 cmdlet 的 cmdlet 時，必須遵循下列指導方針。 當您找到適用於您情況的設計指導方針時，請務必查看類似的指導方針中的程式碼的方針。

### <a name="use-only-approved-verbs-rd01"></a>只使用核准的動詞命令 (RD01)

Cmdlet 屬性中指定的動詞命令必須來自可辨識的 Windows PowerShell 所提供的動詞命令集合。 它不能其中一個禁止的同義字。 使用下列列舉來指定 cmdlet 動詞命令所定義的常數字串：

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

如需已核准的動詞名稱的詳細資訊，請參閱[Cmdlet 動詞](./approved-verbs-for-windows-powershell-commands.md)。

使用者需要一組可探索和預期的 cmdlet 名稱。 讓使用者可以快速評估 cmdlet 的用途，並輕鬆地找出系統的功能，請使用適當的動詞命令。 例如，下列的命令列命令取得名稱開頭為"start"系統上的所有命令的清單： `get-command start-*`。 使用在您的 cmdlet 名詞來區分您的 cmdlet 與其他 cmdlet。 名詞指出要在作業執行所在的資源。 作業本身被以動詞命令。

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet 名稱：無法使用的字元 (RD02)

當您命名 cmdlet 時，請勿使用任何下列特殊字元。

|字元|名稱|
|---------------|----------|
|#|數字符號|
|、|逗號|
|()|括號|
|{}|大括號|
|[]|方括號|
|&|連字號|
|-|連字號**附註：** 連字號可以用來分隔從名詞動詞，但無法使用的動詞或名詞中。|
|/|斜線符號|
|\|反斜線|
|$|貨幣符號|
|^|插入號|
|;|分號|
|：|冒號|
|"|雙引號|
|'|單引號|
|<>|角括弧|
|&#124;|直槓|
|?|問號|
|@|@ 記號|
|' | 回刻度 （抑音符號）|
|*|星號|
|%|百分比符號|
|+|加號|
|=|等號|
|~|波狀符號|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>無法使用的參數名稱 (RD03)

為所有的 cmdlet 參數加上額外的參數會加入在特定情況下，Windows PowerShell 會提供一組通用。 設計您自己的 cmdlet 時，您無法使用下列名稱：確認、 Debug、 ErrorAction、 ErrorVariable、 OutBuffer OutVariable、 WarningAction、 WarningVariable、 WhatIf、 UseTransaction，和詳細資訊。 如需有關這些參數的詳細資訊，請參閱 <<c0> [ 常見的參數名稱](./common-parameter-names.md)。

### <a name="support-confirmation-requests-rd04"></a>支援確認要求 (RD04)

針對執行的作業，修改系統的 cmdlet，應該呼叫[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法來要求確認，並在特殊情況下呼叫[System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法。 ( [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)後，才應該呼叫方法[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫方法。)

若要進行這些呼叫必須指定此 cmdlet，它支援確認要求，方法是設定`SupportsShouldProcess`Cmdlet 屬性的關鍵字。 如需有關設定此屬性的詳細資訊，請參閱 < [Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。

> [!NOTE]
> 如果在 cmdlet 類別的 Cmdlet 屬性指出此 cmdlet 支援呼叫[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，而此 cmdlet 也無法進行的呼叫[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，使用者可能意外地修改系統。

使用[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)修改任何系統的方法。 使用者喜好設定並`WhatIf`參數控制[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 相反地， [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)呼叫有潛在危險的修改執行額外的檢查。 這個方法不受任何使用者喜好設定或`WhatIf`參數。 如果您的指令程式會呼叫[System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，它應該有`Force`參數略過這兩種方法的呼叫，並可繼續進行作業。 這很重要，因為它可讓您使用非互動式指令碼和主機中的 cmdlet。

如果您的 cmdlet 會支援這些呼叫，使用者可以判斷是否應實際執行動作。 例如， [Stop-process](/powershell/module/microsoft.powershell.management/stop-process) cmdlet 會呼叫[System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法之前停止的重要處理序，包括系統，而 Winlogon，一組和Spoolsv 程序。

如需有關如何支援這些方法的詳細資訊，請參閱 <<c0> [ 要求確認](./requesting-confirmation-from-cmdlets.md)。

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>針對互動式工作階段 (RD05) 支援 Force 參數

如果以互動方式使用您的 cmdlet，則一律提供 Force 參數，來覆寫的互動式的動作，例如提示或讀取行的輸入）。 這很重要，因為它可讓您使用非互動式指令碼和主機中的 cmdlet。 互動式的主機，可以實作下列方法。

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>文件輸出物件 (RD06)

Windows PowerShell 會使用寫入到管線的物件。 為了讓使用者充分利用每個 cmdlet 所傳回的物件，您必須文件所傳回的物件和這些傳回的物件成員的用途為何，您必須記錄。

## <a name="code-guidelines"></a>程式碼的指導方針

撰寫 cmdlet 程式碼時，必須遵循下列指導方針。 當您找到適用於您情況的程式碼指導方針時，請務必查看類似的指導方針的設計方針。

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>衍生自的 Cmdlet 或 PSCmdlet 類別 (RC01)

Cmdlet 必須衍生自[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)或是[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基底類別。 從衍生的 Cmdlet [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別不會依賴 Windows PowerShell 執行階段。 它們可以直接從任何 Microsoft.NET Framework 語言呼叫。 從衍生的 Cmdlet [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別取決於 Windows PowerShell 執行階段。 因此，它們的 runspace 內執行。

您實作的所有 cmdlet 類別必須都是公用類別。 如需有關這些 cmdlet 類別的詳細資訊，請參閱 <<c0> [ 指令程式概觀](./cmdlet-overview.md)。

### <a name="specify-the-cmdlet-attribute-rc02"></a>指定 Cmdlet 屬性 (RC02)

可辨識的 Windows PowerShell 的 cmdlet，為其.NET Framework 類別必須使用 Cmdlet 屬性裝飾。 這個屬性會指定此 cmdlet 的下列功能。

- 識別 cmdlet 動詞和名詞 」 組。

- 指定多個參數集時，會使用預設參數集。 Windows PowerShell 沒有足夠的資訊，以判斷哪一個參數設定為使用時，會使用預設參數集。

- 指出此 cmdlet 是否支援對[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 此 cmdlet 會在系統中進行變更之前，此方法會顯示確認訊息給使用者。 如需有關如何進行確認要求的詳細資訊，請參閱 <<c0> [ 要求確認](./requesting-confirmation-from-cmdlets.md)。

- 表示影響層級 （或嚴重性），並確認訊息相關聯的動作。 在大部分情況下，應該使用中的預設值。 如需有關如何影響層級會影響顯示給使用者確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

如需如何宣告 cmdlet 屬性的詳細資訊，請參閱[CmdletAttribute 宣告](./cmdlet-attribute-declaration.md)。

### <a name="override-an-input-processing-method-rc03"></a>覆寫輸入處理方法 (RC03)

針對在 Windows PowerShell 環境中參與 cmdlet，必須覆寫至少下列其中之一*輸入處理方法*。

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)這個方法會呼叫一次，並用來提供前置處理的功能。

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)多次，會呼叫這個方法，它用來提供記錄的記錄功能。

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)這個方法會呼叫一次，並用來提供後置處理的功能。

### <a name="specify-the-outputtype-attribute-rc04"></a>指定 OutputType 屬性 (RC04)

（在 Windows PowerShell 2.0 引進） 的 OutputType 屬性會指定您的 cmdlet 會傳回管線的.NET Framework 類型。 藉由指定 cmdlet 的輸出型別，您會使 cmdlet 所傳回您更容易找到其他指令程式的物件。 如需裝飾具有此屬性在 cmdlet 類別的詳細資訊，請參閱[OutputType 屬性宣告](./outputtype-attribute-declaration.md)。

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>不會保留輸出物件 (RC05) 的控制代碼

您的 cmdlet 應該不會保留任何傳遞給物件的控制代碼[System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 這些物件會傳遞至管線中下一個 cmdlet 或指令碼使用它們。 如果您保留物件的控制代碼，兩個實體會擁有每個物件，即會發生錯誤。

### <a name="handle-errors-robustly-rc06"></a>穩固處理錯誤 (RC06)

管理環境原本就會偵測，並對您管理系統的重要變更。 因此，務必指令程式會正確地處理錯誤。 如需詳細的錯誤記錄的詳細資訊，請參閱[Windows PowerShell 錯誤報告](./error-reporting-concepts.md)。

- 錯誤會導致無法繼續處理任何多筆記錄的 cmdlet，時，終止錯誤。 此指令程式必須呼叫[System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)所參考方法[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件。 如果不 cmdlet 所攔截到例外狀況，Windows PowerShell 執行階段本身會擲回終止錯誤，其中包含較少的資訊。

- 不會停止在下一次作業的非終止錯誤來自管線 （例如，a 記錄不同的程序所產生的），此指令程式的記錄必須呼叫[System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)所參考方法[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件。 非終止錯誤的範例是特定的處理程序無法停止時，就會發生此錯誤。 呼叫[System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法可讓使用者以一致的方式執行要求的動作，並保留失敗的特定動作的資訊。 您的 cmdlet 應該盡可能獨立處理每一筆記錄。

- [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)所參考的物件[System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)和[System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法需要在本質上發生例外狀況。 當您決定要使用的例外狀況時，請遵循.NET Framework 設計方針。 如果錯誤在語意上是相同的現有的例外狀況，會使用該例外狀況，或衍生自該例外狀況。 否則，衍生新的例外狀況或例外狀況階層架構，直接從[System.Exception](/dotnet/api/System.Exception)型別。

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件也會要求群組的使用者錯誤的錯誤分類。 使用者可以檢視所設定的值根據分類錯誤`$ErrorView`CategoryView 到殼層變數。 可能的類別由[System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉型別。

- 如果 cmdlet 會建立新的執行緒，而且在該執行緒中執行的程式碼會擲回未處理的例外狀況，Windows PowerShell 不會攔截錯誤，並將會終止處理序。

- 如果物件有其解構函式會造成未處理的例外狀況的程式碼，Windows PowerShell 不會攔截錯誤，並將會終止處理序。 如果物件呼叫 Dispose 方法，會造成未處理的例外狀況，這也會發生。

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>使用 Windows PowerShell 模組來部署您的 Cmdlet (RC07)

建立 Windows PowerShell 模組來封裝及部署您的 cmdlet。 模組的支援是在 Windows PowerShell 2.0 引進。 您可以使用直接二進位模組檔案 （這是很有幫助測試您的 cmdlet 時），以包含 cmdlet 類別的組件，或者您可以建立模組資訊清單所參考的指令程式組件。 （您也可以新增現有的嵌入式管理單元組件時使用的模組。）如需有關模組的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

## <a name="see-also"></a>另請參閱

[極力建議您的開發指導方針](./strongly-encouraged-development-guidelines.md)

[諮詢開發指導方針](./advisory-development-guidelines.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
