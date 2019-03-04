---
title: 建立 Windows PowerShell 項目提供者 |Microsoft Docs
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
ms.openlocfilehash: 30b4dbcd281f712bba8d8e3540d2282d527388e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862064"
---
# <a name="creating-a-windows-powershell-item-provider"></a>建立 Windows PowerShell 項目提供者

本主題描述如何建立 Windows PowerShell 提供者，可以操作資料存放區中的資料。 本主題中，資料存放區中的項目統稱為 「 項目 」 的資料存放區。 如此一來，可以操作的資料存放區中的提供者被指 Windows PowerShell 項目提供者。

> [!NOTE]
> 您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此提供者的原始程式檔 (AccessDBSampleProvider03.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
> 您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此提供者的原始程式檔 (AccessDBSampleProvider03.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。
>
> 如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

本主題中所述的 Windows PowerShell 項目提供者取得資料的項目從 Access 資料庫。 在此情況下，「 項目 」 是存取資料庫中的資料表，或是在資料表中的資料列。

下列清單包含本主題的章節。 如果您不熟悉如何撰寫 Windows PowerShell 項目提供者，閱讀這些章節中出現的順序。 不過，如果您已熟悉撰寫 Windows PowerShell 項目提供者，直接移至您所需要的資訊：

- [定義 Windows PowerShell 項目提供者類別](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [定義基底的功能](#Defining-Base-Functionality)

- [路徑有效性檢查](#Checking-for-Path-Validity)

- [判斷項目是否存在](#Determining-if-an-Item-Exists)

- [附加到的動態參數`Test-Path`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [擷取項目](#Retrieving-an-Item)

- [附加到的動態參數`Get-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [設定項目](#Setting-an-Item)

- [附加到的動態參數`Set-Item`Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [清除項目](#Clearing-an-Item)

- [附加至 Cler Get-item Cmdlet 的動態參數](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [執行預設動作的項目](#Performing-a-Default-Action-for-an-Item)

- [擷取 InvokeDefaultAction 動態參數](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [實作 Helper 方法和類別](#Implementing-Helper-Methods-and-Classes)

- [程式碼範例](#Code-Sample)

- [定義物件類型和格式設定](#Defining-Object-Types-and-Formatting)

- [建置 Windows PowerShell 提供者](#Building-the-Windows-PowerShell-provider)

- [測試 Windows PowerShell 提供者](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>定義 Windows PowerShell 項目提供者類別

Windows PowerShell 項目提供者必須定義衍生自.NET 類別[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基底類別。 以下是這一節所述的項目提供者的類別定義。

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

請注意，在此類別定義中， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。 第一個參數會指定使用 Windows powershell 提供者的使用者易記名稱。 第二個參數指定命令處理期間提供者會公開 Windows PowerShell 執行階段的 Windows PowerShell 特定功能。 此提供者中，沒有新增的 Windows PowerShell 的特定功能。

## <a name="defining-base-functionality"></a>定義基底的功能

中所述[設計您 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)，則[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別衍生自數個其他提供不同的類別提供者的功能。 Windows PowerShell 項目提供者，因此，必須定義所有這些類別所提供的功能。

如需如何實作功能，新增工作階段特定的初始化資訊，以便釋放資源提供者所使用的詳細資訊，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者，包括此處描述的提供者可以使用這項功能所提供的 Windows PowerShell 的預設實作。

Windows PowerShell 項目提供者可以管理存放區中的項目之前，它必須實作的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別來存取資料存放區。 如需有關如何實作這個類別的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

## <a name="checking-for-path-validity"></a>路徑有效性檢查

Windows PowerShell 執行階段時尋找資料的項目，提供提供者的 Windows PowerShell 路徑中的 < PSPath 概念 > 一節所定義[Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。 Windows PowerShell 項目提供者必須確認傳遞給它，藉由實作任何路徑的語法和語意有效性[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法。 這個方法會傳回`true`路徑是否有效，以及`false`否則。 要注意，此方法的實作應驗證是否存在的項目路徑，但僅限於路徑語法和語意不正確。
Windows PowerShell 執行階段時尋找資料的項目，提供提供者的 Windows PowerShell 路徑中的 < PSPath 概念 > 一節所定義[Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。 Windows PowerShell 項目提供者必須確認傳遞給它，藉由實作任何路徑的語法和語意有效性[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法。 這個方法會傳回`true`路徑是否有效，以及`false`否則。 要注意，此方法的實作應驗證是否存在的項目路徑，但僅限於路徑語法和語意不正確。

以下是實作[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)此提供者的方法。 請注意，此實作會呼叫 NormalizePath helper 方法來將路徑中的所有分隔符號都轉換成一個統一的帳戶。

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>判斷項目是否存在

確認路徑之後，Windows PowerShell 執行階段必須判斷在該路徑是否存在的資料的項目。 若要支援這種類型的查詢，Windows PowerShell 項目提供者會實作[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法。 這個方法會傳回`true`項目位於指定的路徑和`false`（預設） 否則。

以下是實作[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)此提供者的方法。 請注意，這個方法會呼叫 PathIsDrive、 ChunkPath 和 GetTable 協助程式方法，提供者就會使用定義 DatabaseTableInfo 物件。

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>有關實作 ItemExists 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Windows PowerShell 項目提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法必須確定傳遞給方法的路徑符合指定的功能的需求。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 此方法的實作應該處理任何形式的存取可能會使項目對使用者顯示此項目。 例如，如果使用者具有寫入權限透過 FileSystem 提供者 （由 Windows PowerShell 提供），但沒有讀取權限的檔案，檔案仍然存在和[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)傳回`true`。 您的實作可能需要檢查的父項目，以查看可列舉的子項目。

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>將動態參數附加至 Test-path Cmdlet

有時候`Test-Path`呼叫的 cmdlet [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)需要在執行階段動態指定的其他參數。 若要提供這些動態參數項目提供者必須實作的 Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法。 這個方法會擷取位於指定路徑的項目動態參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`Test-Path`cmdlet。

此 Windows PowerShell 項目提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>擷取項目

若要擷取項目，Windows PowerShell 項目提供者必須覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，以支援來自呼叫`Get-Item`cmdlet。 項目使用這個方法會寫入[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。

以下是實作[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)此提供者的方法。 請注意，這個方法會使用 GetTable 和 GetRow 協助程式方法，在擷取是將 Access 資料庫中的資料表中的資料列的項目。

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>有關實作 GetItem 的注意事項

在下列情況可能適用於實作[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Windows PowerShell 項目提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)必須確定傳遞給方法的路徑符合這些需求。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，會覆寫這個方法不應該擷取物件通常隱藏的使用者除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 例如， [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) FileSystem 提供者檢查方法[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性，它會嘗試呼叫之前[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)隱藏或系統檔案。

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>附加至 Get-item Cmdlet 的動態參數

有時候`Get-Item`cmdlet 需要在執行階段動態指定的其他參數。 若要提供這些動態參數項目提供者必須實作的 Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。 這個方法會擷取位於指定路徑的項目動態參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`Get-Item`cmdlet。

此提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>設定項目

若要設定項目，Windows PowerShell 項目提供者必須覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支援來自呼叫`Set-Item`cmdlet。 這個方法會設定位於指定路徑的項目值。

此提供者未提供的覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法。 不過，以下是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>有關實作 SetItem 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Windows PowerShell 項目提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)必須確定傳遞給方法的路徑符合這些需求。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，覆寫這個方法不應該設定或寫入物件，而您的使用者隱藏，除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 錯誤應該傳送至[System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，若路徑代表隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設為`false`。

- 您實作[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)，並確認它的傳回值之前對資料存放區中的任何變更。 這個方法用來變更資料存放區，例如，刪除檔案時，請確認執行作業。 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會傳送給使用者，變更納入考量的任何命令列設定的 Windows PowerShell 執行階段資源的名稱或在決定應該顯示的喜好設定變數。

  若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 這個方法會將訊息傳送給使用者，以允許確認是否應該繼續執行作業的意見反應。 若要在呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允許額外的檢查，如有潛在危險的系統修改。

## <a name="retrieving-dynamic-parameters-for-setitem"></a>擷取 SetItem 動態參數

有時候`Set-Item`cmdlet 需要在執行階段動態指定的其他參數。 若要提供這些動態參數項目提供者必須實作的 Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。 這個方法會擷取位於指定路徑的項目動態參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`Set-Item`cmdlet。

此提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>清除項目

若要清除項目，Windows PowerShell 項目提供者會實作[System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法，以支援來自呼叫`Clear-Item`cmdlet。 這個方法會清除資料處的項目指定的路徑。

此提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>有關實作 ClearItem 的注意事項

在下列情況可能適用於實作[System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Windows PowerShell 項目提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)必須確定傳遞給方法的路徑符合這些需求。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，覆寫這個方法不應該設定或寫入物件，而您的使用者隱藏，除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 錯誤應該傳送至[System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設為`false`。

- 您實作[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)，並確認它的傳回值之前對資料存放區中的任何變更。 這個方法用來變更資料存放區，例如，刪除檔案時，請確認執行作業。 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會傳送給使用者，使用 Windows PowerShell 執行階段變更，並處理任何命令列設定或喜好設定資源的名稱在決定應該要顯示的內容變數。

  若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 這個方法會將訊息傳送給使用者，以允許確認是否應該繼續執行作業的意見反應。 若要在呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允許額外的檢查，如有潛在危險的系統修改。

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>擷取 ClearItem 動態參數

有時候`Clear-Item`cmdlet 需要在執行階段動態指定的其他參數。 若要提供這些動態參數項目提供者必須實作的 Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。 這個方法會擷取位於指定路徑的項目動態參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`Clear-Item`cmdlet。

此項目提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>執行預設動作的項目

Windows PowerShell 項目提供者可實作[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，以支援來自呼叫`Invoke-Item`cmdlet，可讓提供者至位於指定路徑的項目執行預設動作。 例如，FileSystem 提供者可能會使用這個方法呼叫 ShellExecute 特定項目。

此提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>有關實作 InvokeDefaultAction 的注意事項

在下列情況可能適用於實作[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Windows PowerShell 項目提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)必須確定傳遞給方法的路徑符合這些需求。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，會覆寫這個方法不應該設定或寫入物件對使用者隱藏的除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 錯誤應該傳送至[System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設為`false`。

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>擷取 InvokeDefaultAction 動態參數

有時候`Invoke-Item`cmdlet 需要在執行階段動態指定的其他參數。 若要提供這些動態參數項目提供者必須實作的 Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法。 這個方法會擷取位於指定路徑的項目動態參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件新增至動態參數`Invoke-Item`cmdlet。

此項目提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>實作 Helper 方法和類別

此項目提供者會實作數個協助程式方法，而類別所使用的公用覆寫 Windows PowerShell 所定義的方法。 這些 helper 方法和類別的程式碼所示[程式碼範例](#Code-Sample)一節。

### <a name="normalizepath-method"></a>NormalizePath 方法

此項目提供者會實作 NormalizePath helper 方法，以確保路徑有一致的格式。 指定的格式會使用反斜線 (\\) 做為分隔符號。

### <a name="pathisdrive-method"></a>PathIsDrive 方法

此項目提供者會實作 PathIsDrive helper 方法來判斷實際的磁碟機名稱是否包含指定的路徑。

### <a name="chunkpath-method"></a>ChunkPath 方法

此項目提供者會實作 ChunkPath helper 方法，以便提供者可以識別其個別項目會指定的路徑。 它會傳回陣列組成的路徑項目。

### <a name="gettable-method"></a>GetTable 方法

此項目提供者會實作 GetTables helper 方法，它會傳回一個 DatabaseTableInfo 物件，代表呼叫中指定資料表的相關資訊。

### <a name="getrow-method"></a>GetRow 方法

[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)此項目提供者方法的呼叫 GetRows helper 方法。 這個 helper 方法會擷取 DatabaseRowInfo 物件，表示指定的資料列，資料表中的相關資訊。

### <a name="databasetableinfo-class"></a>DatabaseTableInfo 類別

此項目提供者會定義 DatabaseTableInfo 類別，表示在資料庫中的資料表中的資訊的集合。 這個類別是類似[System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo)類別。

範例項目提供者會定義 DatabaseTableInfo.GetTables 方法會傳回為資料表定義在資料庫中的資料表資訊物件的集合。 這個方法包含 try/catch 區塊，以確保該資料庫中的任何錯誤可顯示的資料列與零個項目。

### <a name="databaserowinfo-class"></a>DatabaseRowInfo 類別

此項目提供者會定義 DatabaseRowInfo 協助程式類別，表示在資料庫中資料表之資料列。 這個類別是類似[System.IO.Fileinfo](/dotnet/api/System.IO.FileInfo)類別。

範例提供者會定義 DatabaseRowInfo.GetRows 方法，以傳回指定之資料表的資料列資訊物件的集合。 這個方法包含 try/catch 區塊來攔截例外狀況。 任何錯誤都會造成沒有資料列的資訊。

## <a name="code-sample"></a>程式碼範例

完整的範例程式碼，請參閱[AccessDbProviderSample03 程式碼範例](./accessdbprovidersample03-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式設定

當撰寫提供者，它可能需要將成員加入至現有的物件，或定義新的物件。 完成時，建立 Windows PowerShell 可以用來識別物件的成員類型檔案與格式檔案，定義物件的顯示方式。 如需詳細資訊，請參閱 <<c0> [ 延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。
當撰寫提供者，它可能需要將成員加入至現有的物件，或定義新的物件。 完成時，建立 Windows PowerShell 可以用來識別物件的成員類型檔案與格式檔案，定義物件的顯示方式。 如需詳細資訊，請參閱 <<c0> [ 延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-windows-powershell-provider"></a>建置的 Windows PowerShell 提供者

請參閱[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。
請參閱[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

此 Windows PowerShell 項目提供者註冊時使用 Windows PowerShell，您就可以只測試基本，和磁碟機提供者的功能。 若要測試的項目操作，您也必須實作中所描述的容器功能[實作容器的 Windows PowerShell 提供者](./creating-a-windows-powershell-container-provider.md)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[建立容器的 Windows PowerShell 提供者](./creating-a-windows-powershell-container-provider.md)

[建立磁碟機的 Windows PowerShell 提供者](./creating-a-windows-powershell-drive-provider.md)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)