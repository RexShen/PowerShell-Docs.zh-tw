---
ms.date: 09/13/2016
ms.topic: reference
title: 強烈建議使用的開發指導方針
description: 強烈建議使用的開發指導方針
ms.openlocfilehash: e12fa0d1adc0d7a0dad938457bdcd289736df97c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355233"
---
# <a name="strongly-encouraged-development-guidelines"></a>強烈建議使用的開發指導方針

本節說明當您撰寫 Cmdlet 時應遵循的指導方針。 它們分成設計 Cmdlet 的指導方針和撰寫 Cmdlet 程式碼的指導方針。 您可能會發現這些指導方針並不適用于每個案例。 但是，如果已套用這些原則，而您未遵循這些指導方針，則當使用者使用您的 Cmdlet 時，可能會有不佳的體驗。

## <a name="design-guidelines"></a>設計方針

設計 Cmdlet 時，應遵循下列指導方針，以確保使用您的 Cmdlet 與其他 Cmdlet 之間的使用者體驗一致。 當您找到適用于您情況的設計指導方針時，請務必查看類似指導方針的程式碼指導方針。

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>使用特定名詞作為 Cmdlet 名稱 (SD01) 

Cmdlet 命名中使用的名詞需要非常明確，讓使用者能夠探索您的 Cmdlet。
將一般名詞（例如 "server"）加上產品名稱的簡短版本。 例如，如果名詞參考的伺服器是執行 Microsoft SQL Server 的實例，請使用 "SQLServer" 這類名詞。 特定名詞的組合和核准動詞命令的簡短清單，可讓使用者快速探索和預期功能，同時避免在 Cmdlet 名稱之間重複。

為了增強使用者體驗，您為 Cmdlet 名稱選擇的名詞應該是單數的。 例如，請使用名稱， `Get-Process` 而不要使用 **Get 進程**。 針對所有 Cmdlet 名稱，最好遵循此規則，即使 Cmdlet 可能會在多個專案上採取動作也是一樣。

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>針對 Cmdlet 名稱使用 Pascal 案例 (SD02) 

使用 Pascal 的參數名稱大寫。 換句話說，請將動詞的第一個字母和名詞中使用的所有詞彙做為大寫。 例如，"`Clear-ItemProperty`"。

### <a name="parameter-design-guidelines-sd03"></a>參數設計指導方針 (SD03) 

Cmdlet 需要可接收其必須操作之資料的參數，以及表示用來判斷作業特性之資訊的參數。 例如，Cmdlet 可能會有一個 `Name` 從管線接收資料的參數，而此 Cmdlet 可能會有一個 `Force` 參數，表示可以強制執行 Cmdlet 來執行其作業。 Cmdlet 可以定義的參數數目沒有任何限制。

#### <a name="use-standard-parameter-names"></a>使用標準參數名稱

您的 Cmdlet 應使用標準參數名稱，讓使用者可以快速判斷特定參數的意義。 如果需要更明確的名稱，請使用標準參數名稱，然後指定更明確的名稱做為別名。 例如， `Get-Service` Cmdlet 有一個參數，該參數具有泛型名稱 (`Name`) ，而 () 更明確的別名 `ServiceName` 。 這兩個詞彙都可以用來指定參數。

如需參數名稱和其資料類型的詳細資訊，請參閱 [Cmdlet 參數名稱和功能指導方針](./standard-cmdlet-parameter-names-and-types.md)。

#### <a name="use-singular-parameter-names"></a>使用單數參數名稱

請避免針對其值為單一專案的參數使用複數名稱。 這包括採用陣列或清單的參數，因為使用者可能會提供只有一個元素的陣列或清單。

只有在參數的值一律為多元素值的情況下，才應該使用複數參數名稱。 在這些情況下，Cmdlet 應確認是否提供多個元素，如果未提供多個元素，則 Cmdlet 應該向使用者顯示警告。

#### <a name="use-pascal-case-for-parameter-names"></a>使用 Pascal 的參數名稱案例

使用 Pascal 的參數名稱大寫。 換句話說，在參數名稱中，每個單字的第一個字母都是大寫，包括名稱的第一個字母。 例如，參數名稱會 `ErrorAction` 使用正確的大小寫。 下列參數名稱使用不正確的大小寫：

- `errorAction`
- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>採用選項清單的參數

有兩種方式可以建立參數，其值可從一組選項中選取。

-  (定義列舉型別，或使用現有的列舉型別) 指定有效的值。
  然後，使用列舉型別來建立該型別的參數。

- 將 **ValidateSet** 屬性加入至參數宣告。 如需此屬性的詳細資訊，請參閱 [ValidateSet 屬性聲明](./validateset-attribute-declaration.md)。

#### <a name="use-standard-types-for-parameters"></a>使用標準類型的參數

為了確保與其他指令程式一致，請在可能的情況下使用標準類型的參數。 如需有關應用於不同參數之類型的詳細資訊，請參閱 [標準 Cmdlet 參數名稱和類型](./standard-cmdlet-parameter-names-and-types.md)。 本主題提供數個主題的連結，這些主題描述標準參數群組的名稱和 .NET Framework 類型，例如「活動參數」。

#### <a name="use-strongly-typed-net-framework-types"></a>使用 Strongly-Typed .NET Framework 類型

參數應定義為 .NET Framework 類型，以提供更好的參數驗證。 例如，限制為一組值之一值的參數應定義為列舉型別。 若要支援統一資源識別項 (URI) 值，請將參數定義為[system.string 類型。](/dotnet/api/System.Uri) 針對所有但自由格式的文字屬性，請避免基本的字串參數。

#### <a name="use-consistent-parameter-types"></a>使用一致的參數類型

當多個 Cmdlet 使用同一個參數時，請一律使用相同的參數類型。 例如，如果 `Process` 參數是一個 Cmdlet 的 [system.string](/dotnet/api/System.Int16) 類型，請勿讓 `Process` 另一個 Cmdlet 的參數 [成為 system.string](/dotnet/api/System.UInt16) 類型。

#### <a name="parameters-that-take-true-and-false"></a>採用 True 和 False 的參數

如果您的參數只接受 `true` 和 `false` ，請將參數定義為 [SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型。
切換參數會被視為 `true` 命令中指定的參數。 如果命令中未包含參數，Windows PowerShell 會將參數的值視為 `false` 。 請勿定義布林值參數。

如果您的參數需要區分3個值： $true、$false 和「未指定」，請將類型的參數定義為可為 Null \<bool> 。 當 Cmdlet 可以修改物件的布林值屬性時，通常會發生第三個「未指定」值的需求。 在此情況下，「未指定」表示不變更屬性的目前值。

#### <a name="support-arrays-for-parameters"></a>支援參數的陣列

使用者通常必須對多個引數執行相同的作業。 針對這些使用者，Cmdlet 應接受陣列作為參數輸入，讓使用者可以將引數以 Windows PowerShell 變數的形式傳遞至參數。 例如， [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 會使用字串陣列來識別要抓取之進程的名稱。

#### <a name="support-the-passthru-parameter"></a>支援 PassThru 參數

根據預設，許多修改系統的 Cmdlet （例如， [停止進程](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) Cmdlet）都會作為物件的「接收器」，而不會傳回結果。 這些 Cmdlet 應執行 `PassThru` 參數，以強制 Cmdlet 傳回物件。 當 `PassThru` 指定參數時，此 Cmdlet 會使用 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 方法的呼叫傳回物件（）。 例如，下列命令會停止 Calc 處理常式，並將結果進程傳遞至管線。

```powershell
Stop-Process calc -passthru
```

在大多數情況下，新增、設定和新的 Cmdlet 都應該支援 `PassThru` 參數。

#### <a name="support-parameter-sets"></a>支援參數集

Cmdlet 旨在完成單一用途。 不過，通常會有一種以上的方法來描述作業或操作目標。 例如，進程可能會以其名稱、識別碼或處理常式物件來識別。 此 Cmdlet 應支援其目標的所有合理表示。 一般來說，此 Cmdlet 會藉由指定參數集 (稱為參數集來滿足這項需求，) 會一起運作。 單一參數可以屬於任意數目的參數集合。 如需參數集的詳細資訊，請參閱 [Cmdlet 參數集](./cmdlet-parameter-sets.md)。

當您指定參數集時，請將集合中的一個參數設定為 ValueFromPipeline。 如需如何宣告 **參數** 屬性的詳細資訊，請參閱 [ParameterAttribute](./parameter-attribute-declaration.md)宣告。

使用參數集時，會由 **Cmdlet** 屬性定義預設參數集。 預設參數集應該包含互動式 Windows PowerShell 會話中最有可能使用的參數。 如需如何宣告 **Cmdlet** 屬性的詳細資訊，請參閱 [CmdletAttribute](./cmdlet-attribute-declaration.md)宣告。

### <a name="provide-feedback-to-the-user-sd04"></a>將意見反應提供給使用者 (SD04) 

使用本節中的指導方針，將意見反應提供給使用者。 這項意見反應可讓使用者瞭解系統中發生的狀況，並做出更佳的系統管理決策。

Windows PowerShell 執行時間可讓使用者藉 `Write` 由設定喜好設定變數，指定如何處理每個方法呼叫的輸出。 使用者可以設定數個喜好設定變數，包括決定系統是否應該顯示資訊的變數，以及決定系統是否應該在採取進一步動作之前查詢使用者的變數。

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>支援 WriteWarning、WriteVerbose 和 WriteDebug 方法

當 Cmdlet 即將執行可能會產生非預期結果的作業時，指令程式應呼叫 [WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 方法。 例如，如果 Cmdlet 即將覆寫唯讀檔案，則 Cmdlet 應該呼叫這個方法。

當使用者需要有關 Cmdlet 所執行之工作的詳細資訊時，Cmdlet 應呼叫 [WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 方法。 例如，如果 Cmdlet 作者覺得有一些案例可能需要更多有關 Cmdlet 所做的資訊，則 Cmdlet 應呼叫此資訊。

當開發人員或產品支援工程師必須瞭解 Cmdlet 作業損毀時，此 Cmdlet 應該呼叫 [WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 方法。 Cmdlet 不需要在呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的相同程式碼中呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法，因為此 `Debug` 參數會顯示這兩組資訊。（此參數）會顯示這兩組資訊。

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>針對花費很長時間的作業支援 WriteProgress

需要很長時間才能完成，而且無法在背景中執行的 Cmdlet 作業，應該透過 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 方法的定期呼叫來支援進度報告。

#### <a name="use-the-host-interfaces"></a>使用主機介面

在此情況下，Cmdlet 必須直接與使用者進行通訊，而不是使用不同的寫入，或應該是由 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 類別支援的方法。 在此情況下，此 Cmdlet 應該衍生自 [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 類別，並使用 [PSCmdlet. Host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) 屬性（property）。 這個屬性支援不同層級的通訊類型，包括 PromptForChoice、Prompt 和 WriteLine/ReadLine 類型。 在最特定的層級中，它也提供讀取和寫入個別金鑰以及處理緩衝區的方式。

除非 Cmdlet 專門設計為產生圖形化使用者介面， (GUI) ，否則不應該使用 [PSCmdlet *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) 屬性來略過主機。 設計用來產生 GUI 的 Cmdlet 範例是 [Out GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) Cmdlet。

> [!NOTE]
> Cmdlet 不應使用 [System. Console](/dotnet/api/System.Console) API。

### <a name="create-a-cmdlet-help-file-sd05"></a>建立 Cmdlet 說明檔 (SD05) 

針對每個 Cmdlet 元件建立 Help.xml 檔案，其中包含 Cmdlet 的相關資訊。 這項資訊包含 Cmdlet 的描述、Cmdlet 參數的描述、Cmdlet 用法的範例等等。

## <a name="code-guidelines"></a>程式碼指導方針

在撰寫 Cmdlet 的程式碼時，應遵循下列指導方針，以確保使用您的 Cmdlet 與其他 Cmdlet 之間的使用者體驗一致。 當您找到適用于您的情況的程式碼指導方針時，請務必查看類似指導方針的設計指導方針。

### <a name="coding-parameters-sc01"></a>編碼參數 (SC01) 

宣告以 **參數** 屬性裝飾之 Cmdlet 類別的公用屬性，以定義參數。 參數不一定要是 Cmdlet 的衍生 .NET Framework 類別的靜態成員。 如需如何宣告 **參數** 屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。

#### <a name="support-windows-powershell-paths"></a>支援 Windows PowerShell 路徑

Windows PowerShell 路徑是標準化命名空間存取的機制。 當您將 Windows PowerShell 路徑指派給 Cmdlet 中的參數時，使用者可以定義自訂的 "drive" 作為特定路徑的快捷方式。 當使用者指定這類磁片磁碟機時，儲存的資料（例如登錄中的資料）可以一致的方式使用。

如果您的 Cmdlet 允許使用者指定檔案或資料來源，則應該定義 [system.string](/dotnet/api/System.String)類型的參數。 如果支援多個磁片磁碟機，則類型應為數組。 參數的名稱應該是 `Path` ，別名為 `PSPath` 。
此外， `Path` 參數應該支援萬用字元。 如果不需要支援萬用字元，請定義 `LiteralPath` 參數。

如果 Cmdlet 讀取或寫入的資料必須是檔案，則 Cmdlet 應接受 Windows PowerShell 的路徑輸入，而且 Cmdlet 應使用 [Sessionstate](/dotnet/api/System.Management.Automation.SessionState.Path) 屬性將 Windows PowerShell 路徑轉譯為檔案系統可辨識的路徑。 特定的機制包括下列方法：

- [PSCmdlet. GetResolvedProviderPathFromPSPath。](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)
- [PSCmdlet. GetUnresolvedProviderPathFromPSPath。](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)
- [PathIntrinsics. GetResolvedProviderPathFromPSPath。](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)
- [PathIntrinsics. GetUnresolvedProviderPathFromPSPath。](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

如果 Cmdlet 讀取或寫入的資料只是一組字串，而不是檔案，則 Cmdlet 應該使用提供者內容資訊 (`Content` 成員) 來讀取和寫入。 這項資訊是從 [CmdletProvider. InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) 屬性取得。 這些機制可讓其他資料存放區參與資料的讀取和寫入。

#### <a name="support-wildcard-characters"></a>支援萬用字元

如果可能的話，Cmdlet 應支援萬用字元。 Cmdlet 的許多地方都有支援萬用字元 (特別是當參數接受字串來識別一組物件) 的一個物件時。 例如， [StopProc 教學](./stopproc-tutorial.md)課程中的範例 **Stop-Proc** Cmdlet 會定義一個 `Name` 參數來處理代表進程名稱的字串。 此參數支援萬用字元，讓使用者可以輕鬆地指定要停止的處理常式。

當提供萬用字元的支援時，Cmdlet 作業通常會產生陣列。
有時候，支援陣列並不合理，因為使用者一次只能使用一個專案。 例如， [設定位置](/powershell/module/Microsoft.PowerShell.Management/Set-Location) Cmdlet 不需要支援陣列，因為使用者只會設定單一位置。 在此情況下，Cmdlet 仍然支援萬用字元，但它會強制解析成單一位置。

如需萬用字元字元模式的詳細資訊，請參閱 [在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

#### <a name="defining-objects"></a>定義物件

本章節包含定義 Cmdlet 物件和擴充現有物件的指導方針。

##### <a name="define-standard-members"></a>定義標準成員

定義標準成員以延伸自訂 Types.ps1xml 檔案中的物件類型 (使用 Windows PowerShell Types.ps1xml 檔案做為範本) 。 標準成員是由名稱為 PSStandardMembers 的節點所定義。 這些定義可讓其他 Cmdlet 和 Windows PowerShell 執行時間以一致的方式處理您的物件。

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>定義要當做參數使用的 ObjectMembers

如果您要設計 Cmdlet 的物件，請確定其成員會直接對應至將使用它的 Cmdlet 參數。 此對應可讓物件輕鬆地傳送至管線，並從一個 Cmdlet 傳遞給另一個 Cmdlet。

由 Cmdlet 所傳回之預先存在的 .NET Framework 物件，通常會遺失腳本開發人員或使用者所需的一些重要或方便的成員。 這些遺漏的成員對於顯示和建立正確的成員名稱而言特別重要，因為可以將物件正確地傳遞至管線。 建立自訂的 Types.ps1xml 檔案，以記錄這些必要的成員。 當您建立這個檔案時，我們建議採用下列命名慣例： *<Your_Product_Name>*.Types.ps1xml。

例如，您可以將 `Mode` 腳本屬性加入 [FileInfo](/dotnet/api/System.IO.FileInfo) 類型，更清楚地顯示檔案的屬性。 此外，您可以將 `Count` 別名屬性加入至 [system.object](/dotnet/api/System.Array) 類型，以允許一致地使用該屬性名稱 (而不是 `Length`) 。

##### <a name="implement-the-icomparable-interface"></a>執行 IComparable 介面

在所有輸出物件上，執行 [system.object](/dotnet/api/System.IComparable) 介面。
這可讓輸出物件輕鬆地輸送至不同的排序和分析 Cmdlet。

##### <a name="update-display-information"></a>更新顯示資訊

如果物件的顯示未提供預期的結果，請建立該物件的自訂 *\<YourProductName>*.Format.ps1xml 檔。

### <a name="support-well-defined-pipeline-input-sc02"></a> (SC02) 支援定義完善的管線輸入

#### <a name="implement-for-the-middle-of-a-pipeline"></a>在管線中間執行

執行 Cmdlet，假設它將從管線的中間呼叫 (也就是，其他 Cmdlet 會產生其輸入或使用其輸出) 。 例如，您可能會假設 `Get-Process` Cmdlet （因為它會產生資料）只會用來做為管線中的第一個 Cmdlet。
不過，因為此 Cmdlet 是針對管線的中間所設計，此 Cmdlet 可讓管線中的先前 Cmdlet 或資料指定要取出的進程。

#### <a name="support-input-from-the-pipeline"></a>支援來自管線的輸入

在 Cmdlet 的每個參數集，至少包含一個支援管線輸入的參數。 管線輸入的支援可讓使用者抓取資料或物件、將資料傳送到正確的參數集，並將結果直接傳遞給 Cmdlet。

如果 **參數** 屬性包含 `ValueFromPipeline` 關鍵字、 `ValueFromPipelineByPropertyName` 關鍵字屬性或其宣告中的兩個關鍵字，參數就會接受來自管線的輸入。 如果參數集中沒有任何參數支援 `ValueFromPipeline` 或 `ValueFromPipelineByPropertyName` 關鍵字，則 Cmdlet 不會有意義地放在另一個 Cmdlet 之後，因為它會忽略任何管線輸入。

#### <a name="support-the-processrecord-method"></a>支援 ProcessRecord 方法

若要接受管線中上述 Cmdlet 的所有記錄，您的 Cmdlet 必須執行 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法。 Windows PowerShell 會多次呼叫這個方法，每一筆記錄傳送至您的 Cmdlet。

### <a name="write-single-records-to-the-pipeline-sc03"></a>將單一記錄寫入管線 (SC03) 

當 Cmdlet 傳回物件時，此 Cmdlet 應該在產生物件時立即將其寫入。 Cmdlet 不應該保留它們，以便將它們緩衝至組合的陣列中。 以輸入的形式接收物件的 Cmdlet 將能夠處理、顯示或處理並顯示輸出物件，而不會有延遲。 一次產生一個輸出物件的指令程式，應該呼叫 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 方法。 以批次方式產生輸出物件的 Cmdlet (例如，因為基礎 API 會傳回輸出物件的陣列) 應該呼叫 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 方法，並將其第二個參數設定為 `true` 。

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>將 Cmdlet Case-Insensitive，並 Case-Preserving (SC04) 

根據預設，Windows PowerShell 本身不區分大小寫。 不過，因為它會處理許多預先存在的系統，Windows PowerShell 確實會保留大小寫，以方便操作和相容性。
換句話說，如果字元是以大寫字母提供，Windows PowerShell 會將其保留為大寫字母。 針對可正常運作的系統，Cmdlet 必須遵循此慣例。 可能的話，應該以不區分大小寫的方式操作。 不過，它應該會針對稍後在命令或管線中發生的 Cmdlet 保留原始案例。

## <a name="see-also"></a>另請參閱

[必要的開發指導方針](./required-development-guidelines.md)

[建議性開發指導方針](./advisory-development-guidelines.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
