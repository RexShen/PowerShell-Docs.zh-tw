---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 Windows PowerShell 瀏覽提供者
description: 建立 Windows PowerShell 瀏覽提供者
ms.openlocfilehash: 73d4971fb91acaef9e1f20226e7b9b883730e394
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658657"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>建立 Windows PowerShell 瀏覽提供者

本主題說明如何建立可流覽資料存放區的 Windows PowerShell 流覽提供者。 這種類型的提供者支援遞迴命令、嵌套的容器和相對路徑。

> [!NOTE]
> 您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此提供者的 c # 原始程式檔 (AccessDBSampleProvider05.cs) 。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。 如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

此處所述的提供者可讓使用者將 Access 資料庫當作磁片磁碟機來處理，讓使用者可以流覽至資料庫中的資料表。 建立您自己的流覽提供者時，您可以執行方法來建立導覽所需的磁片磁碟機路徑、將相對路徑標準化、移動資料存放區的專案，以及取得子名稱的方法、取得專案的父路徑，以及測試以識別專案是否為容器。

> [!CAUTION]
> 請注意，此設計假設有一個具有名稱識別碼之欄位的資料庫，以及欄位的類型為 LongInteger。

## <a name="define-the-windows-powershell-provider"></a>定義 Windows PowerShell 提供者

Windows PowerShell 的流覽提供者必須建立一個衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 基類的 .net 類別。 以下是本節所述之導覽提供者的類別定義。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="31-32":::

請注意，在此提供者中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 屬性包含兩個參數。 第一個參數會指定 Windows PowerShell 所使用之提供者的使用者易記名稱。 第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。 對於此提供者，不會新增 Windows PowerShell 特定功能。

## <a name="defining-base-functionality"></a>定義基底功能

如 [設計您的 PS 提供者](./designing-your-windows-powershell-provider.md)所述， [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 基類衍生自數個提供不同提供者功能的其他類別。 因此，Windows PowerShell 的流覽提供者必須定義這些類別所提供的所有功能。

若要執行新增會話特定初始化資訊，以及釋出提供者所使用之資源的功能，請參閱 [建立基本的 PS 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者 (包括此處所述的提供者) 可以使用 Windows PowerShell 所提供的這項功能的預設執行。

若要透過 Windows PowerShell 磁片磁碟機取得資料存放區的存取權，您必須執行 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 基類的方法。 如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 基類所提供的方法。 如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。

若要取得資料存放區的子專案或其名稱，以及建立、複製、重新命名和移除專案的方法，您必須先執行 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 基類所提供的方法（base class）。 如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。

## <a name="creating-a-windows-powershell-path"></a>建立 Windows PowerShell 路徑

Windows PowerShell 流覽提供者會使用提供者內部 Windows PowerShell 路徑來導覽資料存放區的專案。 若要建立提供者內部路徑，提供者必須執行 [>navigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 方法，以支援來自 Combine-Path Cmdlet 的呼叫。 這個方法會使用父路徑與子路徑之間的提供者特定路徑分隔符號，將父系和子路徑結合成提供者內部路徑。

預設的執行會以 "/" 或 " \\ " 做為路徑分隔符號，將路徑分隔符號正規化為 " \\ "，將父系和子路徑部分與分隔符號結合，然後傳回包含合併路徑的字串。

此流覽提供者不會執行此方法。 但是，下列程式碼是 [>navigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 方法的預設實值。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>執行 MakePath 的注意事項

下列情況可能適用于您的 [>navigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)的執行：

- 您的 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 方法不應該將路徑驗證為提供者命名空間中合法的完整路徑，以進行驗證。 請注意，每個參數只能代表路徑的一部分，而組合的部分可能不會產生完整的路徑。 例如，filesystem 提供者的 [>navigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 方法可能會在參數中接收 "windows\system32" `parent` ，並在參數中接收 "abc.dll" `child` 。 方法會使用 "" 分隔符號來聯結這些值， \\ 並傳回 "windows\system32\abc.dll"，這不是完整的檔案系統路徑。

  > [!IMPORTANT]
  > [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)中所提供的路徑部分可能包含提供者命名空間中不允許的字元數。 這些字元最有可能用於萬用字元展開，而此方法的執行不應移除它們。

## <a name="retrieving-the-parent-path"></a>正在抓取父路徑

Windows PowerShell 導覽提供者會執行 [>navigationCmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 方法，以取得指定之完整或部分提供者特定路徑的父部分。 方法會移除路徑的子部分，並傳回父路徑部分。 `root`參數會指定磁片磁碟機根目錄的完整路徑。 如果載入的磁片磁碟機未用於抓取作業，這個參數可以是 null 或空的。 如果指定了根，則方法必須傳回與根目錄相同樹狀結構中容器的路徑。

範例流覽提供者不會覆寫這個方法，而是使用預設的實值。
它接受使用 "/" 和 " \\ " 做為路徑分隔符號的路徑。 它會先將路徑正規化為只有 " \\ " 分隔符號，然後將父路徑分割為最後一個 " \\ "，並傳回父路徑。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>若要記住如何執行 GetParentPath

[>navigationCmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法的執行應該針對提供者命名空間的路徑分隔符號，以詞法方式分割路徑。 例如，filesystem 提供者會使用這個方法來尋找最後的 " \\ "，並傳回分隔符號左邊的所有專案。

## <a name="retrieve-the-child-path-name"></a>取出子路徑名稱

您的流覽提供者會 [>navigationCmdletprovider Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 方法，以抓取位於指定的完整或部分提供者特定路徑之專案子系的名稱 (分葉元素) 。

範例流覽提供者不會覆寫這個方法。 預設的執行如下所示。 它接受使用 "/" 和 " \\ " 做為路徑分隔符號的路徑。 它會先將路徑正規化為只有 " \\ " 分隔符號，然後將父路徑分割為最後一個 " \\ "，並傳回子路徑部分的名稱。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>執行 GetChildName 的注意事項

[>navigationCmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法的執行應該在路徑分隔符號上以詞法方式分割路徑。 如果提供的路徑不包含任何路徑分隔符號，則方法應傳回未修改的路徑。

> [!IMPORTANT]
> 呼叫這個方法時所提供的路徑可能包含在提供者命名空間中不合法的字元。 這些字元最有可能用於萬用字元展開或正則運算式比對，而此方法的執行不應移除它們。

## <a name="determining-if-an-item-is-a-container"></a>判斷專案是否為容器

流覽提供者可以執行 [>navigationCmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 方法，以判斷指定的路徑是否表示容器。 如果路徑表示容器，則會傳回 true，否則會傳回 false。 使用者需要此方法才能 `Test-Path` 針對提供的路徑使用 Cmdlet。

下列程式碼顯示範例導覽提供者中的 [>navigationCmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 實作為。 方法會驗證指定的路徑是否正確，以及資料表是否存在，如果路徑指出容器，則會傳回 true。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="847-872":::

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>執行 IsItemContainer 的注意事項

您的流覽提供者 .NET 類別可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在此情況下， [>navigationCmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 的執行必須確保傳遞的路徑符合需求。 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 屬性（property）。

## <a name="moving-an-item"></a>移動專案

在支援 Cmdlet 時 `Move-Item` ，您的流覽提供者會執行 [>navigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 方法。 這個方法會將參數所指定的專案移 `path` 至參數中所提供路徑的容器 `destination` 。

範例流覽提供者不會覆寫 [>navigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 方法。 以下是預設的執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>執行 MoveItem 的注意事項

您的流覽提供者 .NET 類別可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在此情況下， [>navigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 的執行必須確保傳遞的路徑符合需求。 若要這樣做，方法應該存取適當的屬性，例如 **CmdletProvider** 屬性。

根據預設，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則此方法的覆寫不應將物件移至現有的物件 `true` 。 例如，filesystem 提供者不會將 c:\temp\abc.txt 複製到現有的 c:\bar.txt 檔案，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為 `true` 。 如果參數中所指定的路徑 `destination` 存在且為容器，則不需要 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。 在此情況下， [>navigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 應該將參數所指示的專案移 `path` 至參數所指示的容器 `destination` 做為子系。

您的 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。 當對系統狀態進行變更（例如刪除檔案）時，此方法會用來確認執行作業。
[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會傳送要變更給使用者的資源名稱，且 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入考慮，以決定應該向使用者顯示的內容。

呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) `true` 會傳回， [>navigationCmdletprovider.. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 方法應該呼叫 [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ，以呼叫 system.object.. * 方法來呼叫. 管理方法。 這個方法會將訊息傳送給使用者，以允許意見反應指出作業是否應該繼續。 您的提供者應該呼叫 [Cmdletprovider ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 做為額外檢查是否有潛在危險的系統修改。

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>將動態參數附加至 Move-Item Cmdlet

有時 `Move-Item` Cmdlet 需要在執行時間動態提供的額外參數。 若要提供這些動態參數，流覽提供者必須執行 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) ，以從指定路徑的專案中取得必要的參數值，並傳回物件，該物件具有剖析屬性（attribute）的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。

此流覽提供者不會執行此方法。 但是，下列程式碼是 [>navigationCmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>標準化相對路徑

您的流覽提供者會實 [>navigationCmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 方法，將參數中指出的完整路徑正規化為 `path` 相對於參數所指定的路徑 `basePath` 。 方法會傳回正規化路徑的字串表示。 如果參數指定的路徑不存在，則會寫入錯誤 `path` 。

範例流覽提供者不會覆寫這個方法。 以下是預設的執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>執行 NormalizeRelativePath 的注意事項

您的 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 必須剖析 `path` 參數，但不一定要使用純粹的語法剖析，而是您的執行。 建議您將此方法設計為使用路徑來查閱資料存放區中的路徑資訊，並建立符合大小寫和標準化路徑語法的路徑。

## <a name="code-sample"></a>程式碼範例

如需完整的範例程式碼，請參閱 [AccessDbProviderSample05 程式碼範例](./accessdbprovidersample05-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

提供者可能會將成員新增至現有的物件，或定義新的物件。 如需詳細資訊，請參閱[擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))。

## <a name="building-the-windows-powershell-provider"></a>建立 Windows PowerShell 提供者

如需詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試，包括衍生所提供的 Cmdlet。 此範例將測試範例流覽提供者。

1. 執行新的命令介面，並使用指令程式 `Set-Location` 來設定路徑，以指出存取資料庫。

   ```powershell
   Set-Location mydb:
   ```

2. 現在 `Get-Childitem` ，請執行 Cmdlet 來取得資料庫專案的清單，這些專案是可用的資料庫資料表。 針對每個資料表，此 Cmdlet 也會抓取資料表資料列的數目。

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

3. 再次使用指令程式 `Set-Location` 來設定 Employees 資料表的位置。

   ```powershell
   Set-Location Employees
   ```

4. 現在讓我們使用指令程式 `Get-Location` 來取出 employee 資料表的路徑。

   ```powershell
   Get-Location
   ```

   ```Output
   Path
   ----
   mydb:\Employees
   ```

5. 現在使用 `Get-Childitem` 輸送至 Cmdlet 的 Cmdlet `Format-Table` 。 這組 Cmdlet 會抓取 employee 資料表的專案，這是資料表資料列。 這些格式是由 Cmdlet 所指定 `Format-Table` 。

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

6. 您現在可以執行 `Get-Item` Cmdlet，以抓取員工資料表中的資料列0專案。

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

7. 再次使用指令 `Get-Item` 程式，以取得資料列0中專案的員工資料。

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

[擴充物件類型和格式化](/previous-versions/ms714665(v=vs.85))

[執行容器 Windows PowerShell 提供者](./creating-a-windows-powershell-container-provider.md)

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
