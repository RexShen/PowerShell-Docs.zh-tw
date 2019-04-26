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
ms.openlocfilehash: 33effed9a96cf1b9ee5f1a50b60a1937526db9d1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081898"
---
# <a name="creating-a-windows-powershell-container-provider"></a>建立 Windows PowerShell 容器提供者

本主題描述如何建立可在多層資料存放區的 Windows PowerShell 提供者。 針對此類型的資料存放區中，存放區的最上層包含根項目，以及每個後續的層級指節點的子項目。 藉由讓使用者能夠在這些子節點上運作，使用者可以階層方式透過資料存放區互動。

可以作用於多層級的資料存放區的提供者被指 Windows PowerShell 容器提供者。 不過，請注意一個容器 （沒有巢狀容器），在它的項目時，可以使用 Windows PowerShell 容器提供者。 如果沒有巢狀的容器，您必須實作的 Windows PowerShell 巡覽提供者。 如需有關如何實作 Windows PowerShell 巡覽提供者的詳細資訊，請參閱[建立 Windows PowerShell 巡覽提供者](./creating-a-windows-powershell-navigation-provider.md)。

> [!NOTE]
> 您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此提供者的原始程式檔 (AccessDBSampleProvider04.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。
>
> 如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

此處所述的 Windows PowerShell 容器提供者會定義為單一的容器，使用資料表和資料列做為容器的項目定義之資料庫的資料庫。

> [!CAUTION]
> 請注意，這項設計會假設的欄位有名稱識別碼的資料庫和欄位的型別是 LongInteger。

以下是本主題中的區段清單。 如果您不熟悉如何撰寫 Windows PowerShell 容器提供者，請閱讀這項資訊，它會出現的順序。 不過，如果您已熟悉撰寫 Windows PowerShell 容器提供者，請直接前往您所需要的資訊。

- [定義 Windows PowerShell 容器提供者類別](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [定義基底的功能](#defining-base-functionality)

- [正在擷取子系項目](#Retrieving-Child-Items)

- [附加到的動態參數`Get-ChildItem`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [擷取子系項目名稱](#Retrieving-Child-Item-Names)

- [附加到的動態參數`Get-ChildItem`Cmdlet （名稱）](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))

- [重新命名項目](#Renaming-Items)

- [附加到的動態參數`Rename-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [建立新的項目](#Creating-New-Items)

- [附加到的動態參數`New-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [移除項目](#Removing-Items)

- [附加到的動態參數`Remove-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [查詢的子項目](#Querying-for-Child-Items)

- [複製項目](#Copying-Items)

- [附加到的動態參數`Copy-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [程式碼範例](#Code-Sample)

- [建置 Windows PowerShell 提供者](#Building-the-Windows-PowerShell-Provider)

- [測試 Windows PowerShell 提供者](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a>定義 Windows PowerShell 容器提供者類別

Windows PowerShell 容器提供者必須定義衍生自.NET 類別[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基底類別。 以下是這一節所述的 Windows PowerShell 容器提供者的類別定義。

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

請注意，在此類別定義中， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。 第一個參數會指定使用 Windows powershell 提供者的使用者易記名稱。 第二個參數指定命令處理期間提供者會公開 Windows PowerShell 執行階段的 Windows PowerShell 特定功能。 此提供者，如有加入任何 Windows PowerShell 特定功能。

## <a name="defining-base-functionality"></a>定義基底的功能

中所述[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)，則[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別衍生自所提供的其他幾項類別不同的提供者的功能。 Windows PowerShell 容器提供者，因此，必須定義所有這些類別所提供的功能。

若要實作功能，說明如何加入工作階段特定的初始化資訊，以及用於釋放提供者所使用的資源，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者 （包括此處所述的提供者） 可以使用這項功能所提供的 Windows PowerShell 的預設實作。

若要存取資料存放區，提供者必須實作的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別。 如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

若要操作的資料存放區，例如開始、 設定和清除項目，項目的提供者必須實作所提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基底類別。 如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)。

## <a name="retrieving-child-items"></a>正在擷取子系項目

若要擷取的子系項目，Windows PowerShell 容器提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以支援來自呼叫`Get-ChildItem`cmdlet。 這個方法會從資料存放區擷取子系項目，並將其寫入到管線中，為物件。 如果`recurse`指令程式參數指定，則方法會擷取所有的子系，不論在何種層級。 如果`recurse`參數沒有指定，則方法會擷取單一層級的子系。

以下是實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)此提供者的方法。 請注意，這個方法在路徑表示存取資料庫，並從該資料表的資料列擷取子項目，如果路徑表示的資料表時，會擷取所有的資料庫資料表中的子項目。

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>有關實作 GetChildItems 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 此方法的實作應該列入任何形式的存取可能會使項目對使用者顯示的項目。 例如，如果使用者具有寫入權限透過 FileSystem 提供者 （由 Windows PowerShell 提供），但沒有讀取權限的檔案，檔案仍然存在和[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)傳回`true`。 您的實作可能需要檢查的父項目，以查看 是否可以列舉子系。

- 撰寫多個項目，當[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法可能需要一些時間。 您可以設計您的提供者將使用的項目寫入[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法，一次。 使用這項技術，將會在資料流中的使用者顯示的項目。

- 您實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)負責防止無限遞迴時有循環的連結，諸如此類的。 應該擲回適當終止的例外狀況，以反映這種情況。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>附加至 Get-childitem Cmdlet 的動態參數

有時候`Get-ChildItem`呼叫的 cmdlet [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)需要在執行階段動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法。 這個方法會擷取動態參數所指出的路徑處的項目，並傳回物件，此物件具有屬性與欄位類似於 cmdlet 類別屬性的剖析或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`Get-ChildItem`cmdlet。

此 Windows PowerShell 容器提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>擷取子系項目名稱

若要擷取子項目的名稱，Windows PowerShell 容器提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以支援來自呼叫`Get-ChildItem`cmdlet 時其`Name`指定參數。 這個方法會擷取在指定路徑或子系項目名稱的所有容器的子系項目名稱，如果`returnAllContainers`指定此 cmdlet 的參數。 子系名稱是分葉的部分路徑。 例如，路徑 c:\windows\system32\abc.dll 子名稱是"abc.dll 」。 目錄 c:\windows\system32 的子系名稱是"system32"。

以下是實作[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)此提供者的方法。 請注意此方法會擷取資料表名稱，是否指定的路徑表示的 Access 資料庫 （磁碟機） 和資料列號碼如果的路徑表示的資料表。

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>有關實作 GetChildNames 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

  > [!NOTE]
  > 此規則的例外狀況發生時`returnAllContainers`指定此 cmdlet 的參數。 在此情況下，此方法應該擷取任何子容器名稱，即使它不符合的值[System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter)， [System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)，或[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)屬性。

- 根據預設，會覆寫這個方法不應該擷取會在除非通常不對使用者顯示的物件名稱[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)指定屬性。 如果指定的路徑表示容器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。

- 您實作[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)負責防止無限遞迴時有循環的連結，諸如此類的。 應該擲回適當終止的例外狀況，以反映這種情況。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>將動態參數附加至 Get-childitem Cmdlet （名稱）

有時候`Get-ChildItem`指令程式 (使用`Name`參數) 需要在執行階段動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。 這個方法會擷取位於指定路徑的項目動態參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`Get-ChildItem`cmdlet。

此提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>重新命名項目

若要重新命名項目，Windows PowerShell 容器提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，以支援來自呼叫`Rename-Item`cmdlet。 這個方法會變更指定的路徑處的項目名稱提供的新名稱。 新的名稱必須一律是相對於父項目 （容器）。

此提供者不會覆寫[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法。 不過，以下是預設的實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>有關實作 RenameItem 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法是修改之名稱的項目，而不移動作業。 如果方法的實作應該寫入錯誤`newName`參數包含路徑分隔符號，或可能會導致要變更其父代位置的項目。

- 根據預設，這個方法的覆寫應該不重新命名物件，除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)指定屬性。 如果指定的路徑表示容器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。

- 您實作[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。 這個方法用來變更系統狀態，例如，重新命名檔案時，請確認執行作業。 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)傳送給使用者，變更納入考量，任何命令列設定或喜好設定變數中的 Windows PowerShell 執行階段資源的名稱決定應該要顯示的內容。

  若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 這個方法會傳送一則訊息確認訊息給使用者，以允許其他意見反應，說如果應該繼續執行作業。 提供者應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作為額外的檢查，如有潛在危險的系統修改。

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>將動態參數附加至 Rename-item Cmdlet

有時候`Rename-Item`cmdlet 需要在執行階段動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。 這個方法會擷取位於指定路徑的項目參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`Rename-Item`cmdlet。

此容器提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>建立新的項目

若要建立新的項目，容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以支援來自呼叫`New-Item`cmdlet。 這個方法會建立在位於指定路徑的資料項目。 `type` Cmdlet 參數包含新的項目定義提供者類型。 例如，FileSystem 提供者會使用`type`參數的值為"file"或"directory"。 `newItemValue`指令程式參數指定新的項目提供者特定值。

以下是實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)此提供者的方法。

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>有關實作 NewItem 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該執行傳入的字串不區分大小寫比較`type`參數。 它也應該允許至少模稜兩可的符合項目。 比方說，針對類型 「 檔案 」 和 「 目錄 」 中，只有第一個字母，才能釐清。 如果`type`參數會指出無法建立您的提供者，型別[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該重寫 ArgumentException 的訊息指出類型可以建立提供者。

- 針對`newItemValue`參數，請實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法會建議您接受最小值的字串。 它也應該接受所擷取物件的型別[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)相同路徑的方法。 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法也可以使用[System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo)方法，將轉換類型所需的類型。

- 您實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。 若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true， [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法有潛在危險的系統修改為額外的檢查。

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>附加至 New-item Cmdlet 的動態參數

有時候`New-Item`cmdlet 需要在執行階段動態指定的其他參數。 若要提供這些動態參數，容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。 這個方法會擷取位於指定路徑的項目參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`New-Item`cmdlet。

此提供者未實作這個方法。 不過，下列程式碼是這個方法的預設實作。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>移除項目

若要移除的項目，則 Windows PowerShell 提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以支援來自呼叫`Remove-Item`cmdlet。 這個方法會刪除項目從資料存放區，在指定的路徑。 如果`recurse`的參數`Remove-Item`cmdlet 設定為`true`，則方法會移除所有的子項目，不論其層級。 如果參數設定為`false`，則方法會移除單一項目在指定的路徑。

此提供者不支援項目移除。 不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>有關實作 RemoveItem 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，會覆寫這個方法不應該移除物件除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 true。 如果指定的路徑表示容器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。

- 您實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)負責防止無限遞迴時有循環的連結，諸如此類的。 應該擲回適當終止的例外狀況，以反映這種情況。

- 您實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。 若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法有潛在危險的系統修改為額外的檢查。

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>將動態參數附加至 Remove-item Cmdlet

有時候`Remove-Item`cmdlet 需要在執行階段動態指定的其他參數。 若要提供這些動態參數，容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法來處理這些參數。 這個方法會擷取位於指定路徑的項目動態參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`Remove-Item`cmdlet。

此容器提供者未實作這個方法。 不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>查詢的子項目

若要查看子項目有指定的路徑，Windows PowerShell 容器提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。 這個方法會傳回`true`如果項目子系，和`false`否則。 為 null 或空白的路徑，此方法會考慮任何資料存放區中為子系的項目並傳回`true`。

以下是 覆寫[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。 如果有兩個以上的路徑部分 ChunkPath 協助程式方法所建立的則方法會傳回`false`，因為只有一個資料庫的容器和資料表容器所定義。 如需有關這個 helper 方法的詳細資訊，請參閱 ChunkPath 方法中會討論[建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)。

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>有關實作 HasChildItems 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- 如果容器提供者會公開包含有趣的掛接點，實作的根[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法應傳回`true`為 null 或空字串傳遞時的路徑。

## <a name="copying-items"></a>複製項目

若要複製的項目，容器提供者必須實作[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以支援來自呼叫`Copy-Item`cmdlet。 這個方法會從指定的位置複製資料項目`path`參數所指示位置 cmdlet`copyPath`參數。 如果`recurse`參數指定，則方法會複製所有的子容器。 如果未指定參數，則方法會複製項目中的單一層級。

此提供者未實作這個方法。 不過，下列程式碼是預設的實作[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>有關實作 CopyItem 的注意事項

在下列情況可能適用於您實作[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。 若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。

- 根據預設，會覆寫這個方法不應該複製物件現有的物件除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 例如，FileSystem 提供者不會複製 c:\temp\abc.txt 透過現有 c:\abc.txt 檔案除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。 如果在指定的路徑`copyPath`參數存在，並指出容器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。 在此情況下， [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)應該複製所指定的項目`path`所指定的參數，以容器`copyPath`參數做為子系。

- 您實作[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)負責防止無限遞迴時有循環的連結，諸如此類的。 應該擲回適當終止的例外狀況，以反映這種情況。

- 您實作[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。 若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true， [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法有潛在危險的系統修改為額外的檢查。 如需有關呼叫這些方法的詳細資訊，請參閱 <<c0> [ 重新命名的項目](#Renaming-Items)。

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>將動態參數附加至 Copy-item Cmdlet

有時候`Copy-Item`cmdlet 需要在執行階段動態指定的其他參數。 若要提供這些動態參數，Windows PowerShell 容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)處理這些方法參數。 這個方法會擷取位於指定路徑的項目參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。 Windows PowerShell 執行階段會使用傳回的物件加入至參數`Copy-Item`cmdlet。

此提供者未實作這個方法。 不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>程式碼範例

完整的範例程式碼，請參閱[AccessDbProviderSample04 程式碼範例](./accessdbprovidersample04-code-sample.md)。

## <a name="building-the-windows-powershell-provider"></a>建置 Windows PowerShell 提供者

請參閱[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 時，您可以藉由在命令列上執行受支援的 cmdlet 來進行測試。 請注意，下列範例輸出會使用虛構的 Access 資料庫。

1. 執行`Get-ChildItem`cmdlet 來從 Access 資料庫中的 [客戶] 資料表中擷取的子系項目清單。

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

2. 執行`Get-ChildItem`cmdlet 一次來擷取資料表的資料。

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

3. 現在使用`Get-Item`cmdlet 來擷取資料表中的資料列 0 的項目。

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

4. 重複使用`Get-Item`擷取的資料列 0 中的項目。

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

5. 現在使用`New-Item`cmdlet 將資料列新增至現有的資料表。 `Path`參數指定的資料列的完整路徑，並必須指出資料列數目大於現有的資料表中的資料列數目。 `Type`參數會指示 「 資料列 」 來指定要加入項目該類型。 最後，`Value`參數指定的資料列的資料行值的逗號分隔清單。

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. 請確認新的項目作業的正確性，如下所示。

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

[實作項目 Windows PowerShell 提供者](./creating-a-windows-powershell-item-provider.md)

[實作瀏覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)