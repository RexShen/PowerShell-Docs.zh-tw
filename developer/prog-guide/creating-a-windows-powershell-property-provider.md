---
title: 建立 Windows PowerShell 屬性提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: 6ec0752a9ae06c5c2cdd1a1851caeeff52d8eb74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055150"
---
# <a name="creating-a-windows-powershell-property-provider"></a>建立 Windows PowerShell 屬性提供者

本主題描述如何建立提供者，可讓使用者管理的資料存放區中的項目屬性。 如此一來，這種類型的提供者被指 Windows PowerShell 屬性提供者。 例如，登錄提供者的登錄機碼項屬性提供 Windows PowerShell 會處理登錄機碼值。 這種類型的提供者必須加入[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) .NET 類別的實作的介面。

> [!NOTE]
> Windows PowerShell 提供可用來開發 Windows PowerShell 提供者的範本檔案。 適用於 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件 TemplateProvider.cs 檔案。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 下載的範本位於 **\<PowerShell 範例 >** 目錄。 您應該建立一份此檔案，並使用複本，用於建立新的 Windows PowerShell 提供者，移除任何您不需要的功能。
>
> 如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

> [!CAUTION]
> 屬性提供者的方法應該寫入任何物件，使用[System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject)方法。

下列清單包含本主題的章節。 如果您不熟悉如何撰寫 Windows PowerShell 屬性提供者，請閱讀這項資訊，它會出現的順序。 不過，如果您已熟悉撰寫 Windows PowerShell 屬性提供者，請直接前往您所需要的資訊。

- [定義 Windows PowerShell 提供者](#Defining-the-Windows-PowerShell-provider)

- [定義基底的功能](#Defining-Base-Functionality)

- [擷取屬性](#Retrieving-Properties)

- [附加到的動態參數`Get-ItemProperty`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [設定屬性](#Setting-Properties)

- [附加到的動態參數`Set-ItemProperty`Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [清除屬性](#Clearing-Properties)

- [附加到的動態參數`Clear-ItemProperty`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [建置 Windows PowerShell 提供者](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>定義 Windows PowerShell 提供者

屬性提供者必須建立一個支援的.NET 類別[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)介面。 以下是從 Windows PowerShell 所提供的 TemplateProvider.cs 檔案的預設類別宣告。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>定義基底的功能

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)介面可以連結至任何提供者的基底類別，但不包括[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。 新增需要您使用的基底類別的基底功能。 如需基底類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

## <a name="retrieving-properties"></a>擷取屬性

若要擷取屬性，提供者必須實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法，以支援來自呼叫`Get-ItemProperty`cmdlet。 這個方法會擷取位於指定的提供者內部路徑 （完整） 項目的屬性。

`providerSpecificPickList`參數指出要擷取的屬性。 如果這個參數是`null`或空的方法應該擷取所有屬性。 颾魤 ㄛ [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)寫入的執行個體[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)物件，表示擷取屬性的屬性包。 此方法應傳回任何項目。

建議的實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)挑選清單中支援的每個元素的屬性名稱的萬用字元展開。 若要這樣做，請使用[System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)類別來執行萬用字元模式比對。

以下是預設實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)從 Windows PowerShell 所提供的 TemplateProvider.cs 檔案。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>有關實作 GetProperty 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Windows PowerShell 屬性提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法需要確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，會覆寫這個方法不應該擷取除非隱藏使用者物件的讀取器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 應該寫入錯誤，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為`false`。

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>將動態參數附加至 Get-itemproperty Cmdlet

`Get-ItemProperty` Cmdlet 可能需要在執行階段動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 屬性提供者必須實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。 `path`參數表示完整的提供者內部路徑，而`providerSpecificPickList`參數會指定輸入命令列上的提供者特定屬性。 這個參數可能是`null`或空白，如果屬性會使用管線傳送至 cmdlet。 在此情況下，這個方法會傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件，將參數新增至 cmdlet。

以下是預設實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)從 Windows PowerShell 所提供的 TemplateProvider.cs 檔案。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>設定屬性

若要設定的屬性，Windows PowerShell 屬性提供者必須實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法，以支援來自呼叫`Set-ItemProperty`cmdlet。 這個方法會在指定的路徑，設定一或多個項目的屬性，並視需要提供的屬性會覆寫。 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)也會寫入的執行個體[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)物件，表示更新後的屬性包屬性。

以下是預設實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)從 Windows PowerShell 所提供的 TemplateProvider.cs 檔案。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>有關實作 Set-itemproperty 的注意事項

在下列情況可能適用於實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Windows PowerShell 屬性提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法必須確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，會覆寫這個方法不應該擷取除非隱藏使用者物件的讀取器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 應該寫入錯誤，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為`false`。

- 您實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並確認它的傳回值之前對資料存放區中的任何變更。 這個方法用來變更系統狀態，例如，重新命名檔案時，請確認執行作業。 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)傳送變更，以對使用者而言，Windows PowerShell 執行階段和處理的任何命令列設定或喜好設定變數，決定資源的名稱項目應該會顯示。

  若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，如果有潛在危險的系統會遭到修改， [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 這個方法會將確認訊息傳送給使用者，以允許其他意見反應，來表示作業應該繼續執行。

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>附加 Set-itemproperty cmdlet 的動態參數

`Set-ItemProperty` Cmdlet 可能需要在執行階段動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 屬性提供者必須實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。 這個方法會傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 `null`可以傳回值，如果沒有任何動態參數新增。

以下是預設實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)從 Windows PowerShell 所提供的 TemplateProvider.cs 檔案。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>清除屬性

若要清除的屬性，Windows PowerShell 屬性提供者必須實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法，以支援來自呼叫`Clear-ItemProperty`cmdlet。 這個方法會設定一或多個屬性位於指定路徑的項目。

以下是預設實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)從 Windows PowerShell 所提供的 TemplateProvider.cs 檔案。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>要記住實作 ClearProperty

在下列情況可能適用於您實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Windows PowerShell 屬性提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法需要確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，會覆寫這個方法不應該擷取除非隱藏使用者物件的讀取器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 應該寫入錯誤，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為`false`。

- 您實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並確認它的傳回值之前對資料存放區中的任何變更。 這個方法用來確認執行作業，才能變更系統狀態，例如清除內容。 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)傳送給使用者，變更納入考量，任何命令列設定或喜好設定變數中的 Windows PowerShell 執行階段資源的名稱決定應該要顯示的內容。

  若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，如果有潛在危險的系統會遭到修改， [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 這個方法會將確認訊息傳送給使用者，以允許其他意見反應，以指出有潛在危險的作業應該繼續執行。

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>將動態參數附加至 Clear-itemproperty Cmdlet

`Clear-ItemProperty` Cmdlet 可能需要在執行階段動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 屬性提供者必須實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法。 這個方法會傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 `null`可以傳回值，如果沒有任何動態參數新增。

以下是預設實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)從 Windows PowerShell 所提供的 TemplateProvider.cs 檔案。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>建置的 Windows PowerShell 提供者

請參閱[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)