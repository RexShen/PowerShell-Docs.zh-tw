---
title: 建立 Windows PowerShell 巡覽提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081847"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>建立 Windows PowerShell 瀏覽提供者

本主題描述如何建立 Windows PowerShell 巡覽提供者，可以瀏覽資料存放區。 這種類型的提供者支援遞迴命令，巢狀的容器和相對路徑。

> [!NOTE]
> 您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此提供者的原始程式檔 (AccessDBSampleProvider05.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。
>
> 如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

此處所述的提供者可讓使用者控制代碼的 Access 資料庫做為磁碟機，以便使用者瀏覽至資料庫中的資料表。 當建立您自己的巡覽提供者，您可以實作方法，可讓瀏覽所需的磁碟機限定路徑、 相對路徑正規化，移動的資料存放區，以及取得子系名稱，取得父路徑的項目，且測試方法的項目若要識別的項目是一個容器。

> [!CAUTION]
> 請注意，這項設計會假設的欄位有名稱識別碼的資料庫和欄位的型別是 LongInteger。

下列清單包含本主題中的區段。 如果您不熟悉如何撰寫 Windows PowerShell 巡覽提供者，請閱讀這項資訊，它會出現的順序。 不過，如果您已熟悉撰寫 Windows PowerShell 巡覽提供者，請直接前往您所需要的資訊。

- [定義的 PS 導覽提供者類別](#Define-the-Windows-PowerShell-provider)

- [定義基底的功能](#Defining-Base-Functionality)

- [建立 PS 路徑](#Creating-a-Windows-PowerShell-Path)

- [正在擷取父路徑](#Retrieving-the-Parent-Path)

- [擷取的子路徑名稱](#Retrieve-the-Child-Path-Name)

- [判斷項目是否為容器](#Determining-if-an-Item-is-a-Container)

- [移動項目](#Moving-an-Item)

- [附加到的動態參數`Move-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [相對路徑正規化](#Normalizing-a-Relative-Path)

- [程式碼範例](#Code-Sample)

- [定義物件類型和格式設定](#Defining-Object-Types-and-Formatting)

- [建置 Windows PowerShell 提供者](#Building-the-Windows-PowerShell-provider)

- [測試 Windows PowerShell 提供者](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>定義 Windows PowerShell 提供者

Windows PowerShell 巡覽提供者必須建立一個.NET 類別衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基底類別。 以下是這一節所述的瀏覽提供者的類別定義。

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

請注意，在此提供者[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。 第一個參數會指定使用 Windows powershell 提供者的使用者易記名稱。 第二個參數指定命令處理期間提供者會公開 Windows PowerShell 執行階段的 Windows PowerShell 特定功能。 此提供者，如有加入任何 Windows PowerShell 特定功能。

## <a name="defining-base-functionality"></a>定義基底的功能

中所述[設計您的 PS Provider](./designing-your-windows-powershell-provider.md)，則[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基底類別衍生自數個其他類別，提供不同的提供者功能。 Windows PowerShell 巡覽提供者，因此，必須定義所有這些類別所提供的功能。

若要實作功能，說明如何加入工作階段特定的初始化資訊，以及用於釋放提供者所使用的資源，請參閱[建立基本的 PS 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者 （包括此處所述的提供者） 可以使用這項功能 Windows PowerShell 所提供的預設實作。

若要存取資料存放區透過 Windows PowerShell 磁碟機，您必須實作的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別。 如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

若要操作的資料存放區，例如開始、 設定和清除項目，項目的提供者必須實作所提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基底類別。 如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)。

取得子系的項目或其名稱、 資料存放區，以及建立、 複製、 重新命名，然後移除項目，方法中，您必須實作所提供的方法[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基底類別。 如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。

## <a name="creating-a-windows-powershell-path"></a>建立 Windows PowerShell 路徑

Windows PowerShell 巡覽提供者會使用提供者內部的 Windows PowerShell 路徑來瀏覽資料存放區的項目。 若要建立的提供者內部路徑提供者必須實作[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)支援的方法呼叫從合併路徑 cmdlet。 這個方法會將父和子路徑結合成一個提供者內部的路徑，使用提供者專屬的路徑分隔符號之間的父和子路徑。

預設實作會使用路徑"/"或"\\"做為路徑分隔符號，將正規化路徑分隔符號，「\\」 結合它們之間的分隔符號中的父和子路徑的任何部分，則會傳回字串，包含合併的路徑。

此瀏覽提供者未實作這個方法。 不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>有關實作 MakePath 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- 您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法不應驗證為合法完整路徑，提供者命名空間中的路徑。 請注意，每個參數只能代表路徑的一部分，並合併組件可能不會產生完整的路徑。 例如， [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) filesystem 提供者的方法中可能會收到 「 windows\system32"`parent`參數和 「 abc.dll"中的`child`參數。 方法會加入這些值取代"\\」 分隔符號，並傳回 「 windows\system32\abc.dll"，也就是不完整的檔案系統路徑。

  > [!IMPORTANT]
  > 呼叫中提供的路徑部分[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)可能包含提供者命名空間中不允許的字元。 這些字元會很有可能會用於萬用字元展開，而且此方法的實作不應該移除它們。

## <a name="retrieving-the-parent-path"></a>正在擷取父路徑

Windows PowerShell 巡覽提供者可實作[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法來擷取父組件所指定完整或部分提供者專屬的路徑。 方法會移除子路徑的一部分，並傳回父系的路徑部分。 `root`參數指定磁碟機根目錄的完整路徑。 這個參數可以是 null 或空白，如果掛接的磁碟機不是用於擷取作業。 如果指定的根，則此方法必須傳回路徑，以 root 身分執行的相同樹狀結構中的容器。

範例導覽提供者未覆寫這個方法，但使用的預設實作。 它可接受同時使用的路徑"/"和"\\」 做為路徑分隔符號。 第一次將正規化路徑只有 「\\"分隔符號，然後將關閉的父路徑分割最後一個"\\"，並傳回父路徑。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>要記住關於實作 GetParentPath

您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法應該分割語彙上提供者命名空間的路徑分隔符號的路徑。 例如，filesystem 提供者會使用這個方法來尋找上次"\\」，並傳回所有項目分隔符號的左邊。

## <a name="retrieve-the-child-path-name"></a>擷取的子路徑名稱

您的瀏覽提供者會實作[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法來擷取項目的子系的名稱 （分葉項目） 位於指定完整或部分提供者專屬的路徑。

範例導覽提供者不會覆寫這個方法。 如下所示的預設實作。 它可接受同時使用的路徑"/"和"\\」 做為路徑分隔符號。 第一次將正規化路徑只有 「\\"分隔符號，然後將關閉的父路徑分割最後一個"\\"，並傳回子物件名稱的路徑部分。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>有關實作 GetChildName 的注意事項

您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法應該分割上的路徑分隔符號語彙的路徑。 如果提供的路徑不包含任何路徑分隔符號，則此方法應該傳回未經修改的路徑。

> [!IMPORTANT]
> 這個方法的呼叫中提供的路徑可能會包含在提供者命名空間中不合法的字元。 這些字元最有可能用於萬用字元展開或規則運算式比對，而且此方法的實作不應該移除它們。

## <a name="determining-if-an-item-is-a-container"></a>判斷項目是否為容器

瀏覽提供者可實作[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)來判斷是否指定的路徑表示容器的方法。 它會傳回路徑可代表容器和 false 否則如果為 true。 使用者必須要能夠使用這個方法`Test-Path`cmdlet 提供的路徑。

下列程式碼示範[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)我們的範例導覽提供者中實作。 此方法會驗證指定的路徑正確無誤，而且如果資料表存在，而且如果的路徑表示容器會傳回 true。

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>有關實作 IsItemContainer 的注意事項

您的瀏覽提供者.NET 類別可以宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除，從[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在此情況下，實作[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)必須確保傳遞路徑符合需求。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)屬性。

## <a name="moving-an-item"></a>移動項目

支援`Move-Item`cmdlet，您的瀏覽提供者會實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。 這個方法會移動指定的項目`path`容器中所提供的路徑參數`destination`參數。

範例導覽提供者不會覆寫[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。 以下是預設的實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>有關實作 MoveItem 的注意事項

您的瀏覽提供者.NET 類別可以宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除，從[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在此情況下，實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)必須確定傳遞路徑符合需求。 若要這樣做，方法應該存取適當的屬性，例如， **CmdletProvider.Exclude**屬性。

根據預設，會覆寫這個方法不能移動物件現有的物件除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 例如，filesystem 提供者不會複製 c:\temp\abc.txt 透過現有 c:\bar.txt 檔案除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 如果在指定的路徑`destination`參數存在，而且是一個容器中， [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。 在此情況下， [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)所指定的項目應該移`path`所指定的參數，以容器`destination`參數做為子系。

您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。 這個方法用來變更系統狀態，例如，刪除檔案時，請確認執行作業。 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)傳送給使用者，變更納入考量，任何命令列設定或喜好設定變數中的 Windows PowerShell 執行階段資源的名稱判斷應該顯示給使用者。

若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 這個方法會將訊息傳送給使用者，以允許說如果應該繼續執行作業的意見反應。 您的提供者應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作為額外的檢查，如有潛在危險的系統修改。

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>附加至 Move-item Cmdlet 的動態參數

有時候`Move-Item`cmdlet 需要在執行階段以動態方式提供的其他參數。 若要提供這些動態參數，請瀏覽提供者必須實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法來取得必要的參數值從位於指定的路徑，並傳回的項目具有屬性和欄位的剖析時的物件屬性類似於 cmdlet 類別或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。

此瀏覽提供者未實作這個方法。 不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>相對路徑正規化

您的瀏覽提供者會實作[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法，以標準化完整的路徑中指出`path`參數相對於所指定的路徑為`basePath`參數。 方法會傳回標準化路徑的字串表示。 它會寫入錯誤，如果`path`參數會指定不存在的路徑。

範例導覽提供者不會覆寫這個方法。 以下是預設的實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>有關實作 NormalizeRelativePath 的注意事項

您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)應剖析`path`參數，但它不需要使用純粹語法的剖析。 這個方法，以使用路徑來查詢資料存放區中的路徑資訊，並建立路徑符合大小寫的設計建議，以及標準化路徑語法。

## <a name="code-sample"></a>程式碼範例

完整的範例程式碼，請參閱[AccessDbProviderSample05 程式碼範例](./accessdbprovidersample05-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式設定

它可讓提供者將成員加入至現有的物件，或定義新的物件。 如需詳細資訊，請參閱 <<c0> [ 延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-windows-powershell-provider"></a>建置的 Windows PowerShell 提供者

如需詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 時，您可以藉由在命令列，包括衍生所提供的指令程式上執行的受支援的 cmdlet 來進行測試。 此範例會測試範例導覽提供者。

1. 執行新的殼層，並使用`Set-Location`cmdlet 來設定表示和存取資料庫的路徑。

   ```powershell
   Set-Location mydb:
   ```

2. 現在執行`Get-Childitem`cmdlet 來擷取一份資料庫項目，也就是可用的資料庫資料表。 每個資料表，此 cmdlet 也會擷取資料表資料列數目。

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. 使用`Set-Location`cmdlet，將員工資料資料表的位置。

   ```powershell
   Set-Location Employees
   ```

4. 現在我們將使用`Get-Location`cmdlet 來擷取員工資料表的路徑。

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. 現在，使用`Get-Childitem`cmdlet 經由管道輸出至`Format-Table`cmdlet。 這組指令程式會擷取針對員工資料表，也就是資料表的資料列的項目。 它們會格式化依照`Format-Table`cmdlet。

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. 您現在可以執行`Get-Item`cmdlet 來擷取員工資料表的資料列 0 的項目。

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. 使用`Get-Item`cmdlet 一次來擷取員工資料的資料列 0 中的項目。

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>另請參閱

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[實作容器的 Windows PowerShell 提供者](./creating-a-windows-powershell-container-provider.md)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)