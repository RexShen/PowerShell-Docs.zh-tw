---
title: 建立 Windows PowerShell 瀏覽提供者
ms.date: 09/13/2016
ms.openlocfilehash: 0c9714c396a023516cd1c409e598d61bb6cda3ce
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778987"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>建立 Windows PowerShell 瀏覽提供者

本主題說明如何建立可流覽資料存放區的 Windows PowerShell 流覽提供者。 這種類型的提供者支援遞迴命令、嵌套容器和相對路徑。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的 c # 原始程式檔 (AccessDBSampleProvider05.cs) 。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。 如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。

這裡所述的提供者可讓使用者將 Access 資料庫當做磁片磁碟機來處理，讓使用者可以流覽至資料庫中的資料表。 在建立您自己的導覽提供者時，您可以執行方法，以建立導覽所需的磁片磁碟機路徑、將相對路徑標準化、移動資料存放區的專案，以及取得子名稱的方法、取得專案的父路徑，以及測試以識別專案是否為容器。

> [!CAUTION]
> 請注意，這項設計假設有一個具有名稱識別碼之欄位的資料庫，而且欄位的類型是 LongInteger。

## <a name="define-the-windows-powershell-provider"></a>定義 Windows PowerShell 提供者

Windows PowerShell 流覽提供者必須建立一個衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基類的 .net 類別，。 以下是本節所述之導覽提供者的類別定義。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="31-32":::

請注意，在此提供者中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。 第一個參數會為 Windows PowerShell 所使用的提供者指定易記的名稱。 第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。 對於此提供者，不會新增任何 Windows PowerShell 特有的功能。

## <a name="defining-base-functionality"></a>定義基本功能

如[設計您的 PS 提供者](./designing-your-windows-powershell-provider.md)中所述， [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基類衍生自提供不同提供者功能的其他幾個類別。 因此，Windows PowerShell 流覽提供者必須定義這些類別所提供的所有功能。

若要執行功能來新增會話特定的初始化資訊，以及釋放提供者所使用的資源，請參閱[建立基本的 PS 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者 (包括這裡所述的提供者) 可以使用 Windows PowerShell 所提供的這項功能的預設執行。

若要透過 Windows PowerShell 磁片磁碟機取得資料存放區的存取權，您必須執行[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的方法。 如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基類所提供的方法。 如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。

若要取得資料存放區的子專案（或其名稱），以及建立、複製、重新命名和移除專案的方法，您必須執行[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基類所提供的方法。 如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。

## <a name="creating-a-windows-powershell-path"></a>建立 Windows PowerShell 路徑

Windows PowerShell 流覽提供者會使用提供者內部的 Windows PowerShell 路徑來流覽資料存放區的專案。 若要建立提供者內部路徑，提供者必須執行[NavigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法，以支援來自合併-path Cmdlet 的呼叫。 這個方法會使用父系和子路徑之間提供者特定的路徑分隔符號，將父系和子路徑結合成提供者內部路徑。

預設的執行會採用 "/" 或 " \\ " 路徑做為路徑分隔符號、將路徑分隔符號正規化為 " \\ "、結合父系和子路徑部分與它們之間的分隔符號，然後傳回包含合併路徑的字串。

此導覽提供者不會執行此方法。 不過，下列程式碼是[NavigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法的預設實值。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>執行 MakePath 的相關事項

下列條件可能適用于您的[NavigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)的執行方式：

- 您的[NavigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法的執行不應在提供者命名空間中驗證路徑是否為合法的完整路徑。 請注意，每個參數只能代表路徑的一部分，而組合的元件可能不會產生完整路徑。 例如，filesystem 提供者的[NavigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法可能會在參數中收到 "windows\system32" `parent` ，並在參數中接收 "abc.dll" `child` 。 方法會將這些值與 " \\ " 分隔符號聯結，並傳回 "windows\system32\abc.dll"，這不是完整的檔案系統路徑。

  > [!IMPORTANT]
  > [NavigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)的呼叫中所提供的路徑部分可能包含提供者命名空間中不允許的字元。 這些字元最有可能用於萬用字元擴充，而此方法的執行不應將其移除。

## <a name="retrieving-the-parent-path"></a>正在抓取父路徑

Windows PowerShell 導覽提供者會執行[NavigationCmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法，以取得指定完整或部分提供者特定路徑的父系部分。 方法會移除路徑的子部分，並傳回父路徑部分。 `root`參數會指定磁片磁碟機根目錄的完整路徑。 如果載入的磁片磁碟機不是用於抓取作業，此參數可以是 null 或空白。 如果指定了根，此方法必須傳回與根相同之樹狀結構中容器的路徑。

範例導覽提供者不會覆寫這個方法，而是使用預設的實作為。
它接受使用 "/" 和 " \\ " 做為路徑分隔符號的路徑。 它會先將路徑正規化，使其只有 " \\ " 分隔符號，然後在最後一個 "" 分割父路徑，然後傳回 \\ 父路徑。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>若要記住如何執行 GetParentPath

您的[NavigationCmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法應會在提供者命名空間的路徑分隔符號上分割路徑。 例如，filesystem 提供者會使用這個方法來尋找最後一個 " \\ "，並傳回分隔符號左邊的所有內容。

## <a name="retrieve-the-child-path-name"></a>取出子路徑名稱

您的導覽提供者會執行[NavigationCmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法，以取得專案子系的名稱 (分葉元素) ，該專案位於指定的完整或部分提供者特定路徑上。

範例導覽提供者不會覆寫這個方法。 預設的執行如下所示。 它接受使用 "/" 和 " \\ " 做為路徑分隔符號的路徑。 它會先將路徑正規化，使其只有 " \\ " 分隔符號，然後在最後一個 "" 分割父路徑， \\ 並傳回子路徑部分的名稱。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>執行 GetChildName 的相關事項

您的[NavigationCmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法應會在路徑分隔符號上以詞法方式分割路徑。 如果提供的路徑未包含路徑分隔符號，此方法應該會傳回未修改的路徑。

> [!IMPORTANT]
> 呼叫此方法時所提供的路徑可能包含在提供者命名空間中不合法的字元。 這些字元最可能用於萬用字元擴充或正則運算式比對，而此方法的執行不應將其移除。

## <a name="determining-if-an-item-is-a-container"></a>判斷專案是否為容器

導覽提供者可以執行[NavigationCmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法，以判斷指定的路徑是否表示容器。 如果路徑代表容器，則會傳回 true，否則會傳回 false。 使用者需要此方法才能 `Test-Path` 針對提供的路徑使用 Cmdlet。

下列程式碼顯示範例導覽提供者中的[NavigationCmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)執行。 方法會驗證指定的路徑是否正確，以及資料表是否存在，如果路徑指出容器，則會傳回 true。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="847-872":::

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>執行 IsItemContainer 的相關事項

您的導覽提供者 .NET 類別可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中，宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在此情況下， [NavigationCmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)的執行必須確保傳遞的路徑符合需求。 若要這樣做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)屬性（property）。

## <a name="moving-an-item"></a>移動專案

在支援 Cmdlet 的同時 `Move-Item` ，您的導覽提供者會執行[NavigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。 這個方法會在參數中提供的路徑上，將參數所指定的專案移 `path` 至容器 `destination` 。

範例導覽提供者不會覆寫[NavigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。 以下是預設的執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>執行 MoveItem 的相關事項

您的導覽提供者 .NET 類別可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中，宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在此情況下， [NavigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)的執行必須確保傳遞的路徑符合需求。 若要這麼做，方法應該存取適當的屬性，例如**CmdletProvider**屬性。

根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為，否則此方法的覆寫不應將物件移到現有的物件上 `true` 。 例如，filesystem 提供者不會將 c:\temp\abc.txt 複製到現有的 c:\bar.txt 檔案，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true` 。 如果參數中指定的路徑 `destination` 存在，而且是容器，則不需要[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。 在此情況下， [NavigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)應該將參數所指示的專案移 `path` 至參數所指示的容器， `destination` 做為子系。

您的 NavigationCmdletprovider 必須先呼叫[Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法，然後在對資料存放區進行任何變更之前，先檢查它的傳回值，然後再執行此[程式](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)。 這個方法是用來在對系統狀態進行變更（例如刪除檔案）時，確認作業的執行。
[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳送要變更的資源名稱給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數列入決定要向使用者顯示的內容。

在呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)後傳回後 `true` ， [NavigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法應會呼叫 system.servicemodel [. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法，並將其命名為.... 管理介面。 這個方法會將訊息傳送給使用者，以便在應該繼續作業的情況下，提供意見反應。 您的提供者應該呼叫[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作為額外檢查，以進行潛在危險的系統修改。

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>將動態參數附加至移動專案 Cmdlet

有時，此 `Move-Item` Cmdlet 需要在執行時間動態提供的其他參數。 若要提供這些動態參數，導覽提供者必須執行[NavigationCmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法，以從指定路徑的專案中取得必要的參數值，並傳回具有屬性和欄位的物件，而該物件具有類似 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件的剖析屬性。

此導覽提供者不會執行此方法。 不過，下列程式碼是[NavigationCmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>正規化相對路徑

您的導覽提供者會執行[NavigationCmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法，以將參數中指出的完整路徑正規化 `path` 為相對於參數所指定的路徑 `basePath` 。 方法會傳回正規化路徑的字串標記法。 如果參數指定了不存在的路徑，則會寫入錯誤 `path` 。

範例導覽提供者不會覆寫這個方法。 以下是預設的執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>執行 NormalizeRelativePath 的相關事項

您的[NavigationCmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)應會剖析 `path` 參數，但不需要使用純粹的語法剖析程式。 建議您設計這個方法，以使用路徑來查閱資料存放區中的路徑資訊，並建立符合大小寫和標準化路徑語法的路徑。

## <a name="code-sample"></a>程式碼範例

如需完整的範例程式碼，請參閱[AccessDbProviderSample05 程式碼範例](./accessdbprovidersample05-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

提供者可能會將成員新增至現有的物件，或定義新的物件。 如需詳細資訊，請參閱[擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))。

## <a name="building-the-windows-powershell-provider"></a>建立 Windows PowerShell 提供者

如需詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試，包括衍生所提供的 Cmdlet。 這個範例會測試範例導覽提供者。

1. 執行新的 shell，並使用指令程式 `Set-Location` 來設定路徑，以指出 Access 資料庫。

   ```powershell
   Set-Location mydb:
   ```

2. 現在執行 `Get-Childitem` Cmdlet 來抓取資料庫專案的清單，這是可用的資料庫資料表。 針對每個資料表，此 Cmdlet 也會抓取資料表資料列的數目。

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```Output
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

3. 再次使用 `Set-Location` Cmdlet 來設定 Employees 資料表的位置。

   ```powershell
   Set-Location Employees
   ```

4. 現在讓我們使用 `Get-Location` Cmdlet 來抓取 Employees 資料表的路徑。

   ```powershell
   Get-Location
   ```

   ```Output
   Path
   ----
   mydb:\Employees
   ```

5. 現在，請使用 `Get-Childitem` 輸送至 Cmdlet 的 Cmdlet `Format-Table` 。 這組 Cmdlet 會抓取 Employees 資料表的專案，這是資料表的資料列。 它們會依照 Cmdlet 的指定來格式化 `Format-Table` 。

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```Output
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

6. 您現在可以執行 `Get-Item` Cmdlet 來抓取 employee 資料表的資料列0的專案。

   ```powershell
   Get-Item 0
   ```

   ```Output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. 再次使用 `Get-Item` Cmdlet 來抓取資料列0中專案的員工資料。

   ```powershell
   (Get-Item 0).data
   ```

   ```Output
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

[擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))

[執行容器 Windows PowerShell 提供者](./creating-a-windows-powershell-container-provider.md)

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
