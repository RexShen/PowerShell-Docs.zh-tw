---
title: 建立 Windows PowerShell 專案提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: ad42b8de867f468e832380ab6a22a39b6d27d3c6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417497"
---
# <a name="creating-a-windows-powershell-item-provider"></a>建立 Windows PowerShell 項目提供者

本主題說明如何建立可運算元據存放區中資料的 Windows PowerShell 提供者。 在本主題中，存放區中的資料元素稱為資料存放區的「專案」。 因此，可以操控存放區中資料的提供者稱為 Windows PowerShell 專案提供者。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的原始程式檔（AccessDBSampleProvider03.cs）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。
>
> 如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。

本主題所描述的 Windows PowerShell 專案提供者會從 Access 資料庫取得資料的專案。 在此情況下，「專案」是 Access 資料庫中的資料表或資料表中的資料列。

## <a name="defining-the-windows-powershell-item-provider-class"></a>定義 Windows PowerShell 專案提供者類別

Windows PowerShell 專案提供者必須定義一個衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基類的 .net 類別（class）。 以下是本節所述之專案提供者的類別定義。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。 第一個參數會為 Windows PowerShell 所使用的提供者指定易記的名稱。 第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。 對於此提供者，並未新增 Windows PowerShell 特有的功能。

## <a name="defining-base-functionality"></a>定義基本功能

如[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)中所述， [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別衍生自數個其他提供不同提供者功能的類別。 因此，Windows PowerShell 專案提供者必須定義這些類別所提供的所有功能。

如需如何執行功能來新增會話特定初始化資訊以及釋放提供者所使用之資源的詳細資訊，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者（包括這裡所述的提供者）都可以使用 Windows PowerShell 所提供的這項功能的預設執行。

在 Windows PowerShell 專案提供者可以操作存放區中的專案之前，必須先執行[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的方法，以存取資料存放區。 如需有關如何執行此類別的詳細資訊，請參閱[建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

## <a name="checking-for-path-validity"></a>檢查路徑有效性

在尋找資料的專案時，Windows PowerShell 執行時間會 furnishes windows powershell 對提供者的路徑，如[Windows Powershell 運作方式](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)的「PSPath 概念」一節中所定義。 Windows PowerShell 專案提供者必須藉由執行[ItemCmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，驗證傳遞給它的任何路徑的語法和語義有效性。 如果路徑有效，這個方法會傳回 `true`，否則會傳回 `false`。 請注意，這個方法的執行不應該驗證專案是否存在於路徑，但只有路徑在語法上和語義正確。

以下是此提供者的[ItemCmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法的執行。 請注意，此實作為呼叫 NormalizePath helper 方法，以將路徑中的所有分隔符號轉換成統一的。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>判斷專案是否存在

驗證路徑之後，Windows PowerShell 執行時間必須判斷該路徑上是否有資料的專案。 為了支援這種類型的查詢，Windows PowerShell 專案提供者會執行[ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法。 這個方法會傳回 `true` 在指定的路徑找到專案，否則 `false` （預設值）。

以下是此提供者的[ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法的執行。 請注意，這個方法會呼叫 PathIsDrive、ChunkPath 和 GetTable helper 方法，並使用提供者定義的 DatabaseTableInfo 物件。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>執行 ItemExists 的相關事項

下列條件可能適用于您的[ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)的執行方式：

- 定義 provider 類別時，Windows PowerShell 專案提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法的執行必須確保傳遞至方法的路徑符合指定之功能的需求。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 這個方法的執行應該會處理對專案可能會讓使用者看見專案的任何形式的存取權。 例如，如果使用者透過 FileSystem 提供者（由 Windows PowerShell 提供）擁有檔案的寫入存取權，但沒有讀取權限，檔案仍然存在，而且[ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)會傳回 `true`。 您的執行可能需要檢查父專案，以查看子專案是否可以列舉。

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>將動態參數附加至測試路徑 Cmdlet

有時會呼叫[ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)的 `Test-Path` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 專案提供者必須執行[ItemCmdletprovider. Itemexistsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法。 這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Test-Path` Cmdlet。

這個 Windows PowerShell 專案提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>正在抓取專案

若要取出專案，Windows PowerShell 專案提供者必須覆寫[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，以支援來自 `Get-Item` Cmdlet 的呼叫。 這個方法會使用[Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法來寫入專案。

以下是此提供者的[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法的執行。 請注意，這個方法會使用 GetTable 和 GetRow helper 方法來抓取 Access 資料庫中的資料表或資料表中資料列的專案。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>執行 GetItem 的相關事項

下列條件可能適用于[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)的執行程式：

- 定義 provider 類別時，Windows PowerShell 專案提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)的執行必須確定傳遞至方法的路徑符合這些需求。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`，否則此方法的覆寫不應抓取使用者通常會隱藏的物件。 例如，FileSystem 提供者的[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法會先檢查[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性，然後再嘗試呼叫隱藏或系統檔案的 System.servicemodel. [Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) . * （系統管理元件），然後才執行。

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>將動態參數附加至 Get Item Cmdlet

有時候 `Get-Item` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 專案提供者必須執行[ItemCmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。 這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Get-Item` Cmdlet。

此提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>設定專案

若要設定專案，Windows PowerShell 專案提供者必須覆寫[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支援來自 `Set-Item` Cmdlet 的呼叫。 這個方法會在指定的路徑設定專案的值。

此提供者不會提供[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法的覆寫。 不過，以下是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>執行 SetItem 的相關事項

下列條件可能適用于您的[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)的執行方式：

- 定義 provider 類別時，Windows PowerShell 專案提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)的執行必須確定傳遞至方法的路徑符合這些需求。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`，否則此方法的覆寫不應設定或寫入使用者隱藏的物件。 如果路徑代表隱藏的專案，而且[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為 `false`，則應該將錯誤傳送至[Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法。 * *）。

- 您的 ItemCmdletprovider 必須先呼叫[Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，然後在對資料存放區進行任何變更之前，先驗證它的傳回[值，然後再執行。](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 當資料存放區發生變更（例如刪除檔案）時，會使用這個方法來確認作業的執行。 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會將要變更的資源名稱傳送給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入決定應該顯示的內容。

  呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 `true`，則[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法應會呼叫 system.servicemodel. Cmdletprovider [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ShouldContinue 方法（.........）。 這個方法會將訊息傳送給使用者，以允許意見反應來驗證作業是否應該繼續。 呼叫[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允許額外檢查是否有潛在危險的系統修改。

## <a name="retrieving-dynamic-parameters-for-setitem"></a>正在抓取 SetItem 的動態參數

有時候 `Set-Item` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 專案提供者必須執行[ItemCmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。 這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Set-Item` Cmdlet。

此提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>清除專案

若要清除專案，Windows PowerShell 專案提供者會執行[ItemCmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法，以支援來自 `Clear-Item` Cmdlet 的呼叫。 這個方法會清除指定路徑中的資料項目。

此提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>執行 ClearItem 的相關事項

下列條件可能適用于[ItemCmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)的執行程式：

- 定義 provider 類別時，Windows PowerShell 專案提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ItemCmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)的執行必須確定傳遞至方法的路徑符合這些需求。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`，否則此方法的覆寫不應設定或寫入使用者隱藏的物件。 如果路徑代表使用者和 Cmdletprovider 中隱藏的專案，則應該將錯誤傳送至[WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法。 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)會設定為 [`false`] 中的 [系統管理]。

- 您的 ItemCmdletprovider 必須先呼叫[Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，然後在對資料存放區進行任何變更之前，先驗證它的傳回[值，然後再執行。](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 當資料存放區發生變更（例如刪除檔案）時，會使用這個方法來確認作業的執行。 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會使用 Windows PowerShell 執行時間，將要變更的資源名稱傳送給使用者，並在決定應該顯示的內容時處理任何命令列設定或喜好設定變數。

  呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 `true`，則[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法應會呼叫 system.servicemodel. Cmdletprovider [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ShouldContinue 方法（.........）。 這個方法會將訊息傳送給使用者，以允許意見反應來驗證作業是否應該繼續。 呼叫[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允許額外檢查是否有潛在危險的系統修改。

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>取出 ClearItem 的動態參數

有時候 `Clear-Item` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 專案提供者必須執行[ItemCmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。 這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Clear-Item` Cmdlet。

這個專案提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>執行專案的預設動作

Windows PowerShell 專案提供者可以執行[ItemCmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，以支援來自 `Invoke-Item` Cmdlet 的呼叫，這可讓提供者對指定路徑的專案執行預設動作。 例如，FileSystem 提供者可能會使用這個方法來呼叫特定專案的 ShellExecute。

此提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>執行 InvokeDefaultAction 的相關事項

下列條件可能適用于[ItemCmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)的執行程式：

- 定義 provider 類別時，Windows PowerShell 專案提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ItemCmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)的執行必須確定傳遞至方法的路徑符合這些需求。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`，否則此方法的覆寫不應設定或寫入使用者隱藏的物件。 如果路徑代表使用者和 Cmdletprovider 中隱藏的專案，則應該將錯誤傳送至[WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法。 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)會設定為 [`false`] 中的 [系統管理]。

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>取出 InvokeDefaultAction 的動態參數

有時候 `Invoke-Item` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 專案提供者必須執行[ItemCmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法。 這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將動態參數新增至 `Invoke-Item` Cmdlet。

這個專案提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>執行 Helper 方法和類別

這個專案提供者會執行由 Windows PowerShell 定義的公用覆寫方法所使用的數個 helper 方法和類別。 這些 helper 方法和類別的程式碼會顯示在程式[代碼範例](#code-sample)區段中。

### <a name="normalizepath-method"></a>NormalizePath 方法

這個專案提供者會實行 NormalizePath helper 方法，以確保路徑具有一致的格式。 指定的格式會使用反斜線（\\）做為分隔符號。

### <a name="pathisdrive-method"></a>PathIsDrive 方法

這個專案提供者會執行 PathIsDrive helper 方法，以判斷指定的路徑是否實際上是磁片磁碟機名稱。

### <a name="chunkpath-method"></a>ChunkPath 方法

這個專案提供者會執行 ChunkPath helper 方法來分解指定的路徑，讓提供者能夠識別其個別元素。 它會傳回由 path 元素組成的陣列。

### <a name="gettable-method"></a>GetTable 方法

這個專案提供者會執行 GetTables helper 方法，它會傳回代表呼叫中所指定資料表之相關資訊的 DatabaseTableInfo 物件。

### <a name="getrow-method"></a>GetRow 方法

這個專案提供者的[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法會呼叫 GetRows helper 方法。 這個 helper 方法會抓取一個 DatabaseRowInfo 物件，它代表資料表中指定之資料列的相關資訊。

### <a name="databasetableinfo-class"></a>DatabaseTableInfo 類別

這個專案提供者會定義 DatabaseTableInfo 類別，代表資料庫中資料表的資訊集合。 這個類別類似于[Directoryinfo](/dotnet/api/System.IO.DirectoryInfo)類別。

範例專案提供者會定義 DatabaseTableInfo 的 GetTables 方法，它會傳回資料表資訊物件的集合，以定義資料庫中的資料表。 這個方法包含 try/catch 區塊，以確保任何資料庫錯誤都會顯示成包含零個專案的資料列。

### <a name="databaserowinfo-class"></a>DatabaseRowInfo 類別

這個專案提供者會定義 DatabaseRowInfo helper 類別，以代表資料庫之資料表中的資料列。 這個類別類似于[FileInfo](/dotnet/api/System.IO.FileInfo)類別。

範例提供者會定義 DatabaseRowInfo 方法，以傳回指定之資料表的資料列資訊物件集合。 這個方法包含用來攔截例外狀況的 try/catch 區塊。 任何錯誤都不會產生任何資料列資訊。

## <a name="code-sample"></a>程式碼範例

如需完整的範例程式碼，請參閱[AccessDbProviderSample03 程式碼範例](./accessdbprovidersample03-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

撰寫提供者時，可能需要將成員加入至現有的物件或定義新的物件。 完成時，建立一個類型檔案，Windows PowerShell 可以使用此檔案來識別物件的成員，以及定義如何顯示物件的格式檔案。 如需的詳細資訊，請參閱[擴充物件類型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-windows-powershell-provider"></a>建立 Windows PowerShell 提供者

請參閱[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當此 Windows PowerShell 專案提供者向 Windows PowerShell 註冊時，您只能測試提供者的基本和驅動功能。 若要測試專案的操作，您也必須執行[執行容器 Windows PowerShell 提供者](./creating-a-windows-powershell-container-provider.md)中所述的容器功能。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[擴充物件類型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell 的運作方式](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[建立容器 Windows PowerShell 提供者](./creating-a-windows-powershell-container-provider.md)

[建立磁片磁碟機 Windows PowerShell 提供者](./creating-a-windows-powershell-drive-provider.md)

[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)
