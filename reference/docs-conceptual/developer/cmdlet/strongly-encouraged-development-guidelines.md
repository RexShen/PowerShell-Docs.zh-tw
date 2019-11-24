---
title: 強烈建議的開發指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369337"
---
# <a name="strongly-encouraged-development-guidelines"></a>強烈建議使用的開發指導方針

本節說明您在撰寫 Cmdlet 時應遵循的指導方針。 它們會分成設計 Cmdlet 的指導方針，以及撰寫 Cmdlet 程式碼的指導方針。 您可能會發現這些指導方針不適用於每個案例。 不過，如果它們已套用，而您未遵循這些指導方針，則使用者在使用您的 Cmdlet 時可能會有不佳的體驗。

## <a name="design-guidelines"></a>設計指導方針

- [將特定名詞用於 Cmdlet 名稱（SD01）](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [針對 Cmdlet 名稱使用 Pascal 大小寫（SD02）](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [參數設計指導方針（SD03）](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [為使用者提供意見反應（SD04）](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [建立 Cmdlet 說明檔（SD05）](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>程式碼方針

- [編碼參數（SC01）](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [支援妥善定義的管線輸入（SC02）](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [將單一記錄寫入管線（SC03）](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [使 Cmdlet 不區分大小寫，並保留大小寫（SC04）](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>設計指導方針

設計 Cmdlet 時應遵循下列指導方針，以確保使用您的 Cmdlet 和其他 Cmdlet 的使用者體驗一致。 當您找到適用于您情況的設計指導方針時，請務必查看類似方針的程式碼方針。

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>將特定名詞用於 Cmdlet 名稱（SD01）

Cmdlet 命名中使用的名詞必須非常明確，讓使用者能夠探索您的 Cmdlet。 以產品名稱的簡短版本為一般名詞（例如 "server"）加上前置詞。 例如，如果名詞指的是執行 Microsoft SQL Server 實例的伺服器，請使用名詞，例如 "SQLServer"。 結合特定名詞和核准動詞的簡短清單，可讓使用者快速探索並預測功能，同時避免 Cmdlet 名稱重複。

為了加強使用者體驗，您為 Cmdlet 名稱選擇的名詞應為單數。 例如，使用 `Get-Process` 的名稱，而不是**Get 進程**。 最好是針對所有 Cmdlet 名稱遵循此規則，即使 Cmdlet 可能會在一個以上的專案上運作。

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>針對 Cmdlet 名稱使用 Pascal 大小寫（SD02）

針對參數名稱使用 Pascal 大小寫。 換句話說，會將動詞的第一個字母和名詞中使用的所有詞彙變成大寫。 例如，「`Clear-ItemProperty`」。

### <a name="parameter-design-guidelines-sd03"></a>參數設計指導方針（SD03）

Cmdlet 所需的參數會接收其必須運作的資料，以及指示用來判斷作業特性之資訊的參數。 例如，Cmdlet 可能會有從管線接收資料的 `Name` 參數，而 Cmdlet 可能會有 `Force` 參數，以指出 Cmdlet 可以強制執行其作業。 Cmdlet 可以定義的參數數目沒有任何限制。

#### <a name="use-standard-parameter-names"></a>使用標準參數名稱

您的 Cmdlet 應該使用標準參數名稱，讓使用者可以快速判斷特定參數的意義。 如果需要更具體的名稱，請使用標準參數名稱，然後將更具體的名稱指定為別名。 例如，`Get-Service` Cmdlet 的參數具有泛型名稱（`Name`）和更特定的別名（`ServiceName`）。 這兩個詞彙都可以用來指定參數。

如需參數名稱及其資料類型的詳細資訊，請參閱[Cmdlet 參數名稱和功能方針](./standard-cmdlet-parameter-names-and-types.md)。

#### <a name="use-singular-parameter-names"></a>使用單數參數名稱

請避免針對其值為單一專案的參數使用複數名稱。 這包括接受陣列或清單的參數，因為使用者可能會提供只有一個元素的陣列或清單。

複數參數名稱僅適用于參數值一律為多元素值的情況。 在這些情況下，Cmdlet 應該確認已提供多個元素，而如果未提供多個元素，Cmdlet 應該會向使用者顯示警告。

#### <a name="use-pascal-case-for-parameter-names"></a>針對參數名稱使用 Pascal 大小寫

針對參數名稱使用 Pascal 大小寫。 換句話說，在參數名稱中，將每個單字的第一個字母變成大寫，包括名稱的第一個字母。 例如，參數名稱 `ErrorAction` 會使用正確的大小寫。 下列參數名稱使用了不正確的大小寫：

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>接受選項清單的參數

有兩種方式可以建立可從一組選項中選取其值的參數。

- 定義指定有效值的列舉類型（或使用現有的列舉類型）。 然後，使用列舉類型來建立該類型的參數。

- 將**ValidateSet**屬性新增至參數宣告。 如需這個屬性的詳細資訊，請參閱[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告。

#### <a name="use-standard-types-for-parameters"></a>針對參數使用標準類型

若要確保與其他 Cmdlet 的一致性，請盡可能使用標準類型做為參數。 如需有關應用於不同參數之類型的詳細資訊，請參閱[標準 Cmdlet 參數名稱和類型](./standard-cmdlet-parameter-names-and-types.md)。 本主題提供數個主題的連結，說明標準參數群組的名稱和 .NET Framework 類型，例如「活動參數」。

#### <a name="use-strongly-typed-net-framework-types"></a>使用強型別 .NET Framework 類型

參數應該定義為 .NET Framework 類型，以提供更佳的參數驗證。 例如，限制為一組值中某個值的參數，應該定義為列舉類型。 若要支援統一資源識別元（URI）值，請將參數定義為[system.string 類型。](/dotnet/api/System.Uri) 針對所有但自由格式的文字屬性，請避免基本的字串參數。

#### <a name="use-consistent-parameter-types"></a>使用一致的參數類型

當多個 Cmdlet 使用相同的參數時，請一律使用相同的參數類型。  例如，如果 `Process` 參數是一個 Cmdlet 的[Int16](/dotnet/api/System.Int16)類型，請勿將另一個 Cmdlet 的 `Process` 參數設為[system.string 類型。](/dotnet/api/System.UInt16)

#### <a name="parameters-that-take-true-and-false"></a>接受 True 和 False 的參數

如果您的參數只會 `true` 和 `false`，請將參數定義為[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型。 在命令中指定切換參數時，會將它視為 `true`。 如果命令中未包含參數，Windows PowerShell 會將參數的值視為 `false`。 不要定義布林值參數。

如果您的參數需要區分3個值： $true、$false 和「未指定」，則請將類型的參數定義為可為 Null\<bool >。  當 Cmdlet 可以修改物件的布林值屬性時，通常會發生第三個「未指定」的值。 在此情況下，「未指定」表示不會變更屬性的目前值。

#### <a name="support-arrays-for-parameters"></a>支援參數陣列

使用者通常必須針對多個引數執行相同的操作。 對於這些使用者，Cmdlet 應接受陣列做為參數輸入，讓使用者可以將引數當做 Windows PowerShell 變數傳遞至參數。 例如，[取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)Cmdlet 會針對識別要抓取之進程名稱的字串使用陣列。

#### <a name="support-the-passthru-parameter"></a>支援 PassThru 參數

根據預設，許多修改系統的 Cmdlet （例如，[停止進程](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)Cmdlet）會作為物件的「接收」，而不會傳回結果。 這些 Cmdlet 應該會執行 `PassThru` 參數，以強制 Cmdlet 傳回物件。 指定 `PassThru` 參數時，指令程式會使用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法的呼叫來傳回物件（object）。 例如，下列命令會停止 Calc 進程，並將產生的進程傳遞至管線。

```powershell
Stop-Process calc -passthru
```

在大部分情況下，新增、設定和新的 Cmdlet 都應該支援 `PassThru` 參數。

#### <a name="support-parameter-sets"></a>支援參數集

Cmdlet 主要是用來完成單一目的。 不過，通常會有一種以上的方法來描述作業或操作目標。 例如，處理常式可能會以其名稱、其識別碼或處理常式物件來識別。 Cmdlet 應支援其目標的所有合理標記法。 一般來說，此 Cmdlet 會藉由指定一組一起運作的參數（稱為參數集）來滿足這項需求。 單一參數可以屬於任意數目的參數集。 如需參數集的詳細資訊，請參閱[Cmdlet 參數集](./cmdlet-parameter-sets.md)。

當您指定參數集時，請將設定中的一個參數設定為 ValueFromPipeline。 如需如何宣告**參數**屬性的詳細資訊，請參閱[ParameterAttribute](./parameter-attribute-declaration.md)宣告。

使用參數集時，預設參數集是由**Cmdlet**屬性所定義。 預設參數集應包含最可能在互動式 Windows PowerShell 會話中使用的參數。 如需如何宣告**Cmdlet**屬性的詳細資訊，請參閱[CmdletAttribute](./cmdlet-attribute-declaration.md)宣告。

### <a name="provide-feedback-to-the-user-sd04"></a>為使用者提供意見反應（SD04）

使用本節中的指導方針，為使用者提供意見反應。 這項意見反應可讓使用者知道系統中發生了什麼事，並做出更好的管理決策。

Windows PowerShell 執行時間可讓使用者藉由設定喜好設定變數，來指定如何處理每次呼叫 `Write` 方法的輸出。 使用者可以設定數個喜好設定變數，包括判斷系統是否應顯示資訊的變數，以及判斷系統是否應在採取進一步動作之前查詢使用者的變數。

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>支援 WriteWarning、WriteVerbose 和 WriteDebug 方法

當 Cmdlet 即將執行可能會產生非預期結果的作業時，Cmdlet 應該會呼叫[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法。 例如，如果 Cmdlet 即將覆寫唯讀檔案，則 Cmdlet 應該呼叫這個方法。

當使用者需要有關 Cmdlet 所執行作業的一些詳細資料時，Cmdlet 應呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。 例如，如果 Cmdlet 作者覺得有一些案例可能需要更多有關 Cmdlet 執行內容的資訊，則 Cmdlet 應呼叫此資訊。

當開發人員或產品支援工程師必須瞭解哪些已損毀 Cmdlet 作業時，此 Cmdlet 應該會呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。 Cmdlet 不需要在呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的相同程式碼中呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法，因為 `Debug` 參數會同時顯示這兩組資訊，而這是不必要的。

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>針對花費較長時間的作業支援 WriteProgress

需要很長時間才能完成，且無法在背景中執行的 Cmdlet 作業，應該透過定期呼叫[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法來支援進度報告。

#### <a name="use-the-host-interfaces"></a>使用主機介面

在此情況下，Cmdlet 必須直接與使用者通訊，而不是使用不同的 Write，或應由[system.web](/dotnet/api/System.Management.Automation.Cmdlet)類別支援的方法。 在此情況下，此 Cmdlet 應該衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別，並使用[PSCmdlet *. Host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host)屬性。 這個屬性支援不同層級的通訊類型，包括 PromptForChoice、Prompt 和 WriteLine/ReadLine 類型。 在最特定的層級，它也提供讀取和寫入個別金鑰以及處理緩衝區的方式。

除非 Cmdlet 是特別設計來產生圖形化使用者介面（GUI），否則不應使用[PSCmdlet *](/dotnet/api/System.Management.Automation.PSCmdlet.Host)屬性來略過主機。 用來產生 GUI 的 Cmdlet 範例是[Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) Cmdlet。

> [!NOTE]
> Cmdlet 不應使用[System. 主控台](/dotnet/api/System.Console)API。

### <a name="create-a-cmdlet-help-file-sd05"></a>建立 Cmdlet 說明檔（SD05）

針對每個 Cmdlet 元件，建立包含 Cmdlet 相關資訊的 Help .xml 檔案。 這項資訊包含 Cmdlet 的描述、Cmdlet 參數的描述、Cmdlet 使用的範例，以及更多。

## <a name="code-guidelines"></a>程式碼方針

撰寫 Cmdlet 的程式碼時，應遵循下列指導方針，以確保使用您的 Cmdlet 和其他 Cmdlet 的使用者體驗一致。 當您找到適用于您情況的程式碼指導方針時，請務必查看類似方針的設計方針。

### <a name="coding-parameters-sc01"></a>編碼參數（SC01）

藉由宣告以**參數**屬性裝飾之 Cmdlet 類別的公用屬性來定義參數。 參數不一定要是 Cmdlet 的衍生 .NET Framework 類別的靜態成員。 如需如何宣告**參數**屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。

#### <a name="support-windows-powershell-paths"></a>支援 Windows PowerShell 路徑

Windows PowerShell 路徑是標準化命名空間存取的機制。 當您將 Windows PowerShell 路徑指派給 Cmdlet 中的參數時，使用者可以定義自訂的「磁片磁碟機」作為特定路徑的快捷方式。 當使用者指定這種磁片磁碟機時，可以用一致的方式來使用儲存的資料（例如登錄中的資料）。

如果您的 Cmdlet 允許使用者指定檔案或資料來源，則應該定義[system.string](/dotnet/api/System.String)類型的參數。 如果支援多個磁片磁碟機，則類型應為數組。 參數的名稱應該是 `Path`，並具有 `PSPath`的別名。 此外，`Path` 參數應該支援萬用字元。 如果不需要萬用字元的支援，請定義 `LiteralPath` 參數。

如果指令程式讀取或寫入的資料必須是檔案，則 Cmdlet 應該接受 Windows PowerShell 路徑輸入，而此 Cmdlet 應該使用[Sessionstate](/dotnet/api/System.Management.Automation.SessionState.Path)屬性將 windows powershell 路徑轉譯成檔案系統可辨識的路徑。 特定的機制包括下列方法：

- [System.web. PSCmdlet. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.web. PSCmdlet. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.web. PathIntrinsics. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.web. PathIntrinsics. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

如果 Cmdlet 讀取或寫入的資料只是一組字串，而不是檔案，則 Cmdlet 應該使用提供者內容資訊（`Content` 成員）來進行讀取和寫入。 這種資訊是從[CmdletProvider. InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider)屬性取得。 這些機制可讓其他資料存放區參與讀取和寫入資料。

#### <a name="support-wildcard-characters"></a>支援萬用字元

Cmdlet 應盡可能支援萬用字元。 Cmdlet 中的許多地方都會出現萬用字元的支援（尤其是當參數接受字串從一組物件識別一個物件時）。 例如，來自[StopProc 教學](./stopproc-tutorial.md)課程的範例**Stop-Proc** Cmdlet 會定義 `Name` 參數，以處理代表進程名稱的字串。 此參數支援萬用字元，讓使用者可以輕鬆地指定要停止的處理常式。

當提供萬用字元的支援時，Cmdlet 作業通常會產生陣列。 有時候，支援陣列並不合理，因為使用者可能一次只會使用單一專案。 例如，[設定位置](/powershell/module/Microsoft.PowerShell.Management/Set-Location)Cmdlet 不需要支援陣列，因為使用者只會設定一個位置。 在此情況下，Cmdlet 仍然支援萬用字元，但會強制解析成單一位置。

如需萬用字元模式的詳細資訊，請參閱[在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

#### <a name="defining-objects"></a>定義物件

本節包含定義 Cmdlet 和擴充現有物件之物件的指導方針。

##### <a name="define-standard-members"></a>定義標準成員

定義標準成員以擴充自訂 types.ps1xml 檔案中的物件類型（使用 Windows PowerShell types.ps1xml 檔案作為範本）。 標準成員是由名稱為 PSStandardMembers 的節點所定義。 這些定義可讓其他 Cmdlet 和 Windows PowerShell 執行時間以一致的方式處理您的物件。

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>定義要當做參數使用的 ObjectMembers

如果您要設計 Cmdlet 的物件，請確定其成員直接對應至將使用它的 Cmdlet 的參數。 此對應可讓物件輕鬆地傳送至管線，並從一個 Cmdlet 傳遞至另一個指令。

Cmdlet 所傳回的預先存在 .NET Framework 物件經常遺漏腳本開發人員或使用者所需的一些重要或方便的成員。 這些遺漏的成員對於顯示和建立正確的成員名稱而言特別重要，因此可以將物件正確地傳遞至管線。 建立自訂的 types.ps1xml 檔案，以記錄這些必要的成員。 當您建立這個檔案時，我們建議採用下列命名慣例： *< Your_Product_Name >* 。類型. types.ps1xml。

例如，您可以將 `Mode` 腳本屬性新增至[FileInfo](/dotnet/api/System.IO.FileInfo)類型，以更清楚地顯示檔案的屬性。 此外，您可以將 `Count` alias 屬性加入至 system.string[類型，](/dotnet/api/System.Array)以允許一致地使用該屬性名稱（而不是 `Length`）。

##### <a name="implement-the-icomparable-interface"></a>執行 IComparable 介面

在所有輸出物件上執行[system.icomparable](/dotnet/api/System.IComparable)介面。 這可讓輸出物件輕鬆地輸送至各種排序和分析 Cmdlet。

##### <a name="update-display-information"></a>更新顯示資訊

如果物件的顯示未提供預期的結果，請建立自訂的 *\<YourProductName >* 。該物件的 types.ps1xml 檔案格式。

### <a name="support-well-defined-pipeline-input-sc02"></a>支援妥善定義的管線輸入（SC02）

#### <a name="implement-for-the-middle-of-a-pipeline"></a>在管線中間執行

執行 Cmdlet，假設它會從管線中間呼叫（也就是，其他 Cmdlet 會產生其輸入或使用其輸出）。 例如，假設 `Get-Process` Cmdlet 會產生資料，則只會當做管線中的第一個 Cmdlet 使用。 不過，由於此 Cmdlet 是針對管線的中間所設計，因此此 Cmdlet 可讓管線中的先前 Cmdlet 或資料指定要抓取的處理常式。

#### <a name="support-input-from-the-pipeline"></a>支援來自管線的輸入

在 Cmdlet 的每個參數集中，至少包含一個支援管線輸入的參數。 管線輸入的支援可讓使用者抓取資料或物件、將其傳送至正確的參數集，以及直接將結果傳遞給 Cmdlet。

如果**參數**屬性包含 `ValueFromPipeline` 關鍵字、`ValueFromPipelineByPropertyName` 關鍵字屬性或其宣告中的兩個關鍵字，則參數會接受管線中的輸入。 如果參數集中沒有參數支援 `ValueFromPipeline` 或 `ValueFromPipelineByPropertyName` 關鍵字，Cmdlet 就無法有意義地放在另一個 Cmdlet 之後，因為它會忽略任何管線輸入。

#### <a name="support-the-processrecord-method"></a>支援 ProcessRecord 方法

若要接受管線中上述 Cmdlet 的所有記錄，您的 Cmdlet 必須執行[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 Windows PowerShell 會多次呼叫此方法一次，每一筆記錄傳送至您的 Cmdlet。

### <a name="write-single-records-to-the-pipeline-sc03"></a>將單一記錄寫入管線（SC03）

當 Cmdlet 傳回物件時，Cmdlet 應該會在產生物件時立即寫入。 Cmdlet 不應保留它們，以便將它們緩衝到合併的陣列中。 接收物件做為輸入的 Cmdlet 之後，就能夠處理、顯示或處理和顯示輸出物件，而不會延遲。 一次會產生一個輸出物件的 Cmdlet，應呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 以批次方式產生輸出物件的 Cmdlet （例如，因為基礎 API 會傳回輸出物件的陣列），應呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法，並將其第二個參數設定為 `true`。

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>使 Cmdlet 不區分大小寫，並保留大小寫（SC04）

根據預設，Windows PowerShell 本身不會區分大小寫。 不過，因為它處理許多預先存在的系統，所以 Windows PowerShell 確實會保留大小寫，以方便操作和相容。 換句話說，如果以大寫字母提供字元，Windows PowerShell 會將它保留為大寫字母。 若要讓系統順利運作，Cmdlet 必須遵循此慣例。 可能的話，它應該會以不區分大小寫的方式運作。 不過，它應該保留在命令或管線中稍後發生之 Cmdlet 的原始案例。

## <a name="see-also"></a>另請參閱

[必要的開發指導方針](./required-development-guidelines.md)

[諮詢開發指導方針](./advisory-development-guidelines.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
