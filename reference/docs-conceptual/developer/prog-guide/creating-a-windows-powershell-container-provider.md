---
title: 建立 Windows PowerShell 容器提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: fcb03d4021f00837095ce703beb0d841233391d6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416208"
---
# <a name="creating-a-windows-powershell-container-provider"></a>建立 Windows PowerShell 容器提供者

本主題說明如何建立可在多層式資料存放區上使用的 Windows PowerShell 提供者。 對於這種類型的資料存放區，存放區的最上層包含根專案，而每個後續層級稱為子專案的節點。 藉由允許使用者在這些子節點上工作，使用者可以透過資料存放區以階層方式進行互動。

可在多層級資料存放區上工作的提供者稱為 Windows PowerShell 容器提供者。 不過，請注意，只有在有一個容器（沒有嵌套的容器）包含專案時，才可以使用 Windows PowerShell 容器提供者。 如果有嵌套的容器，則您必須執行 Windows PowerShell 流覽提供者。 如需有關執行 Windows PowerShell 流覽提供者的詳細資訊，請參閱[建立 Windows Powershell 流覽提供者](./creating-a-windows-powershell-navigation-provider.md)。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的原始程式檔（AccessDBSampleProvider04.cs）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。
>
> 如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。

這裡所述的 Windows PowerShell 容器提供者會將資料庫定義為其單一容器，並將資料庫的資料表和資料列定義為容器的專案。

> [!CAUTION]
> 請注意，這項設計假設有一個具有名稱識別碼之欄位的資料庫，而且欄位的類型是 LongInteger。

## <a name="defining-a-windows-powershell-container-provider-class"></a>定義 Windows PowerShell 容器提供者類別

Windows PowerShell 容器提供者必須定義一個衍生自[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基類的 .net 類別（class）。 以下是本節所述 Windows PowerShell 容器提供者的類別定義。

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。 第一個參數會為 Windows PowerShell 所使用的提供者指定易記的名稱。 第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。 對於此提供者，不會新增任何 Windows PowerShell 特有的功能。

## <a name="defining-base-functionality"></a>定義基本功能

如[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)中所述， [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別衍生自數個提供不同提供者功能的其他類別。 因此，Windows PowerShell 容器提供者必須定義這些類別所提供的所有功能。

若要執行功能來新增會話特定的初始化資訊，以及釋放提供者所使用的資源，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者（包括這裡所述的提供者）都可以使用 Windows PowerShell 所提供的這項功能的預設執行。

若要取得資料存放區的存取權，提供者必須執行[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的方法。 如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基類所提供的方法。 如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。

## <a name="retrieving-child-items"></a>正在抓取子專案

若要取出子專案，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以支援來自 `Get-ChildItem` Cmdlet 的呼叫。 這個方法會從資料存放區抓取子專案，並將它們以物件的形式寫入管線。 如果指定了 Cmdlet 的 `recurse` 參數，方法會抓取所有子系，不論它們位於哪一層級。 如果未指定 `recurse` 參數，方法只會抓取單一層級的子系。

以下是此提供者的[ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行。 請注意，此方法會在路徑指出 Access 資料庫時，抓取所有資料庫資料表中的子專案，並在路徑表示資料表時，從該資料表的資料列抓取子專案。

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>執行 GetChildItems 的相關事項

下列條件可能適用于您的[ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行方式：

- 定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 此方法的實體系應該考慮到可能會讓使用者看見專案的任何形式的存取權。 例如，如果使用者透過 FileSystem 提供者（由 Windows PowerShell 提供）擁有檔案的寫入存取權，但沒有讀取權限，檔案仍然存在，而且[ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)會傳回 `true`。 您的執行可能需要檢查父專案，以查看是否可以列舉子系。

- 寫入多個專案時， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法可能需要一些時間。 您可以設計提供者，以一次使用[Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法來撰寫專案。 使用這項技術會向使用者呈現串流中的專案。

- 您的[ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)會負責防止無限遞迴（如有迴圈連結），以及 like。 應擲回適當的終止例外狀況，以反映這種情況。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>將動態參數附加至 Get-childitem Cmdlet

有時會呼叫[ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的 `Get-ChildItem` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Get-ChildItem` Cmdlet。

這個 Windows PowerShell 容器提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>正在抓取子專案名稱

若要取得子專案的名稱，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以支援在指定其 `Name` 參數時，從 `Get-ChildItem` Cmdlet 呼叫。 如果指定了 Cmdlet 的 `returnAllContainers` 參數，這個方法會抓取所有容器之指定路徑或子專案名稱的子專案名稱。 子名稱是路徑的分葉部分。 例如，路徑 c:\windows\system32\abc.dll 的子名稱是 "abc"。 目錄 c:\windows\system32 的子名稱是 "system32"。

以下是此提供者的[ContainerCmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法的執行。 請注意，如果指定的路徑指示資料表的 Access 資料庫（磁片磁碟機）和資料列編號，方法會抓取資料表名稱。

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>執行 GetChildNames 的相關事項

下列條件可能適用于您的[ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行方式：

- 定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

  > [!NOTE]
  > 指定 Cmdlet 的 `returnAllContainers` 參數時，就會發生此規則的例外狀況。 在這種情況下，方法應該會抓取容器的任何子系名稱，即使它不符合[Cmdletprovider. Filter *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter)、 [Cmdletprovider.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)Cmdletprovider * 的值，也不會包含 *，或[。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)屬性（property）的值。

- 根據預設，除非指定了[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ，否則此方法的覆寫不應抓取使用者通常會隱藏的物件名稱，。 如果指定的路徑指出容器，則不需要[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。」

- 您的[ContainerCmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)會負責防止無限遞迴（如有迴圈連結），以及 like。 應擲回適當的終止例外狀況，以反映這種情況。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>將動態參數附加至 Get-childitem Cmdlet （名稱）

有時候 `Get-ChildItem` Cmdlet （具有 `Name` 參數）需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。 這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Get-ChildItem` Cmdlet。

此提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>重新命名專案

若要重新命名專案，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，以支援來自 `Rename-Item` Cmdlet 的呼叫。 這個方法會將指定路徑的專案名稱變更為提供的新名稱。 新名稱必須一律相對於父專案（容器）。

此提供者不會覆寫[ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法。 不過，下列是預設的執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>執行 RenameItem 的相關事項

下列條件可能適用于您的[ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)的執行方式：

- 定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- [ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法僅適用于修改專案的名稱，而不是用於移動作業的程式。 如果 `newName` 參數包含路徑分隔符號，或可能導致專案變更其父系位置，則您的方法的執行應該會寫入錯誤。

- 根據預設，除非指定了[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ，否則此方法的覆寫不應重新命名物件。 如果指定的路徑指出容器，則不需要[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。」

- 您的 ContainerCmdletprovider 必須先呼叫[Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，然後在對資料存放區進行任何變更之前，先檢查它的傳回值，然後再執行此[程式](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)。 這個方法是用來在對系統狀態進行變更時（例如，重新命名檔案），確認作業的執行。 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳送要變更的資源名稱給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入決定應該顯示的內容。

  呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 `true`，則[ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法應會呼叫 system.servicemodel. Cmdletprovider [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ShouldContinue 方法（.........）。 這個方法會傳送一則確認訊息給使用者，以允許額外的意見反應，以指出作業是否應該繼續。 提供者應呼叫[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作為額外檢查，以進行潛在危險的系統修改。

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>將動態參數附加至重新命名專案 Cmdlet

有時候 `Rename-Item` Cmdlet 需要在執行時間動態指定的其他參數。 為了提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。 這個方法會在指定的路徑中抓取專案的參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Rename-Item` Cmdlet。

此容器提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>建立新專案

若要建立新的專案，容器提供者必須執行[ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以支援來自 `New-Item` Cmdlet 的呼叫。 這個方法會建立位於指定路徑的資料項目。 Cmdlet 的 `type` 參數包含新專案的提供者定義型別。 例如，FileSystem 提供者會使用值為 "file" 或 "directory" 的 `type` 參數。 Cmdlet 的 `newItemValue` 參數會指定新專案的提供者特定值。

以下是此提供者的[ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法的執行。

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>執行 NewItem 的相關事項

下列條件可能適用于您的[ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行方式：

- [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應針對在 `type` 參數中傳遞的字串執行不區分大小寫的比較。 它也應該允許最少不明確的相符專案。 例如，針對 "file" 和 "directory" 類型，只需要第一個字母來區分。 如果 `type` 參數指出提供者無法建立的類型，則[ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該使用訊息來撰寫 ArgumentException，指出提供者可以建立的類型。

- 針對 `newItemValue` 參數，建議使用[ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法的實值，以最小者接受字串。 它也應該針對相同的路徑，接受[Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法所抓取的物件型別（ItemCmdletprovider）。 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法可以使用[languageprimitives.physicalequality. convertto-html *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo)方法，將型別轉換成所需的型別（types）。

- 您的 ContainerCmdletprovider 必須先呼叫[Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，然後在對資料存放區進行任何變更之前，先檢查它的傳回值，然後再執行此[程式](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)。 呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true，則[ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應呼叫[方法，](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)以做為可能危險的系統修改的額外檢查，以做為其他的檢查，以進行系統管理。

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>將動態參數附加至新的-Item Cmdlet

有時候 `New-Item` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，容器提供者必須執行[ContainerCmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。 這個方法會在指定的路徑中抓取專案的參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `New-Item` Cmdlet。

此提供者不會執行此方法。 不過，下列程式碼是這個方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>移除專案

若要移除專案，Windows PowerShell 提供者必須覆寫[ContainerCmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以支援來自 `Remove-Item` Cmdlet 的呼叫。 這個方法會在指定路徑的資料存放區中刪除專案。 如果 `Remove-Item` Cmdlet 的 `recurse` 參數設定為 `true`，則方法會移除所有子專案，而不論其層級為何。 如果參數設定為 `false`，此方法只會移除指定路徑中的單一專案。

此提供者不支援移除專案。 不過，下列程式碼是[ContainerCmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>執行 RemoveItem 的相關事項

下列條件可能適用于您的[ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行方式：

- 定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 true，否則此方法的覆寫不應移除物件。 如果指定的路徑指出容器，則不需要[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。」

- 您的[ContainerCmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)會負責防止無限遞迴（如有迴圈連結），以及 like。 應擲回適當的終止例外狀況，以反映這種情況。

- 您的 ContainerCmdletprovider 必須先呼叫[Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，然後在對資料存放區進行任何變更之前，先檢查它的傳回值，然後再執行此[程式](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)。 呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 `true`，則[ContainerCmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法應呼叫[方法，](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)以做為可能危險的系統修改的額外檢查，以做為其他的檢查，以進行系統管理。

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>將動態參數附加至 Remove 專案 Cmdlet

有時候 `Remove-Item` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，容器提供者必須執行[ContainerCmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法來處理這些參數。 這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Remove-Item` Cmdlet。

此容器提供者不會執行此方法。 不過，下列程式碼是[ContainerCmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>查詢子專案

若要查看子專案是否存在於指定的路徑，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。 如果專案具有子系，這個方法會傳回 `true`，否則會傳回 `false`。 對於 null 或空路徑，方法會將資料存放區中的任何專案視為子系，並傳回 `true`。

以下是[ContainerCmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法的覆寫：。 如果 ChunkPath helper 方法建立兩個以上的路徑部分，此方法會傳回 `false`，因為只會定義資料庫容器和資料表容器。 如需此協助程式方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)中所討論的 ChunkPath 方法。

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>執行 HasChildItems 的相關事項

下列條件可能適用于您的[ContainerCmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)的執行方式：

- 如果容器提供者公開包含感興趣之掛接點的根，則在為路徑傳入 null 或空字串時，ContainerCmdletprovider 應該會傳回 `true` 的[Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。

## <a name="copying-items"></a>複製專案

若要複製專案，容器提供者必須執行[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以支援來自 `Copy-Item` Cmdlet 的呼叫。 這個方法會從 Cmdlet 的 `path` 參數所指示的位置，將資料項目複製到 `copyPath` 參數所指示的位置。 如果指定了 `recurse` 參數，方法會複製所有子容器。 如果未指定參數，方法只會複製單一層級的專案。

此提供者不會執行此方法。 不過，下列程式碼是[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>執行 CopyItem 的相關事項

下列條件可能適用于您的[ContainerCmdletProvider. CopyItem 的程式](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)：

- 定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。 若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。

- 根據預設，除非[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`，否則這個方法的覆寫不應複製現有物件的物件。 例如，FileSystem 提供者不會將 c:\temp\abc.txt 複製到現有的 c:\abc.txt 檔，除非已將[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`。 如果 `copyPath` 參數中指定的路徑存在，並指出容器，則不需要[Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。 在此情況下， [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)會將 `path` 參數所指示的專案複製到 `copyPath` 參數所指示的容器做為子系。

- 您的[ContainerCmdletProvider。 CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)會負責在有迴圈連結時防止無限遞迴，而且也會發生類似的情況。 應擲回適當的終止例外狀況，以反映這種情況。

- 您的[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)必須先呼叫 CopyItem 方法，然後在對資料存放區進行任何變更之前，先檢查其傳回值，然後再進行[此程式。](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true，則[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法應呼叫[方法，](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)以做為可能危險系統修改的額外檢查，以進行進一步的檢查，而不需要進行此程式。 如需呼叫這些方法的詳細資訊，請參閱[重新命名專案](#renaming-items)。

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>將動態參數附加至複製-Item Cmdlet

有時候 `Copy-Item` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法來處理這些參數。 這個方法會在指定的路徑中抓取專案的參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Copy-Item` Cmdlet。

此提供者不會執行此方法。 不過，下列程式碼是[ContainerCmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>範例程式碼

如需完整的範例程式碼，請參閱[AccessDbProviderSample04 程式碼範例](./accessdbprovidersample04-code-sample.md)。

## <a name="building-the-windows-powershell-provider"></a>建立 Windows PowerShell 提供者

請參閱[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試。 請注意，下列範例輸出會使用虛構的 Access 資料庫。

1. 執行 `Get-ChildItem` Cmdlet，從 Access 資料庫的 Customers 資料表中取出子專案的清單。

   ```powershell
   Get-ChildItem mydb:customers
   ```

   下列輸出隨即出現。

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. 再次執行 `Get-ChildItem` Cmdlet，以取得資料表的資料。

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   下列輸出隨即出現。

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. 現在，使用 `Get-Item` Cmdlet 來抓取資料表中第0列的專案。

   ```powershell
   Get-Item mydb:\customers\0
   ```

   下列輸出隨即出現。

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. 重複使用 `Get-Item`，以取得資料列0中專案的資料。

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   下列輸出隨即出現。

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. 現在使用 `New-Item` Cmdlet，將資料列加入至現有的資料表。 `Path` 參數會指定資料列的完整路徑，而且必須指出大於資料表中現有資料列數目的資料列編號。 `Type` 參數表示 "row"，以指定要加入的專案類型。 最後，`Value` 參數會為數據列指定以逗號分隔的資料行值清單。

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. 確認新專案作業的正確性，如下所示。

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   下列輸出隨即出現。

   ```output
   ID        : 3
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
   ```

## <a name="see-also"></a>另請參閱

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[執行 Windows PowerShell 提供者專案](./creating-a-windows-powershell-item-provider.md)

[執行流覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)

[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)
