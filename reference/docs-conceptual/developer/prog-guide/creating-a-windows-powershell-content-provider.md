---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 Windows PowerShell 內容提供者
description: 建立 Windows PowerShell 內容提供者
ms.openlocfilehash: 7890f0ab8d1cc7f29bdc077b342bae950cfa7827
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645368"
---
# <a name="creating-a-windows-powershell-content-provider"></a>建立 Windows PowerShell 內容提供者

本主題說明如何建立 Windows PowerShell 提供者，讓使用者能夠運算元據存放區中的專案內容。 因此，可操作專案內容的提供者稱為 Windows PowerShell 內容提供者。

> [!NOTE]
> 您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此提供者的 c # 原始程式檔 (AccessDBSampleProvider06.cs) 。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。 如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

## <a name="define-the-windows-powershell-content-provider-class"></a>定義 Windows PowerShell 內容提供者類別

Windows PowerShell 的內容提供者必須建立支援 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面的 .net 類別。 以下是本節所述之專案提供者的類別定義。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="32-33":::

請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 屬性包含兩個參數。 第一個參數會指定 Windows PowerShell 所使用之提供者的使用者易記名稱。 第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。 對於此提供者，沒有新增 Windows PowerShell 的特定功能。

## <a name="define-functionality-of-base-class"></a>定義基類的功能

如 [設計您的 Windows PowerShell 提供](./designing-your-windows-powershell-provider.md)者所述， [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別衍生自數個提供不同提供者功能的其他類別。 因此，Windows PowerShell 內容提供者，通常會定義這些類別所提供的所有功能。

如需如何執行新增會話特定初始化資訊，以及釋出提供者所用資源之功能的詳細資訊，請參閱 [建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。
不過，大部分的提供者（包括此處所述的提供者）可以使用 Windows PowerShell 所提供的這項功能的預設執行。

若要存取資料存放區，提供者必須在 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 基類的方法中執行。 如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 基類所提供的方法。 如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。

若要處理多層式資料存放區，提供者必須執行 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 基類所提供的方法。 如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。

為了支援遞迴命令、嵌套的容器和相對路徑，提供者必須執行 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 基類。 此外，這個 Windows PowerShell 內容提供者可將 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面附加至 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 基類，因此必須執行該類別所提供的方法，才能執行。」。 如需詳細資訊，請參閱實作為這些方法的詳細資訊，請參閱 [執行導覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)。

## <a name="implementing-a-content-reader"></a>執行內容讀取程式

若要從專案讀取內容，提供者必須執行衍生自 [Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)的內容讀取者類別。
此提供者的內容讀取器允許存取資料表中的資料列內容。 內容讀取器類別會定義 **讀取** 方法，該方法會從指定的資料列抓取資料，並傳回代表該資料的清單、移動內容讀取器的 **Seek** 方法、關閉內容讀取器的 **關閉** 方法，以及 **處置** 方法。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="2115-2241":::

## <a name="implementing-a-content-writer"></a>執行內容寫入器

若要將內容寫入至專案，提供者必須執行從 [Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)衍生的內容寫入器類別。
內容寫入器類別會定義 **寫入** 方法，以寫入指定的資料列內容、移動內容寫入器的 **Seek** 方法、關閉內容寫入器的 **Close** 方法，以及 **Dispose** 方法。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="2250-2394":::

## <a name="retrieving-the-content-reader"></a>正在抓取內容讀取器

若要從專案取得內容，提供者必須執行 [IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 以支援 `Get-Content` Cmdlet。 這個方法會傳回位於指定路徑之專案的內容讀取器。 然後可以開啟讀取器物件來讀取內容。

以下是適用于此提供者之這個方法的 [IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 的實作為。

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1829-1846":::

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>執行 GetContentReader 的注意事項

下列情況可能適用于 [IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)的實作為：

- 定義提供者類別時，Windows PowerShell 內容提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下，IcontentCmdletprovider 的執行必須確定傳遞至方法的路徑符合指定之功能的需求，才能執行此 [程式](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 。 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- 根據預設，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則，此方法的覆寫不應針對使用者所隱藏的物件，取得讀取 `true` 器。 如果路徑代表隱藏于使用者和 Cmdletprovider 中的專案，則應該撰寫錯誤。 [Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 會設定為 `false` 。

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>將動態參數附加至 Get-Content Cmdlet

`Get-Content`Cmdlet 可能需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 內容提供者必須執行 [IcontentCmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 方法。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。

此 Windows PowerShell 容器提供者不會執行此方法。 但是，下列程式碼是此方法的預設執行。

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1853-1856":::

## <a name="retrieving-the-content-writer"></a>正在抓取內容寫入器

若要將內容寫入至專案，提供者必須執行 [IcontentCmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 以支援 `Set-Content` 和 `Add-Content` Cmdlet。 這個方法會傳回位於指定路徑之專案的內容寫入器。

以下是適用于此方法的 [IcontentCmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 的實作為。

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1863-1880":::

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>執行 GetContentWriter 的注意事項

下列情況可能適用于您的 [IcontentCmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)的執行：

- 定義提供者類別時，Windows PowerShell 內容提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下，IcontentCmdletprovider 的執行必須確定傳遞至方法的路徑符合指定之功能的需求，才能執行此 [程式](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 。 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- 根據預設，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則，此方法的覆寫不應針對使用者隱藏的物件取得寫入 `true` 器。 如果路徑代表隱藏于使用者和 Cmdletprovider 中的專案，則應該撰寫錯誤。 [Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 會設定為 `false` 。

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>將動態參數附加至 Add-Content 和 Set-Content Cmdlet

`Add-Content`和 `Set-Content` Cmdlet 可能需要加入執行時間的額外動態參數。 若要提供這些動態參數，Windows PowerShell 內容提供者必須執行 [IcontentCmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 方法來處理這些參數。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。

此 Windows PowerShell 容器提供者不會執行此方法。 但是，下列程式碼是此方法的預設執行。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1887-1890":::

## <a name="clearing-content"></a>清除內容

您的內容提供者在支援 Cmdlet 時，會執行 [IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 方法 `Clear-Content` 。 這個方法會在指定的路徑移除專案的內容，但不會讓專案保持不變。

以下是此提供者的 [IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 方法的執行方式。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1775-1812":::

#### <a name="things-to-remember-about-implementing-clearcontent"></a>執行 ClearContent 的注意事項

下列情況可能適用于 [IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)的實作為：

- 定義提供者類別時，Windows PowerShell 內容提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下，IcontentCmdletprovider 的執行必須確定傳遞至方法的路徑符合指定之功能的需求，才能執行此 [程式](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 。 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- 根據預設，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則，此方法的覆寫不應清除使用者隱藏的物件內容 `true` 。 如果路徑代表隱藏于使用者和 Cmdletprovider 中的專案，則應該撰寫錯誤。 [Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 會設定為 `false` 。

- 您的 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並驗證其傳回值的方法，才能執行。 當變更資料存放區（例如清除內容）時，會使用這個方法來確認作業的執行。 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會傳送要變更給使用者的資源名稱，並以 Windows PowerShell 執行時間處理任何命令列設定或喜好設定變數，以決定應該顯示的內容。

  呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) `true` 會傳回， [IcontentCmdletprovider.. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 方法應該呼叫 [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ，以呼叫 system.object.. * 方法來呼叫. 管理方法。 這個方法會將訊息傳送給使用者，以允許意見反應確認作業是否應該繼續。 對 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 的呼叫，可允許額外檢查可能有危險的系統修改。

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>將動態參數附加至 Clear-Content Cmdlet

此 `Clear-Content` Cmdlet 可能需要在執行時間新增的額外動態參數。 若要提供這些動態參數，Windows PowerShell 內容提供者必須執行 [IcontentCmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 方法來處理這些參數。 這個方法會在指定的路徑上，抓取專案的參數。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。

此 Windows PowerShell 容器提供者不會執行此方法。 但是，下列程式碼是此方法的預設執行。

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1819-1822":::

## <a name="code-sample"></a>程式碼範例

如需完整的範例程式碼，請參閱 [AccessDbProviderSample06 程式碼範例](./accessdbprovidersample06-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

撰寫提供者時，可能需要將成員新增至現有的物件，或定義新的物件。 完成這項操作之後，您必須建立一個類型檔案，Windows PowerShell 可以用來識別物件的成員，以及定義如何顯示物件的格式檔案。 如需詳細資訊，請參閱 [擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))。

## <a name="building-the-windows-powershell-provider"></a>建立 Windows PowerShell 提供者

瞭解 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試。 例如，測試範例內容提供者。

您 `Get-Content` 可以使用 Cmdlet，在參數所指定的路徑上，取得資料庫資料表中指定專案的內容 `Path` 。 `ReadCount`參數會指定已定義內容讀取器要讀取 (預設值 1) 的專案數目。 使用下列命令輸入，Cmdlet 會從資料表中抓取兩個數據列 (專案) ，並顯示其內容。 請注意，下列範例輸出會使用虛構的 Access 資料庫。

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```Output
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

[擴充物件類型和格式化](/previous-versions//ms714665(v=vs.85))

[執行流覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)
