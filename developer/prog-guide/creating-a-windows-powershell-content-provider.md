---
title: 建立 Windows PowerShell 內容提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: a897ba29835e6f04ccacf3c4d7d8a1d43cedb91e
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323218"
---
# <a name="creating-a-windows-powershell-content-provider"></a>建立 Windows PowerShell 內容提供者

本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以運算元據存放區中的專案內容。 因此，可以操作專案內容的提供者稱為 Windows PowerShell 內容提供者。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的原始程式檔（AccessDBSampleProvider06.cs）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。
>
> 如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。

## <a name="define-the-windows-powershell-content-provider-class"></a>定義 Windows PowerShell 內容提供者類別

Windows PowerShell 內容提供者必須建立一個支援[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面的 .net 類別。 以下是本節所述之專案提供者的類別定義。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。 第一個參數會為 Windows PowerShell 所使用的提供者指定易記的名稱。 第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。 對於此提供者，並未新增 Windows PowerShell 特有的功能。

## <a name="define-functionality-of-base-class"></a>定義基類的功能

如[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)中所述， [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別衍生自數個其他提供不同提供者功能的類別。 因此，Windows PowerShell 內容提供者通常會定義這些類別所提供的所有功能。

如需如何執行功能來新增會話特定初始化資訊以及釋放提供者所使用之資源的詳細資訊，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者（包括這裡所述的提供者）都可以使用 Windows PowerShell 所提供的這項功能的預設執行。

若要存取資料存放區，提供者必須實作為[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的方法。 如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基類所提供的方法。 如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。

若要在多層式資料存放區上工作，提供者必須執行[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基類所提供的方法。 如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。

若要支援遞迴命令、嵌套容器和相對路徑，提供者必須執行[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基類。 此外，此 Windows PowerShell 內容提供者也可以將[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面附加至[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基類，並在此提供者。因此，必須執行該類別所提供的方法。 如需詳細資訊，請參閱執行這些方法，請參閱實[作為流覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)。

## <a name="implementing-a-content-reader"></a>執行內容讀取程式

若要從專案讀取內容，提供者必須執行衍生自[Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)的內容讀取器類別。 此提供者的內容讀取器允許存取資料表中的資料列內容。 內容讀取器類別會定義**讀取**方法，以從指定的資料列抓取資料，並傳回代表該資料的清單、移動內容讀取器的**搜尋**方法、關閉內容讀取器的**關閉**方法，以及**Dispose**方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>執行內容寫入器

若要將內容寫入專案，提供者必須執行衍生自[Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)的內容寫入器類別。 內容寫入器類別會定義**寫入**方法，以寫入指定的資料列內容、移動內容寫入器的**搜尋**方法、關閉內容寫入器的**Close**方法，以及**Dispose**方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>正在抓取內容讀取器

若要從專案取得內容，提供者必須執行[IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)來支援此`Get-Content` Cmdlet。 這個方法會傳回位於指定路徑之專案的內容讀取器。 然後，可以開啟 reader 物件來讀取內容。

以下是此提供者的這個方法的[IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)的執行程式。

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>執行 GetContentReader 的相關事項

下列條件可能適用于[IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)的執行程式：

- 定義 provider 類別時，Windows PowerShell 內容提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法的執行必須確保傳遞至方法的路徑符合指定之功能的需求。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`，否則此方法的覆寫不應抓取使用者所隱藏物件的讀取器。 如果路徑代表使用者所隱藏的專案，而且[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)已設定為`false`，則應該寫入錯誤。

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>將動態參數附加至 Get Content Cmdlet

`Get-Content` Cmdlet 可能需要在執行時間動態指定的其他參數。 為了提供這些動態參數，Windows PowerShell 內容提供者必須執行[IcontentCmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)類似的剖析屬性。目標. Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。

這個 Windows PowerShell 容器提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>正在抓取內容寫入器

若要將內容寫入專案，提供者必須執行[IcontentCmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) ，以支援`Set-Content`和`Add-Content` Cmdlet。 這個方法會傳回位於指定路徑之專案的內容寫入器。

以下是這個方法的[IcontentCmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)的執行方式。

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>執行 GetContentWriter 的相關事項

下列條件可能適用于您的[IcontentCmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)的執行方式：

- 定義 provider 類別時，Windows PowerShell 內容提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [IcontentCmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法的執行必須確保傳遞至方法的路徑符合指定之功能的需求。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`，否則此方法的覆寫不應抓取使用者所隱藏之物件的寫入器。 如果路徑代表使用者所隱藏的專案，而且[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)已設定為`false`，則應該寫入錯誤。

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>將動態參數附加至新增內容和設定內容 Cmdlet

`Add-Content` 和`Set-Content` Cmdlet 可能需要新增執行時間的其他動態參數。 為了提供這些動態參數，Windows PowerShell 內容提供者必須執行[IcontentCmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法來處理這些參數。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)類似的剖析屬性。目標. Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。

這個 Windows PowerShell 容器提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>清除內容

您的內容提供者會執行[IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以支援`Clear-Content` Cmdlet。 這個方法會移除指定路徑中的專案內容，但保留專案不變。

以下是此提供者的[IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法的執行。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>執行 ClearContent 的相關事項

下列條件可能適用于[IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)的執行程式：

- 定義 provider 類別時，Windows PowerShell 內容提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法的執行必須確保傳遞至方法的路徑符合指定之功能的需求。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`，否則，此方法的覆寫不應清除使用者隱藏的物件內容。 如果路徑代表使用者所隱藏的專案，而且[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)已設定為`false`，則應該寫入錯誤。

- 您的[IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法應會呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並確認其傳回值的執行方式，並加以驗證。對資料存放區進行任何變更之前。 這個方法是用來在對資料存放區進行變更（例如清除內容）時，確認作業的執行。 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會將要變更的資源名稱傳送給使用者，而 Windows PowerShell 執行時間會處理中的任何命令列設定或喜好設定變數。決定應該顯示的內容。

  在呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) `true`後傳回後， [IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法應該會呼叫[，而該程式會傳回Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法的。 這個方法會將訊息傳送給使用者，以允許意見反應來驗證作業是否應該繼續。 呼叫[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允許額外檢查是否有潛在危險的系統修改。

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>將動態參數附加至 Clear 內容 Cmdlet

`Clear-Content` Cmdlet 可能需要在執行時間新增的其他動態參數。 為了提供這些動態參數，Windows PowerShell 內容提供者必須執行[IcontentCmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法來處理這些參數。 這個方法會在指定的路徑中抓取專案的參數。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)類似的剖析屬性。目標. Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。

這個 Windows PowerShell 容器提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>程式碼範例

如需完整的範例程式碼，請參閱[AccessDbProviderSample06 程式碼範例](./accessdbprovidersample06-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

撰寫提供者時，可能需要將成員加入至現有的物件或定義新的物件。 完成此動作時，您必須建立類型檔案，Windows PowerShell 可以使用此檔案來識別物件的成員，以及定義如何顯示物件的格式檔案。 如需詳細資訊，請參閱[擴充物件類型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-windows-powershell-provider"></a>建立 Windows PowerShell 提供者

請參閱[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試。 例如，測試範例內容提供者。

使用 Cmdlet，在`Path`參數所指定的路徑上，抓取資料庫資料表中指定專案的內容。 `Get-Content` `ReadCount`參數會指定要讀取之已定義內容讀取器的專案數（預設為1）。 使用下列命令專案，Cmdlet 會從資料表中抓取兩個數據列（專案），並顯示其內容。 請注意，下列範例輸出會使用虛構的 Access 資料庫。

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>另請參閱

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[擴充物件類型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[執行流覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)

[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)
