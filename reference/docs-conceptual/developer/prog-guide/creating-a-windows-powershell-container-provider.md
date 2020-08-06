---
title: 建立 Windows PowerShell 容器提供者
ms.date: 09/13/2016
ms.openlocfilehash: a5bcba425909eb98c010a1ea010cb02b995771f3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787201"
---
# <a name="creating-a-windows-powershell-container-provider"></a><span data-ttu-id="9e9ba-102">建立 Windows PowerShell 容器提供者</span><span class="sxs-lookup"><span data-stu-id="9e9ba-102">Creating a Windows PowerShell Container Provider</span></span>

<span data-ttu-id="9e9ba-103">本主題說明如何建立可在多層式資料存放區上使用的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-103">This topic describes how to create a Windows PowerShell provider that can work on multi-layer data stores.</span></span> <span data-ttu-id="9e9ba-104">對於這種類型的資料存放區，存放區的最上層包含根專案，而每個後續層級稱為子專案的節點。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-104">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="9e9ba-105">藉由允許使用者在這些子節點上工作，使用者可以透過資料存放區以階層方式進行互動。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-105">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

<span data-ttu-id="9e9ba-106">可在多層級資料存放區上工作的提供者稱為 Windows PowerShell 容器提供者。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-106">Providers that can work on multi-level data stores are referred to as Windows PowerShell container providers.</span></span> <span data-ttu-id="9e9ba-107">不過，請注意，只有在有一個容器 (沒有任何嵌套容器) 具有專案時，才可以使用 Windows PowerShell 容器提供者。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-107">However, be aware that a Windows PowerShell container provider can be used only when there is one container (no nested containers) with items in it.</span></span> <span data-ttu-id="9e9ba-108">如果有嵌套的容器，則您必須執行 Windows PowerShell 流覽提供者。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-108">If there are nested containers, then you must implement a Windows PowerShell navigation provider.</span></span> <span data-ttu-id="9e9ba-109">如需有關執行 Windows PowerShell 流覽提供者的詳細資訊，請參閱[建立 Windows Powershell 流覽提供者](./creating-a-windows-powershell-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-109">For more information about implementing Windows PowerShell navigation provider, see [Creating a Windows PowerShell Navigation Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9e9ba-110">您可以使用適用于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的 c # 原始程式檔 (AccessDBSampleProvider04.cs) 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-110">You can download the C# source file (AccessDBSampleProvider04.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9e9ba-111">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-111">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="9e9ba-112">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-112">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="9e9ba-113">如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-113">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="9e9ba-114">這裡所述的 Windows PowerShell 容器提供者會將資料庫定義為其單一容器，並將資料庫的資料表和資料列定義為容器的專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-114">The Windows PowerShell container provider described here defines the database as its single container, with the tables and rows of the database defined as items of the container.</span></span>

> [!CAUTION]
> <span data-ttu-id="9e9ba-115">請注意，這項設計假設有一個具有名稱識別碼之欄位的資料庫，而且欄位的類型是 LongInteger。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-115">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

## <a name="defining-a-windows-powershell-container-provider-class"></a><span data-ttu-id="9e9ba-116">定義 Windows PowerShell 容器提供者類別</span><span class="sxs-lookup"><span data-stu-id="9e9ba-116">Defining a Windows PowerShell Container Provider Class</span></span>

<span data-ttu-id="9e9ba-117">Windows PowerShell 容器提供者必須定義一個衍生自[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基類的 .net 類別（class）。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-117">A Windows PowerShell container provider must define a .NET class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="9e9ba-118">以下是本節所述 Windows PowerShell 容器提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-118">Here is the class definition for the Windows PowerShell container provider described in this section.</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
public class AccessDBProvider : ContainerCmdletProvider
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="34-35":::

<span data-ttu-id="9e9ba-119">請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-119">Notice that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="9e9ba-120">第一個參數會為 Windows PowerShell 所使用的提供者指定易記的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-120">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="9e9ba-121">第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-121">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="9e9ba-122">對於此提供者，不會新增任何 Windows PowerShell 特有的功能。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-122">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="9e9ba-123">定義基本功能</span><span class="sxs-lookup"><span data-stu-id="9e9ba-123">Defining Base Functionality</span></span>

<span data-ttu-id="9e9ba-124">如[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)中所述， [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別衍生自數個提供不同提供者功能的其他類別。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-124">As described in [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="9e9ba-125">因此，Windows PowerShell 容器提供者必須定義這些類別所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-125">A Windows PowerShell container provider, therefore, needs to define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="9e9ba-126">若要執行功能來新增會話特定的初始化資訊，以及釋放提供者所使用的資源，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-126">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="9e9ba-127">不過，大部分的提供者 (包括這裡所述的提供者) 可以使用 Windows PowerShell 所提供的這項功能的預設執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-127">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="9e9ba-128">若要取得資料存放區的存取權，提供者必須執行[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-128">To get access to the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="9e9ba-129">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-129">For more information about implementing these methods, see [Creating an Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="9e9ba-130">若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-130">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="9e9ba-131">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-131">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

## <a name="retrieving-child-items"></a><span data-ttu-id="9e9ba-132">正在抓取子專案</span><span class="sxs-lookup"><span data-stu-id="9e9ba-132">Retrieving Child Items</span></span>

<span data-ttu-id="9e9ba-133">若要取得子專案，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以支援來自 Cmdlet 的呼叫 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-133">To retrieve a child item, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to support calls from the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="9e9ba-134">這個方法會從資料存放區抓取子專案，並將它們以物件的形式寫入管線。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-134">This method retrieves child items from the data store and writes them to the pipeline as objects.</span></span> <span data-ttu-id="9e9ba-135">如果 `recurse` 指定了 Cmdlet 的參數，方法會抓取所有子系，而不論它們位於哪一層級。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-135">If the `recurse` parameter of the cmdlet is specified, the method retrieves all children regardless of what level they are at.</span></span> <span data-ttu-id="9e9ba-136">如果 `recurse` 未指定參數，方法只會抓取單一層級的子系。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-136">If the `recurse` parameter is not specified, the method retrieves only a single level of children.</span></span>

<span data-ttu-id="9e9ba-137">以下是此提供者的[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-137">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method for this provider.</span></span> <span data-ttu-id="9e9ba-138">請注意，此方法會在路徑指出 Access 資料庫時，抓取所有資料庫資料表中的子專案，並在路徑表示資料表時，從該資料表的資料列抓取子專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-138">Notice that this method retrieves the child items in all database tables when the path indicates the Access database, and retrieves the child items from the rows of that table if the path indicates a data table.</span></span>

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

#### <a name="things-to-remember-about-implementing-getchilditems"></a><span data-ttu-id="9e9ba-139">執行 GetChildItems 的相關事項</span><span class="sxs-lookup"><span data-stu-id="9e9ba-139">Things to Remember About Implementing GetChildItems</span></span>

<span data-ttu-id="9e9ba-140">下列條件可能適用于您的[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="9e9ba-140">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span></span>

- <span data-ttu-id="9e9ba-141">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-141">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="9e9ba-142">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-142">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="9e9ba-143">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-143">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="9e9ba-144">此方法的實體系應該考慮到可能會讓使用者看見專案的任何形式的存取權。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-144">The implementation of this method should take into account any form of access to the item that might make the item visible to the user.</span></span> <span data-ttu-id="9e9ba-145">例如，如果使用者透過 FileSystem 提供者對檔案的寫入權限 (由 Windows PowerShell 提供) 但不是讀取權限，則該檔案仍然存在，而且[ItemCmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)會傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-145">For example, if a user has write access to a file through the FileSystem provider (supplied by Windows PowerShell), but not read access, the file still exists and [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) returns `true`.</span></span> <span data-ttu-id="9e9ba-146">您的執行可能需要檢查父專案，以查看是否可以列舉子系。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-146">Your implementation might require the checking of a parent item to see if the child can be enumerated.</span></span>

- <span data-ttu-id="9e9ba-147">寫入多個專案時， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-147">When writing multiple items, the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method can take some time.</span></span> <span data-ttu-id="9e9ba-148">您可以設計提供者，以一次使用[Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法來撰寫專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-148">You can design your provider to write the items using the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method one at a time.</span></span> <span data-ttu-id="9e9ba-149">使用這項技術會向使用者呈現串流中的專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-149">Using this technique will present the items to the user in a stream.</span></span>

- <span data-ttu-id="9e9ba-150">您的[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)會負責防止無限遞迴（如有迴圈連結），以及 like。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-150">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="9e9ba-151">應擲回適當的終止例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-151">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a><span data-ttu-id="9e9ba-152">將動態參數附加至 Get-childitem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9e9ba-152">Attaching Dynamic Parameters to the Get-ChildItem Cmdlet</span></span>

<span data-ttu-id="9e9ba-153">有時候 `Get-ChildItem` 呼叫[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的 Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-153">Sometimes the `Get-ChildItem` cmdlet that calls [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="9e9ba-154">若要提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Getchilditemsdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-154">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) method.</span></span> <span data-ttu-id="9e9ba-155">這個方法會在指定的路徑上抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-155">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="9e9ba-156">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-156">The Windows PowerShell runtime uses the returned object to add the parameters to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="9e9ba-157">這個 Windows PowerShell 容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-157">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="9e9ba-158">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-158">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a><span data-ttu-id="9e9ba-159">正在抓取子專案名稱</span><span class="sxs-lookup"><span data-stu-id="9e9ba-159">Retrieving Child Item Names</span></span>

<span data-ttu-id="9e9ba-160">若要取得子專案的名稱，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以支援 `Get-ChildItem` 在指定其參數時從 Cmdlet 呼叫 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-160">To retrieve the names of child items, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to support calls from the `Get-ChildItem` cmdlet when its `Name` parameter is specified.</span></span> <span data-ttu-id="9e9ba-161">如果指定 Cmdlet 的參數，這個方法會抓取所有容器之指定路徑或子專案名稱的子專案名稱 `returnAllContainers` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-161">This method retrieves the names of the child items for the specified path or child item names for all containers if the `returnAllContainers` parameter of the cmdlet is specified.</span></span> <span data-ttu-id="9e9ba-162">子名稱是路徑的分葉部分。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-162">A child name is the leaf portion of a path.</span></span> <span data-ttu-id="9e9ba-163">例如，路徑 c:\windows\system32\abc.dll 的子名稱是 "abc.dll"。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-163">For example, the child name for the path c:\windows\system32\abc.dll is "abc.dll".</span></span> <span data-ttu-id="9e9ba-164">目錄 c:\windows\system32 的子名稱是 "system32"。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-164">The child name for the directory c:\windows\system32 is "system32".</span></span>

<span data-ttu-id="9e9ba-165">以下是此提供者的[ContainerCmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法的執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-165">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method for this provider.</span></span> <span data-ttu-id="9e9ba-166">請注意，如果指定的路徑指出 Access 資料庫 (磁片磁碟機) 和資料列編號（如果路徑指出資料表），方法會抓取資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-166">Notice that the method retrieves table names if the specified path indicates the Access database (drive) and row numbers if the path indicates a table.</span></span>

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

#### <a name="things-to-remember-about-implementing-getchildnames"></a><span data-ttu-id="9e9ba-167">執行 GetChildNames 的相關事項</span><span class="sxs-lookup"><span data-stu-id="9e9ba-167">Things to Remember About Implementing GetChildNames</span></span>

<span data-ttu-id="9e9ba-168">下列條件可能適用于您的[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="9e9ba-168">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span></span>

- <span data-ttu-id="9e9ba-169">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-169">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="9e9ba-170">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-170">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="9e9ba-171">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-171">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9e9ba-172">當指定 Cmdlet 的參數時，就會發生此規則的例外狀況 `returnAllContainers` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-172">An exception to this rule occurs when the `returnAllContainers` parameter of the cmdlet is specified.</span></span> <span data-ttu-id="9e9ba-173">在這種情況下，方法應該會抓取容器的任何子系名稱，即使它不符合[Cmdletprovider. Filter \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter)、 [Cmdletprovider.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)Cmdletprovider \* 的值，也不會包含 \*，或[。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)屬性（property）的值。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-173">In this case, the method should retrieve any child name for a container, even if it does not match the values of the [System.Management.Automation.Provider.Cmdletprovider.Filter\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), or [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) properties.</span></span>

- <span data-ttu-id="9e9ba-174">根據預設，除非指定了[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ，否則此方法的覆寫不應抓取使用者通常會隱藏的物件名稱，。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-174">By default, overrides of this method should not retrieve names of objects that are generally hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is specified.</span></span> <span data-ttu-id="9e9ba-175">如果指定的路徑指出容器，則不需要[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。」</span><span class="sxs-lookup"><span data-stu-id="9e9ba-175">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="9e9ba-176">您的[ContainerCmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)會負責防止無限遞迴（如有迴圈連結），以及 like。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-176">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="9e9ba-177">應擲回適當的終止例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-177">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a><span data-ttu-id="9e9ba-178">將動態參數附加至 Get-childitem Cmdlet (名稱) </span><span class="sxs-lookup"><span data-stu-id="9e9ba-178">Attaching Dynamic Parameters to the Get-ChildItem Cmdlet (Name)</span></span>

<span data-ttu-id="9e9ba-179">有時候， `Get-ChildItem` Cmdlet `Name` 會使用參數 () 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-179">Sometimes the `Get-ChildItem` cmdlet (with the `Name` parameter) requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="9e9ba-180">若要提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Getchildnamesdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-180">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) method.</span></span> <span data-ttu-id="9e9ba-181">這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-181">This method retrieves the dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="9e9ba-182">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-182">The Windows PowerShell runtime uses the returned object to add the parameters to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="9e9ba-183">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-183">This provider does not implement this method.</span></span> <span data-ttu-id="9e9ba-184">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-184">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a><span data-ttu-id="9e9ba-185">重新命名專案</span><span class="sxs-lookup"><span data-stu-id="9e9ba-185">Renaming Items</span></span>

<span data-ttu-id="9e9ba-186">若要重新命名專案，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，以支援來自 Cmdlet 的呼叫 `Rename-Item` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-186">To rename an item, a Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method to support calls from the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="9e9ba-187">這個方法會將指定路徑的專案名稱變更為提供的新名稱。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-187">This method changes the name of the item at the specified path to the new name provided.</span></span> <span data-ttu-id="9e9ba-188">新名稱必須一律相對於父專案 (容器) 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-188">The new name must always be relative to the parent item (container).</span></span>

<span data-ttu-id="9e9ba-189">此提供者不會覆寫[ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-189">This provider does not override the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method.</span></span> <span data-ttu-id="9e9ba-190">不過，下列是預設的執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-190">However, the following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a><span data-ttu-id="9e9ba-191">執行 RenameItem 的相關事項</span><span class="sxs-lookup"><span data-stu-id="9e9ba-191">Things to Remember About Implementing RenameItem</span></span>

<span data-ttu-id="9e9ba-192">下列條件可能適用于您的[ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="9e9ba-192">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):</span></span>

- <span data-ttu-id="9e9ba-193">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-193">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="9e9ba-194">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-194">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="9e9ba-195">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-195">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="9e9ba-196">[ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法僅適用于修改專案的名稱，而不是用於移動作業的程式。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-196">The [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method is intended for the modification of the name of an item only, and not for move operations.</span></span>
  <span data-ttu-id="9e9ba-197">如果 `newName` 參數包含路徑分隔符號，或可能導致專案變更其父系位置，則您的方法的執行應該會寫入錯誤。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-197">Your implementation of the method should write an error if the `newName` parameter contains path separators, or might otherwise cause the item to change its parent location.</span></span>

- <span data-ttu-id="9e9ba-198">根據預設，除非指定了[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ，否則此方法的覆寫不應重新命名物件。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-198">By default, overrides of this method should not rename objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is specified.</span></span> <span data-ttu-id="9e9ba-199">如果指定的路徑指出容器，則不需要[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。」</span><span class="sxs-lookup"><span data-stu-id="9e9ba-199">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="9e9ba-200">您的 ContainerCmdletprovider 必須先呼叫[Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，然後在對資料存放區進行任何變更之前，先檢查它的傳回值，然後再執行此[程式](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-200">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="9e9ba-201">這個方法是用來在對系統狀態進行變更時（例如，重新命名檔案），確認作業的執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-201">This method is used to confirm execution of an operation when a change is made to system state, for example, renaming files.</span></span>
  <span data-ttu-id="9e9ba-202">[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳送要變更的資源名稱給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入決定應該顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-202">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="9e9ba-203">在呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)後傳回後 `true` ， [ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法應會呼叫 system.servicemodel [. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法，並將其命名為.... 管理介面。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-203">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="9e9ba-204">這個方法會傳送一則確認訊息給使用者，以允許額外的意見反應，以指出作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-204">This method sends a message a confirmation message to the user to allow additional feedback to say if the operation should be continued.</span></span> <span data-ttu-id="9e9ba-205">提供者應呼叫[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作為額外檢查，以進行潛在危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-205">A provider should call [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a><span data-ttu-id="9e9ba-206">將動態參數附加至重新命名專案 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9e9ba-206">Attaching Dynamic Parameters to the Rename-Item Cmdlet</span></span>

<span data-ttu-id="9e9ba-207">有時，此 `Rename-Item` Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-207">Sometimes the `Rename-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="9e9ba-208">為了提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Renameitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-208">To provide these dynamic parameters, Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span> <span data-ttu-id="9e9ba-209">這個方法會在指定的路徑中抓取專案的參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-209">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="9e9ba-210">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Rename-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-210">The Windows PowerShell runtime uses the returned object to add the parameters to the `Rename-Item` cmdlet.</span></span>

<span data-ttu-id="9e9ba-211">此容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-211">This container provider does not implement this method.</span></span> <span data-ttu-id="9e9ba-212">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-212">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a><span data-ttu-id="9e9ba-213">建立新專案</span><span class="sxs-lookup"><span data-stu-id="9e9ba-213">Creating New Items</span></span>

<span data-ttu-id="9e9ba-214">若要建立新的專案，容器提供者必須執行[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以支援來自 Cmdlet 的呼叫 `New-Item` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-214">To create new items, a container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to support calls from the `New-Item` cmdlet.</span></span> <span data-ttu-id="9e9ba-215">這個方法會建立位於指定路徑的資料項目。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-215">This method creates a data item located at the specified path.</span></span> <span data-ttu-id="9e9ba-216">`type`Cmdlet 的參數包含新專案的提供者定義型別。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-216">The `type` parameter of the cmdlet contains the provider-defined type for the new item.</span></span> <span data-ttu-id="9e9ba-217">例如，FileSystem 提供者會使用 `type` 值為 "file" 或 "directory" 的參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-217">For example, the FileSystem provider uses a `type` parameter with a value of "file" or "directory".</span></span> <span data-ttu-id="9e9ba-218">`newItemValue`Cmdlet 的參數會指定新專案的提供者特定值。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-218">The `newItemValue` parameter of the cmdlet specifies a provider-specific value for the new item.</span></span>

<span data-ttu-id="9e9ba-219">以下是此提供者的[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法的執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-219">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method for this provider.</span></span>

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

#### <a name="things-to-remember-about-implementing-newitem"></a><span data-ttu-id="9e9ba-220">執行 NewItem 的相關事項</span><span class="sxs-lookup"><span data-stu-id="9e9ba-220">Things to Remember About Implementing NewItem</span></span>

<span data-ttu-id="9e9ba-221">下列條件可能適用于您的[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="9e9ba-221">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span></span>

- <span data-ttu-id="9e9ba-222">[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應針對參數中傳遞的字串執行不區分大小寫的比較 `type` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-222">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should perform a case-insensitive comparison of the string passed in the `type` parameter.</span></span>
  <span data-ttu-id="9e9ba-223">它也應該允許最少不明確的相符專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-223">It should also allow for least ambiguous matches.</span></span> <span data-ttu-id="9e9ba-224">例如，針對 "file" 和 "directory" 類型，只需要第一個字母來區分。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-224">For example, for the types "file" and "directory", only the first letter is required to disambiguate.</span></span> <span data-ttu-id="9e9ba-225">如果 `type` 參數指出提供者無法建立的類型，則[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該使用訊息來撰寫 ArgumentException，指出提供者可以建立的類型。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-225">If the `type` parameter indicates a type your provider cannot create, the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should write an ArgumentException with a message indicating the types the provider can create.</span></span>

- <span data-ttu-id="9e9ba-226">針對 `newItemValue` 參數，建議使用[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法的實值，以最小者接受字串。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-226">For the `newItemValue` parameter, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method is recommended to accept strings at a minimum.</span></span> <span data-ttu-id="9e9ba-227">它也應該針對相同的路徑，接受[Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法所抓取的物件型別（ItemCmdletprovider）。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-227">It should also accept the type of object that is retrieved by the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method for the same path.</span></span> <span data-ttu-id="9e9ba-228">[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法可以使用[languageprimitives.physicalequality. convertto-html \*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo)方法，將型別轉換成所需的型別（types）。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-228">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method can use the [System.Management.Automation.Languageprimitives.Convertto\*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) method to convert types to the desired type.</span></span>

- <span data-ttu-id="9e9ba-229">您的 ContainerCmdletprovider 必須先呼叫[Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，然後在對資料存放區進行任何變更之前，先檢查它的傳回值，然後再執行此[程式](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-229">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="9e9ba-230">呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true，則[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應呼叫[方法，](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)以做為可能危險的系統修改的額外檢查，以做為其他的檢查，以進行系統管理。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-230">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns true, the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a><span data-ttu-id="9e9ba-231">將動態參數附加至新的-Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9e9ba-231">Attaching Dynamic Parameters to the New-Item Cmdlet</span></span>

<span data-ttu-id="9e9ba-232">有時，此 `New-Item` Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-232">Sometimes the `New-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="9e9ba-233">若要提供這些動態參數，容器提供者必須執行[ContainerCmdletprovider. Newitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-233">To provide these dynamic parameters, the container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span> <span data-ttu-id="9e9ba-234">這個方法會在指定的路徑中抓取專案的參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-234">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="9e9ba-235">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `New-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-235">The Windows PowerShell runtime uses the returned object to add the parameters to the `New-Item` cmdlet.</span></span>

<span data-ttu-id="9e9ba-236">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-236">This provider does not implement this method.</span></span> <span data-ttu-id="9e9ba-237">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-237">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a><span data-ttu-id="9e9ba-238">移除專案</span><span class="sxs-lookup"><span data-stu-id="9e9ba-238">Removing Items</span></span>

<span data-ttu-id="9e9ba-239">若要移除專案，Windows PowerShell 提供者必須覆寫[ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以支援來自 Cmdlet 的呼叫 `Remove-Item` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-239">To remove items, the Windows PowerShell provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to support calls from the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="9e9ba-240">這個方法會在指定路徑的資料存放區中刪除專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-240">This method deletes an item from the data store at the specified path.</span></span> <span data-ttu-id="9e9ba-241">如果 `recurse` Cmdlet 的參數 `Remove-Item` 設定為 `true` ，則方法會移除所有子專案，而不論其層級為何。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-241">If the `recurse` parameter of the `Remove-Item` cmdlet is set to `true`, the method removes all child items regardless of their level.</span></span> <span data-ttu-id="9e9ba-242">如果參數設定為 `false` ，方法只會移除指定路徑中的單一專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-242">If the parameter is set to `false`, the method removes only a single item at the specified path.</span></span>

<span data-ttu-id="9e9ba-243">此提供者不支援移除專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-243">This provider does not support item removal.</span></span> <span data-ttu-id="9e9ba-244">不過，下列程式碼是[ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-244">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a><span data-ttu-id="9e9ba-245">執行 RemoveItem 的相關事項</span><span class="sxs-lookup"><span data-stu-id="9e9ba-245">Things to Remember About Implementing RemoveItem</span></span>

<span data-ttu-id="9e9ba-246">下列條件可能適用于您的[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="9e9ba-246">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span></span>

- <span data-ttu-id="9e9ba-247">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-247">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="9e9ba-248">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-248">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="9e9ba-249">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-249">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="9e9ba-250">根據預設，除非[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 true，否則此方法的覆寫不應移除物件。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-250">By default, overrides of this method should not remove objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to true.</span></span> <span data-ttu-id="9e9ba-251">如果指定的路徑指出容器，則不需要[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。」</span><span class="sxs-lookup"><span data-stu-id="9e9ba-251">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="9e9ba-252">您的[ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)會負責防止無限遞迴（如有迴圈連結），以及 like。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-252">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="9e9ba-253">應擲回適當的終止例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-253">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

- <span data-ttu-id="9e9ba-254">您的 ContainerCmdletprovider 必須先呼叫[Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，然後在對資料存放區進行任何變更之前，先檢查它的傳回值，然後再執行此[程式](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-254">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="9e9ba-255">在呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)之後 `true` ， [ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法應該會呼叫方法，以做為可能危險的系統修改的額外檢查，以做為其他的檢查，以進行[系統管理。](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)</span><span class="sxs-lookup"><span data-stu-id="9e9ba-255">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a><span data-ttu-id="9e9ba-256">將動態參數附加至 Remove 專案 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9e9ba-256">Attaching Dynamic Parameters to the Remove-Item Cmdlet</span></span>

<span data-ttu-id="9e9ba-257">有時，此 `Remove-Item` Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-257">Sometimes the `Remove-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="9e9ba-258">若要提供這些動態參數，容器提供者必須執行[ContainerCmdletprovider. Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-258">To provide these dynamic parameters, the container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="9e9ba-259">這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-259">This method retrieves the dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="9e9ba-260">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Remove-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-260">The Windows PowerShell runtime uses the returned object to add the parameters to the `Remove-Item` cmdlet.</span></span>

<span data-ttu-id="9e9ba-261">此容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-261">This container provider does not implement this method.</span></span> <span data-ttu-id="9e9ba-262">不過，下列程式碼是[ContainerCmdletprovider. Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-262">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a><span data-ttu-id="9e9ba-263">查詢子專案</span><span class="sxs-lookup"><span data-stu-id="9e9ba-263">Querying for Child Items</span></span>

<span data-ttu-id="9e9ba-264">若要查看子專案是否存在於指定的路徑，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-264">To check to see if child items exist at the specified path, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method.</span></span> <span data-ttu-id="9e9ba-265">如果專案具有子系，則這個方法會傳回 `true` ，否則會傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-265">This method returns `true` if the item has children, and `false` otherwise.</span></span> <span data-ttu-id="9e9ba-266">如果是 null 或空的路徑，方法會將資料存放區中的任何專案視為子系，並傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-266">For a null or empty path, the method considers any items in the data store to be children and returns `true`.</span></span>

<span data-ttu-id="9e9ba-267">以下是[ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法的覆寫：。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-267">Here is the override for the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method.</span></span> <span data-ttu-id="9e9ba-268">如果 ChunkPath helper 方法建立兩個以上的路徑部分，此方法會傳回 `false` ，因為只會定義資料庫容器和資料表容器。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-268">If there are more than two path parts created by the ChunkPath helper method, the method returns `false`, since only a database container and a table container are defined.</span></span> <span data-ttu-id="9e9ba-269">如需此協助程式方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)中所討論的 ChunkPath 方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-269">For more information about this helper method, see the ChunkPath method is discussed in [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="1094-1097":::

#### <a name="things-to-remember-about-implementing-haschilditems"></a><span data-ttu-id="9e9ba-270">執行 HasChildItems 的相關事項</span><span class="sxs-lookup"><span data-stu-id="9e9ba-270">Things to Remember About Implementing HasChildItems</span></span>

<span data-ttu-id="9e9ba-271">下列條件可能適用于您的[ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="9e9ba-271">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):</span></span>

- <span data-ttu-id="9e9ba-272">如果容器提供者公開包含感興趣掛接點的根，則在為路徑傳入 null 或空字串時，應該會傳回[ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法的執行。 `true`</span><span class="sxs-lookup"><span data-stu-id="9e9ba-272">If the container provider exposes a root that contains interesting mount points, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method should return `true` when a null or an empty string is passed in for the path.</span></span>

## <a name="copying-items"></a><span data-ttu-id="9e9ba-273">複製專案</span><span class="sxs-lookup"><span data-stu-id="9e9ba-273">Copying Items</span></span>

<span data-ttu-id="9e9ba-274">若要複製專案，容器提供者必須執行[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以支援來自 Cmdlet 的呼叫 `Copy-Item` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-274">To copy items, the container provider must implement the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to support calls from the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="9e9ba-275">這個方法會將資料項目從 Cmdlet 的參數所指示的位置複製 `path` 到參數所指示的位置 `copyPath` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-275">This method copies a data item from the location indicated by the `path` parameter of the cmdlet to the location indicated by the `copyPath` parameter.</span></span> <span data-ttu-id="9e9ba-276">如果 `recurse` 指定參數，方法會複製所有子容器。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-276">If the `recurse` parameter is specified, the method copies all sub-containers.</span></span> <span data-ttu-id="9e9ba-277">如果未指定參數，方法只會複製單一層級的專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-277">If the parameter is not specified, the method copies only a single level of items.</span></span>

<span data-ttu-id="9e9ba-278">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-278">This provider does not implement this method.</span></span> <span data-ttu-id="9e9ba-279">不過，下列程式碼是[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-279">However, the following code is the default implementation of [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a><span data-ttu-id="9e9ba-280">執行 CopyItem 的相關事項</span><span class="sxs-lookup"><span data-stu-id="9e9ba-280">Things to Remember About Implementing CopyItem</span></span>

<span data-ttu-id="9e9ba-281">下列條件可能適用于您的[ContainerCmdletProvider. CopyItem 的程式](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)：</span><span class="sxs-lookup"><span data-stu-id="9e9ba-281">The following conditions may apply to your implementation of [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):</span></span>

- <span data-ttu-id="9e9ba-282">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-282">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="9e9ba-283">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-283">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="9e9ba-284">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-284">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="9e9ba-285">根據預設，除非[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為，否則此方法的覆寫不應複製現有物件的物件 `true` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-285">By default, overrides of this method should not copy objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="9e9ba-286">例如，FileSystem 提供者不會將 c:\temp\abc.txt 複製到現有的 c:\abc.txt 檔案，除非[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-286">For example, the FileSystem provider will not copy c:\temp\abc.txt over an existing c:\abc.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="9e9ba-287">如果參數中指定的路徑 `copyPath` 存在，並指出容器，則不需要[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-287">If the path specified in the `copyPath` parameter exists and indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="9e9ba-288">在此情況下， [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)會將參數所指示的專案複製 `path` 到參數所指示的容器， `copyPath` 做為子系。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-288">In this case, [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) should copy the item indicated by the `path` parameter to the container indicated by the `copyPath` parameter as a child.</span></span>

- <span data-ttu-id="9e9ba-289">您的[ContainerCmdletProvider。 CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)會負責在有迴圈連結時防止無限遞迴，而且也會發生類似的情況。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-289">Your implementation of [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="9e9ba-290">應擲回適當的終止例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-290">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

- <span data-ttu-id="9e9ba-291">您的[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)必須先呼叫 CopyItem 方法，然後在對資料存放區進行任何變更之前，先檢查其傳回值，然後再進行[此程式。](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)</span><span class="sxs-lookup"><span data-stu-id="9e9ba-291">Your implementation of the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="9e9ba-292">呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true，則[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法應呼叫[方法，](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)以做為可能危險系統修改的額外檢查，以進行進一步的檢查，而不需要進行此程式。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-292">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns true, the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span> <span data-ttu-id="9e9ba-293">如需呼叫這些方法的詳細資訊，請參閱[重新命名專案](#renaming-items)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-293">For more information about calling these methods, see [Rename Items](#renaming-items).</span></span>

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a><span data-ttu-id="9e9ba-294">將動態參數附加至複製-Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9e9ba-294">Attaching Dynamic Parameters to the Copy-Item Cmdlet</span></span>

<span data-ttu-id="9e9ba-295">有時，此 `Copy-Item` Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-295">Sometimes the `Copy-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="9e9ba-296">若要提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-296">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="9e9ba-297">這個方法會在指定的路徑中抓取專案的參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-297">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="9e9ba-298">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Copy-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-298">The Windows PowerShell runtime uses the returned object to add the parameters to the `Copy-Item` cmdlet.</span></span>

<span data-ttu-id="9e9ba-299">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-299">This provider does not implement this method.</span></span> <span data-ttu-id="9e9ba-300">不過，下列程式碼是[ContainerCmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-300">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a><span data-ttu-id="9e9ba-301">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="9e9ba-301">Code Sample</span></span>

<span data-ttu-id="9e9ba-302">如需完整的範例程式碼，請參閱[AccessDbProviderSample04 程式碼範例](./accessdbprovidersample04-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-302">For complete sample code, see [AccessDbProviderSample04 Code Sample](./accessdbprovidersample04-code-sample.md).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="9e9ba-303">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9e9ba-303">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="9e9ba-304">請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-304">See [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="9e9ba-305">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9e9ba-305">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="9e9ba-306">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-306">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="9e9ba-307">請注意，下列範例輸出會使用虛構的 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-307">Be aware that the following example output uses a fictitious Access database.</span></span>

1. <span data-ttu-id="9e9ba-308">執行 `Get-ChildItem` Cmdlet，從 Access 資料庫的 Customers 資料表中取出子專案的清單。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-308">Run the `Get-ChildItem` cmdlet to retrieve the list of child items from a Customers table in the Access database.</span></span>

   ```powershell
   Get-ChildItem mydb:customers
   ```

   <span data-ttu-id="9e9ba-309">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-309">The following output appears.</span></span>

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

2. <span data-ttu-id="9e9ba-310">再次執行 `Get-ChildItem` Cmdlet 以取得資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-310">Run the `Get-ChildItem` cmdlet again to retrieve the data of a table.</span></span>

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   <span data-ttu-id="9e9ba-311">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-311">The following output appears.</span></span>

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. <span data-ttu-id="9e9ba-312">現在，使用 `Get-Item` Cmdlet 來抓取資料表中第0列的專案。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-312">Now use the `Get-Item` cmdlet to retrieve the items at row 0 in the data table.</span></span>

   ```powershell
   Get-Item mydb:\customers\0
   ```

   <span data-ttu-id="9e9ba-313">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-313">The following output appears.</span></span>

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. <span data-ttu-id="9e9ba-314">重複使用 `Get-Item` ，以取得資料列0中的專案資料。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-314">Reuse `Get-Item` to retrieve the data for the items in row 0.</span></span>

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   <span data-ttu-id="9e9ba-315">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-315">The following output appears.</span></span>

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

5. <span data-ttu-id="9e9ba-316">現在使用 `New-Item` Cmdlet 將資料列加入至現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-316">Now use the `New-Item` cmdlet to add a row to an existing table.</span></span> <span data-ttu-id="9e9ba-317">`Path`參數會指定資料列的完整路徑，而且必須指出大於資料表中現有資料列數目的資料列編號。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-317">The `Path` parameter specifies the full path to the row, and must indicate a row number that is greater than the existing number of rows in the table.</span></span> <span data-ttu-id="9e9ba-318">`Type`參數會指出 "row"，以指定要加入的專案類型。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-318">The `Type` parameter indicates "row" to specify that type of item to add.</span></span>
   <span data-ttu-id="9e9ba-319">最後，參數會為 `Value` 資料列指定以逗號分隔的資料行值清單。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-319">Finally, the `Value` parameter specifies a comma-delimited list of column values for the row.</span></span>

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. <span data-ttu-id="9e9ba-320">確認新專案作業的正確性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-320">Verify the correctness of the new item operation as follows.</span></span>

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   <span data-ttu-id="9e9ba-321">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="9e9ba-321">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9e9ba-322">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e9ba-322">See Also</span></span>

[<span data-ttu-id="9e9ba-323">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9e9ba-323">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="9e9ba-324">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9e9ba-324">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="9e9ba-325">執行 Windows PowerShell 提供者專案</span><span class="sxs-lookup"><span data-stu-id="9e9ba-325">Implementing an Item Windows PowerShell Provider</span></span>](./creating-a-windows-powershell-item-provider.md)

[<span data-ttu-id="9e9ba-326">執行流覽 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9e9ba-326">Implementing a Navigation Windows PowerShell Provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

<span data-ttu-id="9e9ba-327">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="9e9ba-327">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="9e9ba-328">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9e9ba-328">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="9e9ba-329">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="9e9ba-329">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
