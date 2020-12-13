---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 Windows PowerShell 屬性提供者
description: 建立 Windows PowerShell 屬性提供者
ms.openlocfilehash: 5370624afa784598ca784b201f7e7345eb958ff9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390910"
---
# <a name="creating-a-windows-powershell-property-provider"></a>建立 Windows PowerShell 屬性提供者

本主題說明如何建立提供者，讓使用者能夠運算元據存放區中專案的屬性。 因此，這種類型的提供者稱為 Windows PowerShell 屬性提供者。 例如，Windows PowerShell 提供的登錄提供者會將登錄機碼值視為登錄機碼專案的屬性來處理。 這種類型的提供者必須將 [IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 介面新增至 .net 類別的實作為。

> [!NOTE]
> Windows PowerShell 提供可用來開發 Windows PowerShell 提供者的範本檔案。 TemplateProvider.cs 檔案可在適用于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件上取得。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 您可以在目錄中取得下載的範本 **\<PowerShell Samples>** 。 您應該複製此檔案，並使用該複本來建立新的 Windows PowerShell 提供者，以移除任何不需要的功能。 如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

> [!CAUTION]
> 屬性提供者的方法應該使用 [Cmdletprovider. Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) 方法來撰寫任何物件。

## <a name="defining-the-windows-powershell-provider"></a>定義 Windows PowerShell 提供者

屬性提供者必須建立可支援 [IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 介面的 .net 類別。 以下是 Windows PowerShell 所提供之 TemplateProvider.cs 檔中的預設類別宣告。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>定義基底功能

[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)介面可以附加至任何提供者的基類，但[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別除外（可能為例外狀況除外）（exception）。 新增您所使用之基類所需的基本功能。 如需基類的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

## <a name="retrieving-properties"></a>擷取屬性

若要取得屬性，提供者必須執行 [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 方法，以支援來自 Cmdlet 的呼叫 `Get-ItemProperty` 。 這個方法會在指定的提供者內部路徑上抓取專案的屬性， (完整的) 。

`providerSpecificPickList`參數會指出要取得的屬性。 如果這個參數是 `null` 或空白，則方法應該抓取所有屬性。 此外， [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 會寫入代表所抓取屬性之屬性包的 [system.object](/dotnet/api/System.Management.Automation.PSObject) 物件的實例（Instance），以提供 方法應該不會傳回任何內容。

建議將 [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 的實作為挑選清單中每個元素的屬性名稱的萬用字元展開。」 若要這樣做，請使用 [Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) 類別來執行萬用字元模式比對。

以下是 Windows PowerShell 所提供之 TemplateProvider.cs 檔中的 [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 預設實作為。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>執行 GetProperty 的注意事項

下列情況可能適用于您的 [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)的執行：

- 定義提供者類別時，Windows PowerShell 屬性提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下， [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- 根據預設，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則，此方法的覆寫不應針對使用者所隱藏的物件，取得讀取 `true` 器。 如果路徑代表隱藏于使用者和 Cmdletprovider 中的專案，則應該撰寫錯誤。 [Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 會設定為 `false` 。

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>將動態參數附加至 Get-ItemProperty Cmdlet

`Get-ItemProperty`Cmdlet 可能需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 屬性提供者必須執行 [IpropertyCmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 方法。 `path`參數會指出完整的提供者內部路徑，而 `providerSpecificPickList` 參數會指定在命令列上輸入的提供者特定屬性。 `null`如果將屬性輸送至 Cmdlet，此參數可能是或空白。 在此情況下，這個方法會傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。

以下是 Windows PowerShell 所提供之 TemplateProvider.cs 檔中的 [IpropertyCmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 預設實作為。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>設定屬性

若要設定屬性，Windows PowerShell 屬性提供者必須執行 [IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) ，以支援來自指令程式的 `Set-ItemProperty` 呼叫。 這個方法會在指定的路徑設定專案的一或多個屬性，並視需要覆寫提供的屬性。
[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) ，也會寫入代表已更新屬性之屬性包的 [system.object](/dotnet/api/System.Management.Automation.PSObject) 物件實例（此物件為../.）。

以下是 Windows PowerShell 所提供之 TemplateProvider.cs 檔案中的 [IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 的預設執行方式：。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>有關實施 Set-ItemProperty 的事項

下列情況可能適用于 IpropertyCmdletprovider 的實作為 [系統管理](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)的執行：

- 定義提供者類別時，Windows PowerShell 屬性提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下，IpropertyCmdletprovider 的執行必須確定傳遞至方法的路徑符合指定之功能的需求，才能執行此 [程式](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 。 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- 根據預設，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則，此方法的覆寫不應針對使用者所隱藏的物件，取得讀取 `true` 器。 如果路徑代表隱藏于使用者和 Cmdletprovider 中的專案，則應該撰寫錯誤。 [Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 會設定為 `false` 。

- 您的 [IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並驗證其傳回值的方法。（.） 當對系統狀態進行變更（例如重新命名檔案）時，會使用這個方法來確認作業的執行。
  [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會將要變更的資源名稱傳送給使用者，並使用 Windows PowerShell 執行時間，並處理任何命令列設定或喜好設定變數，以決定應該顯示的內容。

  在呼叫 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 之後 `true` ，如果可以進行可能有危險的系統修改，則 [IpropertyCmdletprovider.](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .. m a r * 方法應該呼叫 [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) * 方法，然後呼叫 ShouldProcess 方法，以避免發生危險的系統修改。 這個方法會將確認訊息傳送給使用者，以允許其他意見反應，以表示作業應該繼續。

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>附加 Set-ItemProperty Cmdlet 的動態參數

`Set-ItemProperty`Cmdlet 可能需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 屬性提供者必須執行 [IpropertyCmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) 方法。 這個方法會傳回物件，該物件具有剖析屬性（attribute）與 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件類似的屬性和欄位。 `null`如果沒有要加入的動態參數，則可以傳回值。

以下是 Windows PowerShell 所提供之 TemplateProvider.cs 檔中的 [IpropertyCmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 預設實作為。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>清除屬性

若要清除屬性，Windows PowerShell 屬性提供者必須執行 [IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 方法，以支援來自 Cmdlet 的呼叫 `Clear-ItemProperty` 。 這個方法會設定位於指定路徑之專案的一或多個屬性。

以下是 Windows PowerShell 所提供之 TemplateProvider.cs 檔中的 [IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 預設實作為。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>執行 ClearProperty 的事項

下列情況可能適用于您的 [IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)的執行：

- 定義提供者類別時，Windows PowerShell 屬性提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下， [IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- 根據預設，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則，此方法的覆寫不應針對使用者所隱藏的物件，取得讀取 `true` 器。 如果路徑代表隱藏于使用者和 Cmdletprovider 中的專案，則應該撰寫錯誤。 [Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 會設定為 `false` 。

- 您的 [IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並驗證其傳回值的方法，才能執行。 在對系統狀態進行變更（例如清除內容）之前，會使用這個方法來確認操作的執行。
  [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會傳送要變更給使用者的資源名稱，且 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入考慮，以決定應顯示的內容。

  在呼叫 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 之後 `true` ，如果可以進行可能有危險的系統修改，則 IpropertyCmdletprovider. Clearproperty * 方法應該呼叫 system.object，以進行系統管理。 [. *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 方法應該呼叫 [system.object. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 方法。 這個方法會將確認訊息傳送給使用者，以允許其他意見反應，以指出可能會有危險的作業繼續進行。

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>將動態參數附加至 Clear-ItemProperty Cmdlet

`Clear-ItemProperty`Cmdlet 可能需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 屬性提供者必須執行 [IpropertyCmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 方法。 這個方法會傳回物件，該物件具有剖析屬性（attribute）與 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件類似的屬性和欄位。 `null`如果沒有要加入的動態參數，則可以傳回值。

以下是 Windows PowerShell 所提供之 TemplateProvider.cs 檔中的 [IpropertyCmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 預設實作為。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>建立 Windows PowerShell 提供者

瞭解 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="see-also"></a>另請參閱

[Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[擴充物件類型和格式化](/previous-versions//ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))
