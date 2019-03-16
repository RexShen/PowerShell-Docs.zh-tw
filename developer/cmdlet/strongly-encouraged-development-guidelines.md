---
title: 強烈鼓勵開發指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057717"
---
# <a name="strongly-encouraged-development-guidelines"></a>強烈建議使用的開發指導方針

本章節描述當您撰寫您的 cmdlet 時，您應該遵循的指導方針。 分成設計的 cmdlet 和撰寫程式的指令程式碼的指導方針的指導方針。 您可能會發現，這些指導方針不是適用於每個案例。 不過，如果它們會套用，而且您不遵循這些指導方針，您的使用者可能不佳的體驗在使用您的 cmdlet 時。

## <a name="design-guidelines"></a>設計指導方針

- [使用一個特定名詞的 Cmdlet 名稱 (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Cmdlet 名稱 (SD02) 使用 Pascal 大小寫](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [參數設計指導方針 (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [提供意見給使用者 (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [建立 Cmdlet 說明檔 (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>程式碼的指導方針

- [程式碼參數 (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [支援妥善定義的管線輸入 (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [將單一記錄寫入管線 (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [讓 Cmdlet 不區分大小寫和保留大小寫 (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>設計指導方針

設計以確保一致的使用者經驗之間使用您的 cmdlet 和其他 cmdlet 的 cmdlet 時，應該遵循下列指導方針。 當您找到適用於您情況的設計指導方針時，請務必查看類似的指導方針中的程式碼的方針。

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>使用一個特定名詞的 Cmdlet 名稱 (SD01)

Cmdlet 命名中使用的名詞，需要有非常明確，讓使用者可以探索您的 cmdlet。 泛型的名詞，例如 「 伺服器 」 使用一個精簡版本的產品名稱的前置詞。 比方說，如果名詞指的是正在執行 Microsoft SQL Server 執行個體的伺服器，使用的名詞，例如"SQLServer"。 特定名詞的組合和核准的動詞命令的簡短清單可讓使用者快速探索，並預期功能，同時避免重複的 cmdlet 名稱。

若要增強使用者體驗，您選擇的 cmdlet 名稱的名詞應該是單數。 例如，使用名稱`Get-Process`而非**取得處理序**。 最好的方式是遵循所有的 cmdlet 名稱，此規則，即使指令程式很可能要採取多個項目。

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Cmdlet 名稱 (SD02) 使用 Pascal 大小寫

參數名稱使用 pascal 命名法大小寫。 換句話說，充分利用動詞和名詞中使用的所有詞彙的第一個字母。 例如，"`Clear-ItemProperty`」。

### <a name="parameter-design-guidelines-sd03"></a>參數設計指導方針 (SD03)

指令程式必須在收到它必須在其運作，資料的參數和參數，表示用來判斷作業的特性的資訊。 比方說，cmdlet 可能會有`Name`接收資料管線，與此 cmdlet 的參數可能會有`Force`表示執行其作業時，會強制此 cmdlet 的參數。 Cmdlet 可以定義的參數數目沒有限制。

#### <a name="use-standard-parameter-names"></a>使用標準的參數名稱

您的 cmdlet 應該使用標準的參數名稱，好讓使用者可以快速判斷特定參數的表示。 如果需要更特定的名稱，請使用標準的參數名稱，，，然後指定做為別名的 更為具體的名稱。 例如， `Get-Service` cmdlet 有一個參數具有泛型名稱 (`Name`) 和更具體的別名 (`ServiceName`)。 這兩個詞彙可用來指定參數。

如需有關參數名稱和其資料類型的詳細資訊，請參閱[Cmdlet 的參數名稱和功能的指導方針](./standard-cmdlet-parameter-names-and-types.md)。

#### <a name="use-singular-parameter-names"></a>使用單數的參數名稱

請避免使用複數名稱參數的值是單一項目。 這包括參數陣列，或清單，因為使用者可能會提供陣列或清單中只有一個元素的清單。

只有在這些參數的值是一律多項目值的情況下，應該使用複數的參數名稱。 在這些情況下，此指令程式應該確認提供多個項目，且 cmdlet 應該會顯示警告給使用者如果不提供多個項目。

#### <a name="use-pascal-case-for-parameter-names"></a>參數名稱使用 pascal 命名法大小寫

參數名稱使用 pascal 命名法大小寫。 換句話說，將參數名稱，包括名稱的第一個字母中的每個單字的第一個字母的大寫。 例如，參數名稱`ErrorAction`使用正確的大小寫。 下列的參數名稱使用大小寫不正確：

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>參數選項的清單

有兩種方式可建立其值可以從一組選項中選取的參數。

- 定義列舉類型 （或使用現有的列舉類型） 指定有效的值。 然後，使用的列舉型別來建立該類型的參數。

- 新增**ValidateSet**屬性參數宣告。 如需有關這個屬性的詳細資訊，請參閱 < [ValidateSet 屬性宣告](./validateset-attribute-declaration.md)。

#### <a name="use-standard-types-for-parameters"></a>使用標準的類型參數

若要確保與其他 cmdlet 保持一致，使用標準類型參數，其中以往可能。 如需應該使用不同的參數類型的詳細資訊，請參閱[標準的 Cmdlet 參數名稱和型別](./standard-cmdlet-parameter-names-and-types.md)。 本主題提供數個描述的名稱和群組的標準參數，例如 「 活動參數 」 的.NET Framework 類型的主題連結。

#### <a name="use-strongly-typed-net-framework-types"></a>使用強型別.NET Framework 型別

參數應定義為.NET Framework 型別，以提供更好的參數驗證。 例如，從一組值限制為一個值的參數應該定義為列舉型別。 若要支援的統一資源識別元 (URI) 值，定義為參數[System.Uri](/dotnet/api/System.Uri)型別。 避免以外的所有自由格式文字屬性的基本字串參數。

#### <a name="use-consistent-parameter-types"></a>使用一致的參數類型

當多個指令程式使用相同的參數時，一律使用相同的參數類型。  例如，如果`Process`參數是[System.Int16](/dotnet/api/System.Int16)輸入一個 cmdlet，則請勿`Process`另一個 cmdlet 的參數[System.Uint16](/dotnet/api/System.UInt16)型別。

#### <a name="parameters-that-take-true-and-false"></a>參數為 True 和 False

如果您的參數只接受`true`並`false`，此參數定義為類型[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)。 切換參數會被視為`true`當命令中指定。 如果參數未包含在命令中，Windows PowerShell，將會視為是參數的值`false`。 未定義布林值參數。

如果您的參數需要 3 個值之間的區別： $true、 $false 和 「 未指定"，然後將參數定義型別可為 Null\<bool >。  第 3 需要，「 未指定"的值通常發生於此指令程式可以修改物件的布林值屬性。 在此情況下 「 未指定"表示不會變更屬性的目前值。

#### <a name="support-arrays-for-parameters"></a>支援的參數陣列

通常，使用者必須執行相同的作業，針對多個引數。 針對這些使用者，cmdlet 應接受陣列做為輸入，讓使用者可以將引數傳遞至 Windows PowerShell 變數作為參數的參數。 例如， [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 用於識別要擷取的處理序名稱的字串陣列。

#### <a name="support-the-passthru-parameter"></a>支援的 PassThru 參數

根據預設，許多 cmdlet，修改系統，例如[Stop-process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)指令程式，作為 「 接收 」 的物件，並不會傳回結果。 這些 cmdlet 應該實作`PassThru`參數來強制 cmdlet 傳回的物件。 當`PassThru`指定參數，cmdlet 會傳回物件使用呼叫[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 例如，下列命令停止 Calc 處理程序，並將結果的程序傳遞到管線。

```powershell
Stop-Process calc -passthru
```

在大部分情況下，新增、 集和新的 cmdlet 應該支援`PassThru`參數。

#### <a name="support-parameter-sets"></a>支援的參數集

Cmdlet 被用來完成單一用途。 不過，還有常見問題描述作業或作業目標的多個方法。 比方說，其名稱、 其識別項，或處理程序物件，可能會識別處理程序。 此 cmdlet 應支援其目標合理的表示法。 一般來說，此 cmdlet 會滿足此需求，藉由指定的參數 （稱為參數集） 一起運作的設定。 單一參數可以屬於任何數目的參數集合。 如需參數集的詳細資訊，請參閱[指令程式參數設定](./cmdlet-parameter-sets.md)。

當您指定的參數集時，請 ValueFromPipeline 來集中設定只有一個參數。 如需如何宣告**參數**屬性，請參閱[ParameterAttribute 宣告](./parameter-attribute-declaration.md)。

當使用參數集時，所定義的預設參數集**Cmdlet**屬性。 預設參數集應該包含最可能使用互動式的 Windows PowerShell 工作階段中的參數。 如需如何宣告**Cmdlet**屬性，請參閱[CmdletAttribute 宣告](./cmdlet-attribute-declaration.md)。

### <a name="provide-feedback-to-the-user-sd04"></a>提供意見給使用者 (SD04)

使用本節中的指導方針，提供回饋給使用者。 此意見反應可讓使用者知道什麼系統中發生的並做出更好的系統管理決策。

Windows PowerShell 執行階段可讓使用者指定如何處理每次呼叫的輸出`Write`藉由設定 喜好設定變數的方法。 使用者可以設定數個喜好設定變數，包括判斷系統是否應該顯示資訊，以及判斷系統是否應該查詢使用者再採取進一步的動作變數的變數。

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>支援 WriteWarning、 WriteVerbose 和 WriteDebug 方法

指令程式應該呼叫[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法時執行的作業可能會有非預期的結果，此 cmdlet。 比方說，指令程式應該呼叫這個方法，此 cmdlet 是否要覆寫唯讀檔案。

指令程式應該呼叫[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法，當使用者要求有關此指令程式會執行的工作詳細資料。 比方說，指令程式應該呼叫這項資訊，如果 cmdlet 的作者都有可能會要求有關此指令程式會執行的工作的詳細資訊的情況。

此指令程式應該呼叫[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)當開發人員或產品的支援工程師必須了解什麼有損毀 cmdlet 作業的方法。 它不需要此指令程式來呼叫[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法中呼叫的程式碼[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法因為`Debug`參數提供兩個資訊集。

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>支援 WriteProgress 很耗時的作業

Cmdlet 作業很長的時間才能完成，而且不能在背景執行的採用應該支援進度報告透過定期呼叫[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。

#### <a name="use-the-host-interfaces"></a>使用主應用程式介面

有時候，cmdlet 必須直接與使用者通訊而不是使用各種書寫或應該支援的方法[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別。 在此情況下，此 cmdlet 應該衍生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別，並且使用[System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host)屬性。 此屬性支援不同層級的通訊類型，包括 PromptForChoice、 提示和 WriteLine/ReadLine 的型別。 在最特定的層級，它也提供方法來讀取和寫入個別的索引鍵，並處理緩衝區。

除非 cmdlet 專為產生的圖形化使用者介面 (GUI)，它應該不使用略過主機[System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host)屬性。 舉例來說，設計來產生 GUI 指令程式可[Out-gridview](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet。

> [!NOTE]
> 不應該使用 Cmdlet [System.Console](/dotnet/api/System.Console) API。

### <a name="create-a-cmdlet-help-file-sd05"></a>建立 Cmdlet 說明檔 (SD05)

每個 cmdlet，為組件建立 Help.xml 檔案，其中包含有關此指令程式的資訊。 這項資訊包含 cmdlet，cmdlet 的參數的描述，範例 cmdlet 的使用，以及更多的描述。

## <a name="code-guidelines"></a>程式碼的指導方針

撰寫程式碼以確保一致的使用者經驗之間使用您的 cmdlet 和其他 cmdlet 的 cmdlet 時，應該遵循下列指導方針。 當您找到適用於您情況的程式碼指導方針時，請務必查看類似的指導方針的設計方針。

### <a name="coding-parameters-sc01"></a>程式碼參數 (SC01)

藉由宣告以裝飾在 cmdlet 類別的公用屬性來定義參數**參數**屬性。 參數可能沒有 cmdlet 衍生的.NET Framework 類別的靜態成員。 如需如何宣告**參數**屬性，請參閱[參數的屬性宣告](./parameter-attribute-declaration.md)。

#### <a name="support-windows-powershell-paths"></a>支援 Windows PowerShell 路徑

Windows PowerShell 路徑會是正規化命名空間的存取權的機制。 當您指派的 Windows PowerShell 路徑中 cmdlet 的參數時，使用者可以定義自訂的 「 磁碟機 」，可作為特定路徑的捷徑。 當使用者指定這類磁碟機時，預存的資料，例如在登錄中的資料可以用於以一致的方式。

如果您的指令程式可讓使用者指定的檔案或資料來源，它應該定義類型的參數[System.String](/dotnet/api/System.String)。 如果支援多個磁碟機，則類型應該是陣列。 參數的名稱應該是`Path`，使用的別名`PSPath`。 此外，`Path`參數應該支援萬用字元。 如果支援萬用字元並不需要，定義`LiteralPath`參數。

如果指令程式會讀取或寫入的資料必須是檔案、 指令程式應該接受 Windows PowerShell 路徑輸入，而且應該使用此 cmdlet [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path)屬性，以轉譯 Windows為路徑的檔案系統可辨識的 PowerShell 路徑。 特定的機制包括下列方法：

- [System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

指令程式會讀取或寫入的資料如果只是一組字串，而不是檔案時，此指令程式應該使用提供者的內容資訊 (`Content`成員) 來讀取和寫入。 這項資訊取自[System.Management.Automation.Provider.CmdletProvider.InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider)屬性。 這些機制讓參與讀取和寫入資料的其他資料存放區。

#### <a name="support-wildcard-characters"></a>支援萬用字元

指令程式應該盡可能支援萬用字元。 （尤其是當參數接受字串，以識別一組物件中的一個物件），就會在 cmdlet 中的許多地方發生萬用字元的支援。 例如，範例**停止程序**cmdlet，從[StopProc 教學課程](./stopproc-tutorial.md)定義`Name`參數，以處理表示處理程序名稱的字串。 這個參數支援萬用字元，因此使用者可以輕鬆地指定處理程序停止。

當支援萬用字元的字元可用，cmdlet 作業通常會產生陣列。 有時候，並不合理支援陣列，因為使用者可能會一次使用單一項目。 例如， [Set-location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet 就不需要支援陣列，因為使用者設定的就單一位置。 在此情況下，cmdlet 仍然支援萬用字元，但它會強制解析至單一位置。

如需萬用字元字元模式的詳細資訊，請參閱[Cmdlet 參數支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

#### <a name="defining-objects"></a>定義物件

本章節包含的 cmdlet 以及擴充現有物件的物件定義的指導方針。

##### <a name="define-standard-members"></a>定義標準的成員

定義標準的成員，來擴充自訂的 Types.ps1xml 檔案 （使用 Windows PowerShell Types.ps1xml 檔案做為範本） 中的物件類型。 標準的成員會定義具有名稱 PSStandardMembers 的節點。 其他指令程式和 Windows PowerShell 執行階段以一致的方式與您的物件，可讓這些定義。

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>定義 ObjectMembers 來做為參數

如果您要設計的 cmdlet 的物件，請確定，其成員會直接對應到就會使用此 cmdlet 的參數。 此對應可讓您輕鬆地傳送至管線，並從一個 cmdlet 傳遞到另一個物件。

預先存在的 cmdlet 所傳回的.NET Framework 物件經常缺少某些重要或方便存取的成員所需的指令碼開發人員或使用者。 這些遺漏的成員可以是供顯示及建立正確的成員名稱，使物件可以正確地傳遞到管線的特別重要。 建立自訂的 Types.ps1xml 檔案，以便記錄這些必要的成員。 當您建立此檔案時，我們建議下列命名慣例： *< Your_Product_Name >*。Types.ps1xml。

例如，您可以在其中加入`Mode`指令碼屬性到[System.IO.FileInfo](/dotnet/api/System.IO.FileInfo)更清楚地顯示檔案屬性的型別。 此外，您可以在其中加入`Count`別名屬性[System.Array](/dotnet/api/System.Array)允許一致使用該屬性名稱的型別 (而不是`Length`)。

##### <a name="implement-the-icomparable-interface"></a>實作 IComparable 介面

實作[System.IComparable](/dotnet/api/System.IComparable)介面上所有的輸出物件。 這可讓以輕鬆輸送到各種不同的排序及分析 cmdlet 的輸出物件。

##### <a name="update-display-information"></a>更新顯示的資訊

如果物件顯示未提供預期的結果，請建立自訂 *\<YourProductName >*。該物件的 Format.ps1xml 檔案。

### <a name="support-well-defined-pipeline-input-sc02"></a>支援妥善定義的管線輸入 (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>管線的中介的實作

實作假設，它會呼叫從管線的中介的 cmdlet （也就是其他指令程式會產生其輸入或取用它的輸出）。 例如，您可能會假設`Get-Process`cmdlet，因為它會產生資料，只會當做在管線中第一個 cmdlet。 不過，因為這個指令程式專為管線的中間，此 cmdlet 可讓先前的指令程式或資料管線，以指定要擷取的處理序中。

#### <a name="support-input-from-the-pipeline"></a>支援來自管線的輸入

在設定指令程式的每個參數，包含至少一個參數，支援從管線輸入。 管線輸入的支援可讓使用者擷取資料或物件，將它們傳送至正確的參數集，並將結果直接傳遞給 cmdlet。

參數會接受來自管線的輸入，如果**參數**屬性包含`ValueFromPipeline`關鍵字，`ValueFromPipelineByPropertyName`關鍵字的屬性或在其宣告中的這兩個關鍵字。 如果沒有任何參數在參數中設定的支援`ValueFromPipeline`或`ValueFromPipelineByPropertyName`關鍵字，此 cmdlet 無法有意義地在另一個 cmdlet 之後放置，因為它將會忽略任何管線輸入。

#### <a name="support-the-processrecord-method"></a>支援 ProcessRecord 方法

若要接受從管線中前面的 cmdlet 的所有記錄，必須實作您的 cmdlet [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 Windows PowerShell 呼叫此方法許多次，一次傳送到您的 cmdlet 的每一筆記錄。

### <a name="write-single-records-to-the-pipeline-sc03"></a>將單一記錄寫入管線 (SC03)

當 cmdlet 會傳回物件時，則此 cmdlet 應該寫入物件立即產生。 此 cmdlet 不應該保存它們以緩衝到結合的陣列。 接收物件做為輸入的指令程式將可以處理、 顯示或處理和顯示的輸出物件，不會有延遲。 指令程式來產生輸出物件一次應該呼叫[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 指令程式來產生批次中的輸出物件 （例如，因為基礎的 API 傳回的輸出物件陣列） 應該呼叫[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法有二個參數設定若要`true`。

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>讓 Cmdlet 不區分大小寫和保留大小寫 (SC04)

根據預設，Windows PowerShell 本身是不區分大小寫。 不過，因為它會處理許多預先存在的系統，Windows PowerShell 就會保留案例，簡化作業和相容性。 換句話說，如果提供以大寫的字母字元，則 Windows PowerShell 會保留它以大寫的字母。 對於系統正常運作，指令程式必須遵循此慣例。 可能的話，它應該在不區分大小寫的方式運作。 它應，不過，保留原始的情況下，或更新版本中命令管線中發生的 cmdlet。

## <a name="see-also"></a>另請參閱

[所需的開發指導方針](./required-development-guidelines.md)

[諮詢開發指導方針](./advisory-development-guidelines.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
