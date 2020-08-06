---
title: 建立 Windows PowerShell 屬性提供者 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.openlocfilehash: e8ef92629fe036154cdd2f0facbe0cbe8add7533
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778951"
---
# <a name="creating-a-windows-powershell-property-provider"></a>建立 Windows PowerShell 屬性提供者

本主題描述如何建立可讓使用者運算元據存放區中專案屬性的提供者。 因此，這種類型的提供者稱為 Windows PowerShell 屬性提供者。 例如，Windows PowerShell 提供的登錄提供者會處理登錄機碼值，做為登錄機碼專案的屬性。 這種類型的提供者必須將[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)介面新增至 .net 類別的執行。

> [!NOTE]
> Windows PowerShell 提供範本檔案，可供您用來開發 Windows PowerShell 提供者。 TemplateProvider.cs 檔案位於適用于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 已下載的範本可在目錄中取得 **\<PowerShell Samples>** 。 您應該建立此檔案的複本，並使用該複本建立新的 Windows PowerShell 提供者，移除您不需要的任何功能。 如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。

> [!CAUTION]
> 屬性提供者的方法應該使用[Cmdletprovider. Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject)方法來寫入任何物件。

## <a name="defining-the-windows-powershell-provider"></a>定義 Windows PowerShell 提供者

屬性提供者必須建立一個支援[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)介面的 .net 類別。 以下是 Windows PowerShell 所提供的 TemplateProvider.cs 檔案中的預設類別宣告。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>定義基本功能

[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)介面可以附加至任何提供者的基類，但 DriveCmdletprovider 類別除外。（可能為可能為[系統管理元件](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)）。 新增您所使用之基類所需的基本功能。 如需基類的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

## <a name="retrieving-properties"></a>擷取屬性

若要取得屬性，提供者必須執行[IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法，以支援來自 Cmdlet 的呼叫 `Get-ItemProperty` 。 這個方法會抓取位於指定的提供者內部路徑之專案的屬性， (完整) 。

`providerSpecificPickList`參數會指出要取得的屬性。 如果這個參數是 `null` 或空白，則方法應該會抓取所有屬性。 此外， [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)會寫入一個代表所抓取屬性之屬性包的[system.servicemodel 物件實例](/dotnet/api/System.Management.Automation.PSObject)（此物件表示）。 方法應該不會傳回任何內容。

建議您針對挑選清單中的每個專案，將[IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)的屬性名稱的萬用字元擴充功能提供支援。 若要這麼做，請使用[Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)類別來執行萬用字元模式比對。

以下是 Windows PowerShell 所提供的 TemplateProvider.cs 檔案中， [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>執行 GetProperty 的相關事項

下列條件可能適用于您的[IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)的執行方式：

- 定義 provider 類別時，Windows PowerShell 屬性提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為，否則此方法的覆寫不應抓取使用者所隱藏物件的讀取器 `true` 。 如果路徑代表使用者所隱藏的專案，而且[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)已設定為，則應該寫入錯誤 `false` 。

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>將動態參數附加至 ItemProperty Cmdlet

`Get-ItemProperty`Cmdlet 可能需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 屬性提供者必須執行[IpropertyCmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。 `path`參數會指出完整的提供者內部路徑，而 `providerSpecificPickList` 參數會指定在命令列上輸入的提供者特定屬性。 `null`如果將屬性輸送至 Cmdlet，此參數可能會是或空白。 在這種情況下，這個方法會傳回物件，其中具有屬性和欄位，其具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。

以下是 Windows PowerShell 所提供的 TemplateProvider.cs 檔案中， [IpropertyCmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>設定屬性

若要設定屬性，Windows PowerShell 屬性提供者必須執行[IpropertyCmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法，以支援來自 Cmdlet 的呼叫 `Set-ItemProperty` 。 這個方法會在指定的路徑上設定專案的一個或多個屬性，並視需要覆寫提供的屬性。
[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) ，也會寫入代表已更新屬性之屬性包的 system.servicemodel 物件實例（instance），這是一種[系統管理](/dotnet/api/System.Management.Automation.PSObject)介面。

以下是 Windows PowerShell 所提供的 TemplateProvider.cs 檔案中，IpropertyCmdletprovider 的預設實作為[系統管理](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>有關執行 ItemProperty 的事項

下列條件可能會套用至 IpropertyCmdletprovider 的執行方式[*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)中。

- 定義 provider 類別時，Windows PowerShell 屬性提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)的執行必須確定傳遞至方法的路徑符合指定之功能的需求，才能達成此條件。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為，否則此方法的覆寫不應抓取使用者所隱藏物件的讀取器 `true` 。 如果路徑代表使用者所隱藏的專案，而且[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)已設定為，則應該寫入錯誤 `false` 。

- 您的[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)應該會在對資料存放區進行任何變更之前，先呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並驗證其傳回值，然後再執行此程式。 這個方法是用來在對系統狀態進行變更時（例如，重新命名檔案），確認作業的執行。
  [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會將要變更的資源名稱傳送給使用者，並使用 Windows PowerShell 執行時間和處理任何命令列設定或喜好設定變數來決定要顯示的內容。

  在[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)的呼叫之後， `true` 如果可以進行可能危險的系統修改，則 ShouldProcess 方法應會呼叫[system.web](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) * 方法，而這種方式應會呼叫 system.servicemodel * 方法... [IpropertyCmdletprovider.](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .。 這個方法會傳送確認訊息給使用者，以允許其他意見反應來表示應該繼續作業。

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>附加 ItemProperty Cmdlet 的動態參數

`Set-ItemProperty`Cmdlet 可能需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 屬性提供者必須執行[IpropertyCmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。 這個方法會傳回物件，其中具有屬性和欄位，而且其具有類似于 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件的剖析屬性。 `null`如果沒有要加入的動態參數，則可傳回此值。

以下是 Windows PowerShell 所提供的 TemplateProvider.cs 檔案中， [IpropertyCmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>清除屬性

若要清除屬性，Windows PowerShell 屬性提供者必須執行[IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法，以支援來自 Cmdlet 的呼叫 `Clear-ItemProperty` 。 這個方法會為位於指定路徑的專案設定一個或多個屬性。

以下是 Windows PowerShell 所提供的 TemplateProvider.cs 檔案中， [IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>執行 ClearProperty 的相關事項

下列條件可能適用于您的[IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)的執行方式：

- 定義 provider 類別時，Windows PowerShell 屬性提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為，否則此方法的覆寫不應抓取使用者所隱藏物件的讀取器 `true` 。 如果路徑代表使用者所隱藏的專案，而且[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)已設定為，則應該寫入錯誤 `false` 。

- 您的 IpropertyCmdletprovider 必須先呼叫[Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法，然後在對資料存放區進行任何變更之前，先驗證它的傳回[值，然後再執行。](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 這個方法是用來在對系統狀態進行變更（例如清除內容）之前，先確認執行作業。
  [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳送要變更的資源名稱給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入決定應該顯示的內容。

  在呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)之後 `true` ，如果可以進行可能危險的系統修改，則[IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法應該呼叫方法。」（可能為可能會有危險[的](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)系統進行修改），。 這個方法會傳送確認訊息給使用者，以允許額外的意見反應來表示應該繼續進行可能危險的作業。

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>將動態參數附加至 ItemProperty Cmdlet

`Clear-ItemProperty`Cmdlet 可能需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 屬性提供者必須執行[IpropertyCmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法。 這個方法會傳回物件，其中具有屬性和欄位，而且其具有類似于 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件的剖析屬性。 `null`如果沒有要加入的動態參數，則可傳回此值。

以下是 Windows PowerShell 所提供的 TemplateProvider.cs 檔案中， [IpropertyCmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>建立 Windows PowerShell 提供者

請參閱[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[擴充物件類型和格式](https://msdn.microsoft.com/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)
