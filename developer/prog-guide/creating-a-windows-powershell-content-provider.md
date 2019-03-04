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
ms.openlocfilehash: 6e5d79487539d4f58922e2686f1fdba08797f305
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855304"
---
# <a name="creating-a-windows-powershell-content-provider"></a>建立 Windows PowerShell 內容提供者

本主題描述如何建立 Windows PowerShell 提供者，可讓使用者管理的資料存放區中的項目內容。 如此一來，可以操作項目的內容提供者被指 Windows PowerShell 內容提供者。

> [!NOTE]
> 您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此提供者的原始程式檔 (AccessDBSampleProvider06.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
> 您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此提供者的原始程式檔 (AccessDBSampleProvider06.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。
>
> 如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

下列清單包含本主題的章節。 如果您不熟悉如何撰寫 Windows PowerShell 內容提供者，閱讀這些章節中出現的順序。 不過，如果您已熟悉撰寫 Windows PowerShell 內容提供者，直接移至您所需要的資訊。

- [定義 Windows PowerShell 內容提供者類別](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [定義基底的功能](#Define-Functionality-of-Base-Class)

- [實作內容的讀取器](#Implementing-a-Content-Reader)

- [實作內容的寫入器](#Implementing-a-Content-Writer)

- [擷取內容的讀取器](#Retrieving-the-Content-Reader)

- [附加到的動態參數`Get-Content`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [擷取內容的寫入器](#Retrieving-the-Content-Writer)

- [將動態參數附加至 Add_Content 和`Set-Content`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [清除內容](#Clearing-Content)

- [附加到的動態參數`Clear-Content`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [程式碼範例](#Code-Sample)

- [定義物件類型和格式設定]()

- [建置的 Windows PowerShell 提供者](#Building-the-Windows-PowerShell-Provider)

- [測試 Windows PowerShell 提供者](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>定義 Windows PowerShell 內容提供者類別

Windows PowerShell 內容提供者必須建立一個支援的.NET 類別[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面。 以下是這一節所述的項目提供者的類別定義。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

請注意，在此類別定義中， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。 第一個參數會指定使用 Windows powershell 提供者的使用者易記名稱。 第二個參數指定命令處理期間提供者會公開 Windows PowerShell 執行階段的 Windows PowerShell 特定功能。 此提供者中，沒有新增的 Windows PowerShell 的特定功能。

## <a name="define-functionality-of-base-class"></a>定義基底類別的功能

中所述[設計您 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)，則[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別衍生自所提供的其他幾項類別不同的提供者的功能。 Windows PowerShell 內容提供者，因此，通常會定義所有的這些類別所提供的功能。

如需如何實作功能，說明如何加入工作階段特定的初始化資訊，以及用於釋放提供者所使用的資源的詳細資訊，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者，包括此處描述的提供者可以使用這項功能所提供的 Windows PowerShell 的預設實作。

若要存取資料存放區，提供者必須實作的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別。 如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

若要操作的資料存放區，例如開始、 設定和清除項目，項目的提供者必須實作所提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基底類別。 如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)。

若要在多層資料存放區中工作，提供者必須實作所提供的方法[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基底類別。 如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。

若要支援遞迴命令，巢狀的容器和相對路徑，提供者必須實作[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基底類別。 此外，此 Windows PowerShell 內容提供者可以附加[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基底類別，並因此必須實作該類別所提供的方法。 如需詳細資訊，請參閱 < 實作這些方法，請參閱 <<c0> [ 實作的瀏覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)。

## <a name="implementing-a-content-reader"></a>實作內容的讀取器

若要讀取項目的內容，提供者必須實作內容的讀取器類別衍生自[System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)。 此提供者的內容讀取器資料表中的資料允許存取資料列的內容。 內容的讀取器類別會定義**讀取**方法，從指定的資料列擷取資料，並傳回表示該資料，清單**搜尋**方法，它會將內容的讀取器， **關閉**關閉之內容的讀取器的方法和**處置**方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>實作內容的寫入器

若要寫入項目中的內容，提供者必須實作的內容寫入器類別衍生自[System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)。 內容的寫入器類別會定義**撰寫**寫入指定的資料列內容，方法**Seek**方法，它會將內容寫入器，**關閉**關閉的方法內容的寫入器，以及**處置**方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>擷取內容的讀取器

若要取得內容項目，提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)支援`Get-Content`cmdlet。 這個方法會傳回位於指定路徑的項目內容的讀取器。 然後，讀取器物件可以開啟來讀取內容。

以下是實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)這個方法，此提供者。

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

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>有關實作 GetContentReader 的注意事項

在下列情況可能適用於實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Windows PowerShell 內容提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法必須確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，會覆寫這個方法不應該擷取除非隱藏使用者物件的讀取器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 應該寫入錯誤，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為`false`。

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>將動態參數附加至 Get-content Cmdlet

`Get-Content` Cmdlet 可能需要在執行階段動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 內容提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。 這個方法會擷取動態參數所指出的路徑處的項目，並傳回物件，此物件具有屬性與欄位類似於 cmdlet 類別屬性的剖析或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件，將參數新增至 cmdlet。

此 Windows PowerShell 容器提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>擷取內容的寫入器

若要寫入項目中的內容，提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)支援`Set-Content`和`Add-Content`cmdlet。 這個方法會傳回位於指定路徑的項目內容的寫入器。

以下是實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)這個方法。

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

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>有關實作 GetContentWriter 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Windows PowerShell 內容提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法必須確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，會覆寫這個方法不應該擷取除非隱藏使用者物件的寫入器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 應該寫入錯誤，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為`false`。

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>將動態參數附加至 Add-content 和 Set-content Cmdlet

`Add-Content`和`Set-Content`cmdlet 可能需要加入執行階段的其他動態參數。 若要提供這些動態參數，Windows PowerShell 內容提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)處理這些方法參數。 這個方法會擷取動態參數所指出的路徑處的項目，並傳回物件，此物件具有屬性與欄位類似於 cmdlet 類別屬性的剖析或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件，將參數新增至 cmdlet。

此 Windows PowerShell 容器提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>清除內容

您的內容提供者會實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)支援的方法`Clear-Content`cmdlet。 這個方法會移除在指定的路徑、 項目的內容，但會保留項目。

以下是實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)此提供者的方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>有關實作 ClearContent 的注意事項

在下列情況可能適用於實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Windows PowerShell 內容提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法必須確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，覆寫這個方法不應清除的物件，除非使用者隱藏的內容[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 應該寫入錯誤，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為`false`。

- 您實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並確認它的傳回值之前對資料存放區中的任何變更。 這個方法用來變更資料存放區，例如清除內容時，請確認執行作業。 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會傳送給使用者，以處理任何命令列設定或喜好設定，Windows PowerShell 執行階段變更資源的名稱在決定應該要顯示的內容變數。

  若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 這個方法會將訊息傳送給使用者，以允許確認是否應該繼續執行作業的意見反應。 若要在呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允許額外的檢查，如有潛在危險的系統修改。

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>附加至 Clear-content Cmdlet 的動態參數

`Clear-Content` Cmdlet 可能需要在執行階段加入的其他動態參數。 若要提供這些動態參數，Windows PowerShell 內容提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)處理這些方法參數。 這個方法會擷取位於指定路徑的項目參數。 這個方法會擷取動態參數所指出的路徑處的項目，並傳回物件，此物件具有屬性與欄位類似於 cmdlet 類別屬性的剖析或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件，將參數新增至 cmdlet。

此 Windows PowerShell 容器提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>程式碼範例

完整的範例程式碼，請參閱[AccessDbProviderSample06 程式碼範例](./accessdbprovidersample06-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式設定

當撰寫提供者，它可能需要將成員加入至現有的物件，或定義新的物件。 完成時，您必須建立 Windows PowerShell 可以用來識別物件的成員類型檔案與格式檔案，定義物件的顯示方式。 如需詳細資訊，請參閱 <<c0> [ 延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。
當撰寫提供者，它可能需要將成員加入至現有的物件，或定義新的物件。 完成時，您必須建立 Windows PowerShell 可以用來識別物件的成員類型檔案與格式檔案，定義物件的顯示方式。 如需詳細資訊，請參閱 <<c0> [ 延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-windows-powershell-provider"></a>建置 Windows PowerShell 提供者

請參閱[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。
請參閱[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 時，您可以藉由在命令列上執行受支援的 cmdlet 來進行測試。 例如，測試範例的內容提供者。

使用`Get-Content`cmdlet 來擷取所指定路徑上的資料庫資料表中的指定項目的內容`Path`參數。 `ReadCount`參數會指定定義內容的讀取器讀取 （預設值 1） 的項目數。 下列命令項目，此 cmdlet 會從資料表中擷取兩個資料列 （項目），並顯示其內容。 請注意，下列範例輸出會使用虛構的 Access 資料庫。

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

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[實作瀏覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)
