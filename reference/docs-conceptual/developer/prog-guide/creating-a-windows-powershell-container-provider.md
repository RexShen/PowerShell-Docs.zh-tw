---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 Windows PowerShell 容器提供者
description: 建立 Windows PowerShell 容器提供者
ms.openlocfilehash: 999bd69e3c16bfc0a74519986654ec15bbc0da6d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645367"
---
# <a name="creating-a-windows-powershell-container-provider"></a>建立 Windows PowerShell 容器提供者

本主題說明如何建立可在多層式資料存放區上運作的 Windows PowerShell 提供者。 對於這種類型的資料存放區，存放區的最上層包含根專案，而且每個後續層級稱為子專案的節點。 藉由允許使用者在這些子節點上工作，使用者就可以透過資料存放區以階層方式進行互動。

可在多層級資料存放區上運作的提供者稱為 Windows PowerShell 的容器提供者。 不過，請注意，只有當有一個容器 () 的專案中沒有任何嵌套容器時，才可以使用 Windows PowerShell 的容器提供者。 如果有嵌套的容器，則您必須執行 Windows PowerShell 的流覽提供者。 如需有關如何執行 Windows PowerShell 流覽提供者的詳細資訊，請參閱 [建立 Windows PowerShell 流覽提供者](./creating-a-windows-powershell-navigation-provider.md)。

> [!NOTE]
> 您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此提供者的 c # 原始程式檔 (AccessDBSampleProvider04.cs) 。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。 如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

此處所述的 Windows PowerShell 容器提供者將資料庫定義為其單一容器，並將資料庫的資料表和資料列定義為容器的專案。

> [!CAUTION]
> 請注意，此設計假設有一個具有名稱識別碼之欄位的資料庫，以及欄位的類型為 LongInteger。

## <a name="defining-a-windows-powershell-container-provider-class"></a>定義 Windows PowerShell 的容器提供者類別

Windows PowerShell 的容器提供者必須定義一個衍生自 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 基類的 .net 類別。 以下是本節所述 Windows PowerShell 容器提供者的類別定義。

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
public class AccessDBProvider : ContainerCmdletProvider
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="34-35":::

請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 屬性包含兩個參數。 第一個參數會指定 Windows PowerShell 所使用之提供者的使用者易記名稱。 第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。 對於此提供者，不會新增 Windows PowerShell 特定功能。

## <a name="defining-base-functionality"></a>定義基底功能

如 [設計您的 Windows PowerShell 提供](./designing-your-windows-powershell-provider.md)者所述， [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別衍生自數個提供不同提供者功能的其他類別。 因此，Windows PowerShell 的容器提供者需要定義這些類別所提供的所有功能。

若要執行新增會話特定初始化資訊，以及釋出提供者所使用之資源的功能，請參閱 [建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。
不過，大部分的提供者 (包括此處所述的提供者) 可以使用 Windows PowerShell 所提供的這項功能的預設執行。

若要取得資料存放區的存取權，提供者必須執行 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 基類的方法。 如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 基類所提供的方法。 如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。

## <a name="retrieving-child-items"></a>正在抓取子專案

若要取出子專案，Windows PowerShell 的容器提供者必須覆寫 [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法，以支援來自 Cmdlet 的呼叫 `Get-ChildItem` 。 這個方法會從資料存放區中抓取子專案，並將它們以物件的形式寫入管線。 如果 `recurse` 指定了 Cmdlet 的參數，此方法就會抓取所有子系，而不論其所在層級為何。 如果 `recurse` 未指定參數，方法只會抓取單一的子系層級。

以下是此提供者的 [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行方式。 請注意，當路徑指出 Access 資料庫時，這個方法會抓取所有資料庫資料表中的子專案，並在路徑指出資料表時，從該資料表的資料列中抓取子專案。

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="311-362":::

#### <a name="things-to-remember-about-implementing-getchilditems"></a>執行 GetChildItems 的注意事項

下列情況可能適用于您的 [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行：

- 定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- 此方法的執行應該將任何形式的存取權考慮到可能讓使用者看見專案的專案。 例如，如果使用者透過檔案系統提供者來寫入檔案的寫入權限 (由 Windows PowerShell) 提供，但無法讀取存取權，則該檔案仍然存在，而且 [system.management.automation.provider.itemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 會傳回 `true` 。 您的執行可能需要檢查父項目，才能查看是否可以列舉子系。

- 撰寫多個專案時， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法可能需要一些時間。 您可以設計提供者，一次使用一個 [Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 方法來撰寫專案。 使用這項技術會向使用者呈現資料流程中的專案。

- 當有迴圈連結時，您的 ContainerCmdletprovider 會負責防止無限遞迴，例如，您的 [系統管理](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 。 應擲回適當的終止例外狀況，以反映這類情況。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>將動態參數附加至 Get-ChildItem Cmdlet

有時候， `Get-ChildItem` 呼叫 ContainerCmdletprovider 的 Cmdlet 會需要在執行時間動態指定的其他參數（ [Provider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ）。 若要提供這些動態參數，Windows PowerShell 的容器提供者必須執行 [ContainerCmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 方法。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Get-ChildItem` Cmdlet。

此 Windows PowerShell 容器提供者不會執行此方法。 但是，下列程式碼是此方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>正在抓取子專案名稱

若要抓取子專案的名稱，Windows PowerShell 的容器提供者必須覆寫 [ContainerCmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 方法，以便 `Get-ChildItem` 在指定參數時支援來自 Cmdlet 的呼叫 `Name` 。 如果指定了 Cmdlet 的參數，這個方法會抓取所有容器之指定路徑或子專案名稱的子專案名稱 `returnAllContainers` 。 子系名稱是路徑的分葉部分。 例如，路徑 c:\windows\system32\abc.dll 的子名稱為 "abc.dll"。 目錄 c:\windows\system32 的子名稱為 "system32"。

以下是此提供者的 [ContainerCmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 方法的執行方式。 請注意，如果指定的路徑指出 Access 資料庫 (磁片磁碟機) 和資料列編號（如果路徑指出資料表），此方法就會抓取資料表名稱。

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="369-411":::

#### <a name="things-to-remember-about-implementing-getchildnames"></a>執行 GetChildNames 的注意事項

下列情況可能適用于您的 [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行：

- 定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

  > [!NOTE]
  > 指定 Cmdlet 的參數時，就會發生此規則的例外狀況 `returnAllContainers` 。 在此情況下，此方法應該會取出容器的任何子系名稱，即使它不符合[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter)的值也是一樣。 [Cmdletprovider.. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)或[Cmdletprovider..... Exclude * properties..](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)

- 根據預設，除非指定 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性，否則這個方法的覆寫不應抓取使用者通常會隱藏的物件名稱。 如果指定的路徑指出容器，則不需要 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。」

- 當有迴圈連結時，您的 ContainerCmdletprovider 會負責防止無限遞迴，例如，您的 [系統管理](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 。 應擲回適當的終止例外狀況，以反映這類情況。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>將動態參數附加至 Get-ChildItem Cmdlet (名稱) 

有時 `Get-ChildItem` Cmdlet (與 `Name` 參數) 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 的容器提供者必須執行 [ContainerCmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 方法。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件的屬性和欄位具有類似 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Get-ChildItem` Cmdlet。

此提供者不會執行此方法。 但是，下列程式碼是此方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>重新命名專案

若要重新命名專案，Windows PowerShell 的容器提供者必須覆寫 [ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 方法，以支援來自 Cmdlet 的呼叫 `Rename-Item` 。 這個方法會將指定路徑的專案名稱變更為提供的新名稱。 新名稱必須一律相對於父代 (container) 的專案。

此提供者不會覆寫 [ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 方法。 但是，下列是預設的執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>執行 RenameItem 的注意事項

下列情況可能適用于您的 [ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)的執行：

- 定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- [ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法僅適用于修改專案的名稱，而不是用於移動作業的專案。
  如果 `newName` 參數包含路徑分隔符號，或可能導致專案變更其父位置，則您的方法的執行應該會寫入錯誤。

- 根據預設，除非指定 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性，否則這個方法的覆寫不應重新命名物件。 如果指定的路徑指出容器，則不需要 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。」

- 您的 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。 當對系統狀態進行變更（例如重新命名檔案）時，會使用這個方法來確認作業的執行。
  [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會傳送要變更給使用者的資源名稱，且 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入考慮，以決定應顯示的內容。

  呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) `true` 會傳回， [ContainerCmdletprovider.. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 方法應該呼叫 [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ，以呼叫 system.object.. * 方法來呼叫. 管理方法。 這個方法會將確認訊息傳送給使用者，以允許額外的意見反應來指出作業是否應該繼續。 提供者應該呼叫 [Cmdletprovider ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 做為額外的檢查，以進行可能有危險的系統修改。

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>將動態參數附加至 Rename-Item Cmdlet

有時 `Rename-Item` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 容器提供者必須執行 [ContainerCmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 方法。 這個方法會在指定的路徑上抓取專案的參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Rename-Item` Cmdlet。

此容器提供者不會執行此方法。 但是，下列程式碼是此方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>建立新專案

若要建立新的專案，容器提供者必須執行 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法，以支援來自 Cmdlet 的呼叫 `New-Item` 。 這個方法會建立位於指定路徑的資料項目。 `type`Cmdlet 的參數包含新專案的提供者定義型別。 例如，FileSystem 提供者會使用 `type` 值為 "file" 或 "directory" 的參數。 `newItemValue`Cmdlet 的參數會指定新專案的提供者特定值。

以下是此提供者的 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法的執行方式。

```csharp
protected override void NewItem( string path, string type, object newItemValue )
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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="939-955":::

#### <a name="things-to-remember-about-implementing-newitem"></a>執行 NewItem 的注意事項

下列情況可能適用于您的 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行：

- [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該針對參數中所傳遞的字串，執行不區分大小寫的比較 `type` 。
  它也應該允許最少不明確的相符專案。 例如，針對 "file" 和 "directory" 類型，只需要第一個字母來區分。 如果 `type` 參數指出您的提供者無法建立的類型，則 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法應該寫入 ArgumentException，並顯示訊息，指出提供者可建立的類型。

- 若為 `newItemValue` 參數，建議您將 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法的實作為最小接受字串。 此外，它也應該接受針對相同路徑， [system.management.automation.provider.itemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 方法所抓取的物件類型。 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法可以使用[languageprimitives.physicalequality. Convertto *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo)方法，將型別轉換成所需的型別（type）。

- 您的 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。 在呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會傳回 true，則 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法應該呼叫 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ，以做為可能有危險的系統修改的額外檢查，以進行額外的檢查，以進行檢查。

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>將動態參數附加至 New-Item Cmdlet

有時 `New-Item` Cmdlet 需要在執行時間動態指定的其他參數。 若要提供這些動態參數，容器提供者必須執行 [ContainerCmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 方法。 這個方法會在指定的路徑上抓取專案的參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `New-Item` Cmdlet。

此提供者不會執行此方法。 但是，下列程式碼是此方法的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>移除專案

若要移除專案，Windows PowerShell 提供者必須覆寫 [ContainerCmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 方法，以支援來自 Cmdlet 的呼叫 `Remove-Item` 。 這個方法會從指定路徑的資料存放區中刪除專案。 如果 `recurse` Cmdlet 的參數 `Remove-Item` 設定為 `true` ，則方法會移除所有子專案，而不論其層級為何。 如果參數設定為 `false` ，方法只會移除指定路徑上的單一專案。

此提供者不支援移除專案。 但是，下列程式碼是 [ContainerCmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>執行 RemoveItem 的注意事項

下列情況可能適用于您的 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行：

- 定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- 根據預設，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為 true，否則這個方法的覆寫不應移除物件。 如果指定的路徑指出容器，則不需要 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。」

- 當有迴圈連結時，您的 ContainerCmdletprovider 會負責防止無限遞迴，例如，您的 [系統管理](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 。 應擲回適當的終止例外狀況，以反映這類情況。

- 您的 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。 在呼叫 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 之後，ShouldProcess `true` 會傳回， [ContainerCmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 方法應該呼叫 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 來做額外檢查，以瞭解是否有潛在危險的系統修改，並將其視為額外的檢查，以進行檢查。

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>將動態參數附加至 Remove-Item Cmdlet

有時 `Remove-Item` Cmdlet 需要在執行時間動態指定的其他參數。 為了提供這些動態參數，容器提供者必須執行 [ContainerCmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 方法來處理這些參數。 這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件的屬性和欄位具有類似 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件的剖析屬性。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Remove-Item` Cmdlet。

此容器提供者不會執行此方法。 但是，下列程式碼是 [ContainerCmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>查詢子專案

若要檢查子專案是否存在於指定的路徑，Windows PowerShell 的容器提供者必須覆寫 [ContainerCmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 方法。 如果專案有子系，則這個方法會傳回 `true` ，否則會傳回 `false` 。 如果是 null 或空的路徑，方法會將資料存放區中的任何專案視為子系，並傳回 `true` 。

以下是 [ContainerCmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 方法的覆寫方法。 如果 ChunkPath helper 方法建立了兩個以上的路徑部分，則方法會傳回 `false` ，因為只會定義資料庫容器和資料表容器。 如需此 helper 方法的詳細資訊，請參閱 [建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)中所討論的 ChunkPath 方法。

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="1094-1097":::

#### <a name="things-to-remember-about-implementing-haschilditems"></a>執行 HasChildItems 的注意事項

下列情況可能適用于您的 [ContainerCmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)的執行：

- 如果容器提供者公開包含有趣掛接點的根目錄，則在為路徑傳入 null 或空字串時，應會傳回[ContainerCmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法的執行。 `true`

## <a name="copying-items"></a>複製專案

若要複製專案，容器提供者必須執行 [ContainerCmdletProvider CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 方法，以支援來自 Cmdlet 的呼叫 `Copy-Item` 。 這個方法會從 Cmdlet 的參數所指定的位置，將資料項目複製 `path` 到參數所指示的位置 `copyPath` 。 如果 `recurse` 指定了參數，則方法會複製所有子容器。 如果未指定參數，方法只會複製單一層級的專案。

此提供者不會執行此方法。 但是，下列程式碼是 [ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>執行 CopyItem 的注意事項

下列情況可能適用于您的 [ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)的執行：

- 定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。 在這些情況下， [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」 若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include * properties. Include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 * 屬性）。

- 根據預設，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則此方法的覆寫不應將物件複製到現有的物件 `true` 。 例如，FileSystem 提供者不會將 c:\temp\abc.txt 複製到現有的 c:\abc.txt 檔案，除非 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為 `true` 。 如果在參數中指定的路徑 `copyPath` 存在且指出容器，則不需要 [Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。 在此情況下， [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 會將參數所指示的專案複製 `path` 到參數所指示的容器 `copyPath` 做為子系。

- 當有迴圈連結時，您的 ContainerCmdletProvider 會負責防止無限遞迴，例如，您的 [系統管理](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 。 應擲回適當的終止例外狀況，以反映這類情況。

- 您的 [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。 在呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會傳回 true，則 [ContainerCmdletProvider.. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 方法應該呼叫 [方法，](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 以做為可能有危險的系統修改的額外檢查，以做額外的檢查的檢查。 如需呼叫這些方法的詳細資訊，請參閱 [重新命名專案](#renaming-items)。

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>將動態參數附加至 Copy-Item Cmdlet

有時 `Copy-Item` Cmdlet 需要在執行時間動態指定的其他參數。 為了提供這些動態參數，Windows PowerShell 的容器提供者必須執行 [ContainerCmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 方法來處理這些參數。 這個方法會在指定的路徑上抓取專案的參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。 Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Copy-Item` Cmdlet。

此提供者不會執行此方法。 但是，下列程式碼是 [ContainerCmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)的預設執行。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>程式碼範例

如需完整的範例程式碼，請參閱 [AccessDbProviderSample04 程式碼範例](./accessdbprovidersample04-code-sample.md)。

## <a name="building-the-windows-powershell-provider"></a>建立 Windows PowerShell 提供者

瞭解 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試。 請注意，下列範例輸出會使用虛構的 Access 資料庫。

1. 執行 `Get-ChildItem` Cmdlet，從 Access 資料庫的 Customers 資料表中取出子專案清單。

   ```powershell
   Get-ChildItem mydb:customers
   ```

   即會出現下列輸出。

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

2. 再次執行 `Get-ChildItem` Cmdlet 以取出資料表的資料。

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   即會出現下列輸出。

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. 現在，使用 `Get-Item` Cmdlet 取出資料表中第0列的專案。

   ```powershell
   Get-Item mydb:\customers\0
   ```

   即會出現下列輸出。

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. 重複使用 `Get-Item` 以取得資料列0中專案的資料。

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   即會出現下列輸出。

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

5. 現在，使用指令 `New-Item` 程式將資料列新增至現有的資料表。 `Path`參數指定資料列的完整路徑，而且必須指出大於資料表中現有資料列數目的資料列編號。 `Type`參數表示 "row"，以指定要加入的專案類型。
   最後， `Value` 參數會指定資料列的資料行值清單（以逗號分隔）。

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. 確認新專案作業的正確性，如下所示。

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   即會出現下列輸出。

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

[設計 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[執行專案 Windows PowerShell 提供者](./creating-a-windows-powershell-item-provider.md)

[執行導覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)
