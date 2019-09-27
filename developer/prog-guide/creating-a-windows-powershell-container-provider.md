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
ms.openlocfilehash: 0b3ec95dde92644be07927a1d470fe97648c124c
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323511"
---
# <a name="creating-a-windows-powershell-container-provider"></a><span data-ttu-id="35064-102">建立 Windows PowerShell 容器提供者</span><span class="sxs-lookup"><span data-stu-id="35064-102">Creating a Windows PowerShell Container Provider</span></span>

<span data-ttu-id="35064-103">本主題說明如何建立可在多層式資料存放區上使用的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="35064-103">This topic describes how to create a Windows PowerShell provider that can work on multi-layer data stores.</span></span> <span data-ttu-id="35064-104">對於這種類型的資料存放區，存放區的最上層包含根專案，而每個後續層級稱為子專案的節點。</span><span class="sxs-lookup"><span data-stu-id="35064-104">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="35064-105">藉由允許使用者在這些子節點上工作，使用者可以透過資料存放區以階層方式進行互動。</span><span class="sxs-lookup"><span data-stu-id="35064-105">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

<span data-ttu-id="35064-106">可在多層級資料存放區上工作的提供者稱為 Windows PowerShell 容器提供者。</span><span class="sxs-lookup"><span data-stu-id="35064-106">Providers that can work on multi-level data stores are referred to as Windows PowerShell container providers.</span></span> <span data-ttu-id="35064-107">不過，請注意，只有在有一個容器（沒有嵌套的容器）包含專案時，才可以使用 Windows PowerShell 容器提供者。</span><span class="sxs-lookup"><span data-stu-id="35064-107">However, be aware that a Windows PowerShell container provider can be used only when there is one container (no nested containers) with items in it.</span></span> <span data-ttu-id="35064-108">如果有嵌套的容器，則您必須執行 Windows PowerShell 流覽提供者。</span><span class="sxs-lookup"><span data-stu-id="35064-108">If there are nested containers, then you must implement a Windows PowerShell navigation provider.</span></span> <span data-ttu-id="35064-109">如需有關執行 Windows PowerShell 流覽提供者的詳細資訊，請參閱[建立 Windows Powershell 流覽提供者](./creating-a-windows-powershell-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="35064-109">For more information about implementing Windows PowerShell navigation provider, see [Creating a Windows PowerShell Navigation Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

> [!NOTE]
> <span data-ttu-id="35064-110">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的原始程式檔（AccessDBSampleProvider04.cs）。</span><span class="sxs-lookup"><span data-stu-id="35064-110">You can download the C# source file (AccessDBSampleProvider04.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="35064-111">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="35064-111">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="35064-112">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="35064-112">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="35064-113">如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="35064-113">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="35064-114">這裡所述的 Windows PowerShell 容器提供者會將資料庫定義為其單一容器，並將資料庫的資料表和資料列定義為容器的專案。</span><span class="sxs-lookup"><span data-stu-id="35064-114">The Windows PowerShell container provider described here defines the database as its single container, with the tables and rows of the database defined as items of the container.</span></span>

> [!CAUTION]
> <span data-ttu-id="35064-115">請注意，這項設計假設有一個具有名稱識別碼之欄位的資料庫，而且欄位的類型是 LongInteger。</span><span class="sxs-lookup"><span data-stu-id="35064-115">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

## <a name="defining-a-windows-powershell-container-provider-class"></a><span data-ttu-id="35064-116">定義 Windows PowerShell 容器提供者類別</span><span class="sxs-lookup"><span data-stu-id="35064-116">Defining a Windows PowerShell Container Provider Class</span></span>

<span data-ttu-id="35064-117">Windows PowerShell 容器提供者必須定義一個衍生自[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基類的 .net 類別（class）。</span><span class="sxs-lookup"><span data-stu-id="35064-117">A Windows PowerShell container provider must define a .NET class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="35064-118">以下是本節所述 Windows PowerShell 容器提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="35064-118">Here is the class definition for the Windows PowerShell container provider described in this section.</span></span>

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

<span data-ttu-id="35064-119">請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="35064-119">Notice that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="35064-120">第一個參數會為 Windows PowerShell 所使用的提供者指定易記的名稱。</span><span class="sxs-lookup"><span data-stu-id="35064-120">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="35064-121">第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="35064-121">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="35064-122">對於此提供者，不會新增任何 Windows PowerShell 特有的功能。</span><span class="sxs-lookup"><span data-stu-id="35064-122">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="35064-123">定義基本功能</span><span class="sxs-lookup"><span data-stu-id="35064-123">Defining Base Functionality</span></span>

<span data-ttu-id="35064-124">如[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)中所述， [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別衍生自數個提供不同提供者功能的其他類別。</span><span class="sxs-lookup"><span data-stu-id="35064-124">As described in [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="35064-125">因此，Windows PowerShell 容器提供者必須定義這些類別所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="35064-125">A Windows PowerShell container provider, therefore, needs to define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="35064-126">若要執行功能來新增會話特定的初始化資訊，以及釋放提供者所使用的資源，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="35064-126">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="35064-127">不過，大部分的提供者（包括這裡所述的提供者）都可以使用 Windows PowerShell 所提供的這項功能的預設執行。</span><span class="sxs-lookup"><span data-stu-id="35064-127">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="35064-128">若要取得資料存放區的存取權，提供者必須執行[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的方法。</span><span class="sxs-lookup"><span data-stu-id="35064-128">To get access to the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="35064-129">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="35064-129">For more information about implementing these methods, see [Creating an Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="35064-130">若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="35064-130">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="35064-131">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="35064-131">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

## <a name="retrieving-child-items"></a><span data-ttu-id="35064-132">正在抓取子專案</span><span class="sxs-lookup"><span data-stu-id="35064-132">Retrieving Child Items</span></span>

<span data-ttu-id="35064-133">若要取得子專案，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以支援來自 Cmdlet 的`Get-ChildItem`呼叫。</span><span class="sxs-lookup"><span data-stu-id="35064-133">To retrieve a child item, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to support calls from the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="35064-134">這個方法會從資料存放區抓取子專案，並將它們以物件的形式寫入管線。</span><span class="sxs-lookup"><span data-stu-id="35064-134">This method retrieves child items from the data store and writes them to the pipeline as objects.</span></span> <span data-ttu-id="35064-135">如果指定了 Cmdlet 的參數，方法會抓取所有子系，而不論它們位於哪一層級。`recurse`</span><span class="sxs-lookup"><span data-stu-id="35064-135">If the `recurse` parameter of the cmdlet is specified, the method retrieves all children regardless of what level they are at.</span></span> <span data-ttu-id="35064-136">如果未指定參數，方法只會抓取單一層級的子系。 `recurse`</span><span class="sxs-lookup"><span data-stu-id="35064-136">If the `recurse` parameter is not specified, the method retrieves only a single level of children.</span></span>

<span data-ttu-id="35064-137">以下是此提供者的[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行。</span><span class="sxs-lookup"><span data-stu-id="35064-137">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method for this provider.</span></span> <span data-ttu-id="35064-138">請注意，此方法會在路徑指出 Access 資料庫時，抓取所有資料庫資料表中的子專案，並在路徑表示資料表時，從該資料表的資料列抓取子專案。</span><span class="sxs-lookup"><span data-stu-id="35064-138">Notice that this method retrieves the child items in all database tables when the path indicates the Access database, and retrieves the child items from the rows of that table if the path indicates a data table.</span></span>

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

#### <a name="things-to-remember-about-implementing-getchilditems"></a><span data-ttu-id="35064-139">執行 GetChildItems 的相關事項</span><span class="sxs-lookup"><span data-stu-id="35064-139">Things to Remember About Implementing GetChildItems</span></span>

<span data-ttu-id="35064-140">下列條件可能適用于您的[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="35064-140">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span></span>

- <span data-ttu-id="35064-141">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="35064-141">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="35064-142">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="35064-142">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="35064-143">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="35064-143">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="35064-144">此方法的實體系應該考慮到可能會讓使用者看見專案的任何形式的存取權。</span><span class="sxs-lookup"><span data-stu-id="35064-144">The implementation of this method should take into account any form of access to the item that might make the item visible to the user.</span></span> <span data-ttu-id="35064-145">例如，如果使用者透過 FileSystem 提供者（由 Windows PowerShell 提供）擁有檔案的寫入存取權，但不是讀取權限，則檔案仍然存在，而且[ItemCmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 會傳回`true`.</span><span class="sxs-lookup"><span data-stu-id="35064-145">For example, if a user has write access to a file through the FileSystem provider (supplied by Windows PowerShell), but not read access, the file still exists and [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) returns `true`.</span></span> <span data-ttu-id="35064-146">您的執行可能需要檢查父專案，以查看是否可以列舉子系。</span><span class="sxs-lookup"><span data-stu-id="35064-146">Your implementation might require the checking of a parent item to see if the child can be enumerated.</span></span>

- <span data-ttu-id="35064-147">寫入多個專案時， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="35064-147">When writing multiple items, the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method can take some time.</span></span> <span data-ttu-id="35064-148">您可以設計提供者，以一次使用[Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法來撰寫專案。</span><span class="sxs-lookup"><span data-stu-id="35064-148">You can design your provider to write the items using the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method one at a time.</span></span> <span data-ttu-id="35064-149">使用這項技術會向使用者呈現串流中的專案。</span><span class="sxs-lookup"><span data-stu-id="35064-149">Using this technique will present the items to the user in a stream.</span></span>

- <span data-ttu-id="35064-150">您的[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)會負責防止無限遞迴（如有迴圈連結），以及 like。</span><span class="sxs-lookup"><span data-stu-id="35064-150">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="35064-151">應擲回適當的終止例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="35064-151">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a><span data-ttu-id="35064-152">將動態參數附加至 Get-childitem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35064-152">Attaching Dynamic Parameters to the Get-ChildItem Cmdlet</span></span>

<span data-ttu-id="35064-153">有時候呼叫`Get-ChildItem` [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的 Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="35064-153">Sometimes the `Get-ChildItem` cmdlet that calls [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="35064-154">若要提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Getchilditemsdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="35064-154">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) method.</span></span> <span data-ttu-id="35064-155">這個方法會在指定的路徑上抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)類似的剖析屬性。目標.</span><span class="sxs-lookup"><span data-stu-id="35064-155">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="35064-156">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至`Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35064-156">The Windows PowerShell runtime uses the returned object to add the parameters to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="35064-157">這個 Windows PowerShell 容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="35064-157">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="35064-158">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="35064-158">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a><span data-ttu-id="35064-159">正在抓取子專案名稱</span><span class="sxs-lookup"><span data-stu-id="35064-159">Retrieving Child Item Names</span></span>

<span data-ttu-id="35064-160">若要取得子專案的名稱，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以支援從 Cmdlet 的`Get-ChildItem`呼叫`Name`已指定參數。</span><span class="sxs-lookup"><span data-stu-id="35064-160">To retrieve the names of child items, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to support calls from the `Get-ChildItem` cmdlet when its `Name` parameter is specified.</span></span> <span data-ttu-id="35064-161">如果指定 Cmdlet 的`returnAllContainers`參數，這個方法會抓取所有容器之指定路徑或子專案名稱的子專案名稱。</span><span class="sxs-lookup"><span data-stu-id="35064-161">This method retrieves the names of the child items for the specified path or child item names for all containers if the `returnAllContainers` parameter of the cmdlet is specified.</span></span> <span data-ttu-id="35064-162">子名稱是路徑的分葉部分。</span><span class="sxs-lookup"><span data-stu-id="35064-162">A child name is the leaf portion of a path.</span></span> <span data-ttu-id="35064-163">例如，路徑 c:\windows\system32\abc.dll 的子名稱是 "abc"。</span><span class="sxs-lookup"><span data-stu-id="35064-163">For example, the child name for the path c:\windows\system32\abc.dll is "abc.dll".</span></span> <span data-ttu-id="35064-164">目錄 c:\windows\system32 的子名稱是 "system32"。</span><span class="sxs-lookup"><span data-stu-id="35064-164">The child name for the directory c:\windows\system32 is "system32".</span></span>

<span data-ttu-id="35064-165">以下是此提供者的[ContainerCmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法的執行。</span><span class="sxs-lookup"><span data-stu-id="35064-165">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method for this provider.</span></span> <span data-ttu-id="35064-166">請注意，如果指定的路徑指示資料表的 Access 資料庫（磁片磁碟機）和資料列編號，方法會抓取資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="35064-166">Notice that the method retrieves table names if the specified path indicates the Access database (drive) and row numbers if the path indicates a table.</span></span>

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

#### <a name="things-to-remember-about-implementing-getchildnames"></a><span data-ttu-id="35064-167">執行 GetChildNames 的相關事項</span><span class="sxs-lookup"><span data-stu-id="35064-167">Things to Remember About Implementing GetChildNames</span></span>

<span data-ttu-id="35064-168">下列條件可能適用于您的[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="35064-168">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span></span>

- <span data-ttu-id="35064-169">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="35064-169">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="35064-170">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="35064-170">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="35064-171">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="35064-171">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

  > [!NOTE]
  > <span data-ttu-id="35064-172">當指定 Cmdlet 的`returnAllContainers`參數時，就會發生此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="35064-172">An exception to this rule occurs when the `returnAllContainers` parameter of the cmdlet is specified.</span></span> <span data-ttu-id="35064-173">在此情況下，方法應該會抓取容器的任何子系名稱，即使它不符合 Cmdletprovider 的值也是一樣[。](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter) [Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)，或[Cmdletprovider. Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)屬性（property）的 \* （系統管理）。</span><span class="sxs-lookup"><span data-stu-id="35064-173">In this case, the method should retrieve any child name for a container, even if it does not match the values of the [System.Management.Automation.Provider.Cmdletprovider.Filter\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), or [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) properties.</span></span>

- <span data-ttu-id="35064-174">根據預設，除非指定了[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ，否則此方法的覆寫不應抓取使用者通常會隱藏的物件名稱，。</span><span class="sxs-lookup"><span data-stu-id="35064-174">By default, overrides of this method should not retrieve names of objects that are generally hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is specified.</span></span> <span data-ttu-id="35064-175">如果指定的路徑指出容器，則不需要[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。」</span><span class="sxs-lookup"><span data-stu-id="35064-175">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="35064-176">您的[ContainerCmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)會負責防止無限遞迴（如有迴圈連結），以及 like。</span><span class="sxs-lookup"><span data-stu-id="35064-176">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="35064-177">應擲回適當的終止例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="35064-177">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a><span data-ttu-id="35064-178">將動態參數附加至 Get-childitem Cmdlet （名稱）</span><span class="sxs-lookup"><span data-stu-id="35064-178">Attaching Dynamic Parameters to the Get-ChildItem Cmdlet (Name)</span></span>

<span data-ttu-id="35064-179">有時 Cmdlet （ `Name`使用參數）需要在執行時間動態指定的其他參數。 `Get-ChildItem`</span><span class="sxs-lookup"><span data-stu-id="35064-179">Sometimes the `Get-ChildItem` cmdlet (with the `Name` parameter) requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="35064-180">若要提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Getchildnamesdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="35064-180">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) method.</span></span> <span data-ttu-id="35064-181">這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或 Runtimedefinedparameterdictionary 類似的剖析屬性[。](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="35064-181">This method retrieves the dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="35064-182">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至`Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35064-182">The Windows PowerShell runtime uses the returned object to add the parameters to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="35064-183">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="35064-183">This provider does not implement this method.</span></span> <span data-ttu-id="35064-184">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="35064-184">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a><span data-ttu-id="35064-185">重新命名專案</span><span class="sxs-lookup"><span data-stu-id="35064-185">Renaming Items</span></span>

<span data-ttu-id="35064-186">若要重新命名專案，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，以支援來自 Cmdlet 的`Rename-Item`呼叫。</span><span class="sxs-lookup"><span data-stu-id="35064-186">To rename an item, a Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method to support calls from the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="35064-187">這個方法會將指定路徑的專案名稱變更為提供的新名稱。</span><span class="sxs-lookup"><span data-stu-id="35064-187">This method changes the name of the item at the specified path to the new name provided.</span></span> <span data-ttu-id="35064-188">新名稱必須一律相對於父專案（容器）。</span><span class="sxs-lookup"><span data-stu-id="35064-188">The new name must always be relative to the parent item (container).</span></span>

<span data-ttu-id="35064-189">此提供者不會覆寫[ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法。</span><span class="sxs-lookup"><span data-stu-id="35064-189">This provider does not override the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method.</span></span> <span data-ttu-id="35064-190">不過，下列是預設的執行。</span><span class="sxs-lookup"><span data-stu-id="35064-190">However, the following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a><span data-ttu-id="35064-191">執行 RenameItem 的相關事項</span><span class="sxs-lookup"><span data-stu-id="35064-191">Things to Remember About Implementing RenameItem</span></span>

<span data-ttu-id="35064-192">下列條件可能適用于您的[ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="35064-192">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):</span></span>

- <span data-ttu-id="35064-193">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="35064-193">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="35064-194">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="35064-194">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="35064-195">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="35064-195">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="35064-196">[ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法僅適用于修改專案的名稱，而不是用於移動作業的程式。</span><span class="sxs-lookup"><span data-stu-id="35064-196">The [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method is intended for the modification of the name of an item only, and not for move operations.</span></span> <span data-ttu-id="35064-197">如果`newName`參數包含路徑分隔符號，或可能導致專案變更其父系位置，則您的方法的執行應該會寫入錯誤。</span><span class="sxs-lookup"><span data-stu-id="35064-197">Your implementation of the method should write an error if the `newName` parameter contains path separators, or might otherwise cause the item to change its parent location.</span></span>

- <span data-ttu-id="35064-198">根據預設，除非指定了[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ，否則此方法的覆寫不應重新命名物件。</span><span class="sxs-lookup"><span data-stu-id="35064-198">By default, overrides of this method should not rename objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is specified.</span></span> <span data-ttu-id="35064-199">如果指定的路徑指出容器，則不需要[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。」</span><span class="sxs-lookup"><span data-stu-id="35064-199">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="35064-200">您的[ContainerCmdletprovider Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法應會呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並先檢查其傳回值，然後才會進行此程式對資料存放區進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="35064-200">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="35064-201">這個方法是用來在對系統狀態進行變更時（例如，重新命名檔案），確認作業的執行。</span><span class="sxs-lookup"><span data-stu-id="35064-201">This method is used to confirm execution of an operation when a change is made to system state, for example, renaming files.</span></span> <span data-ttu-id="35064-202">[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳送要變更的資源名稱給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數列入決定應該顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="35064-202">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="35064-203">在呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) `true`後傳回後， [ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法應該會呼叫[，而該程式會傳回Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法的。</span><span class="sxs-lookup"><span data-stu-id="35064-203">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="35064-204">這個方法會傳送一則確認訊息給使用者，以允許額外的意見反應，以指出作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="35064-204">This method sends a message a confirmation message to the user to allow additional feedback to say if the operation should be continued.</span></span> <span data-ttu-id="35064-205">提供者應呼叫[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作為額外檢查，以進行潛在危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="35064-205">A provider should call [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a><span data-ttu-id="35064-206">將動態參數附加至重新命名專案 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35064-206">Attaching Dynamic Parameters to the Rename-Item Cmdlet</span></span>

<span data-ttu-id="35064-207">有時， `Rename-Item`此 Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="35064-207">Sometimes the `Rename-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="35064-208">為了提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Renameitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="35064-208">To provide these dynamic parameters, Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span> <span data-ttu-id="35064-209">這個方法會在指定的路徑中抓取專案的參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或 Runtimedefinedparameterdictionary 類似的剖析屬性[。](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)目標.</span><span class="sxs-lookup"><span data-stu-id="35064-209">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="35064-210">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至`Rename-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35064-210">The Windows PowerShell runtime uses the returned object to add the parameters to the `Rename-Item` cmdlet.</span></span>

<span data-ttu-id="35064-211">此容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="35064-211">This container provider does not implement this method.</span></span> <span data-ttu-id="35064-212">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="35064-212">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a><span data-ttu-id="35064-213">建立新專案</span><span class="sxs-lookup"><span data-stu-id="35064-213">Creating New Items</span></span>

<span data-ttu-id="35064-214">若要建立新的專案，容器提供者必須執行[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以支援來自 Cmdlet 的`New-Item`呼叫。</span><span class="sxs-lookup"><span data-stu-id="35064-214">To create new items, a container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to support calls from the `New-Item` cmdlet.</span></span> <span data-ttu-id="35064-215">這個方法會建立位於指定路徑的資料項目。</span><span class="sxs-lookup"><span data-stu-id="35064-215">This method creates a data item located at the specified path.</span></span> <span data-ttu-id="35064-216">Cmdlet `type`的參數包含新專案的提供者定義型別。</span><span class="sxs-lookup"><span data-stu-id="35064-216">The `type` parameter of the cmdlet contains the provider-defined type for the new item.</span></span> <span data-ttu-id="35064-217">例如，FileSystem 提供者會使用`type`值為 "file" 或 "directory" 的參數。</span><span class="sxs-lookup"><span data-stu-id="35064-217">For example, the FileSystem provider uses a `type` parameter with a value of "file" or "directory".</span></span> <span data-ttu-id="35064-218">Cmdlet `newItemValue`的參數會指定新專案的提供者特定值。</span><span class="sxs-lookup"><span data-stu-id="35064-218">The `newItemValue` parameter of the cmdlet specifies a provider-specific value for the new item.</span></span>

<span data-ttu-id="35064-219">以下是此提供者的[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法的執行。</span><span class="sxs-lookup"><span data-stu-id="35064-219">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method for this provider.</span></span>

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

#### <a name="things-to-remember-about-implementing-newitem"></a><span data-ttu-id="35064-220">執行 NewItem 的相關事項</span><span class="sxs-lookup"><span data-stu-id="35064-220">Things to Remember About Implementing NewItem</span></span>

<span data-ttu-id="35064-221">下列條件可能適用于您的[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="35064-221">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span></span>

- <span data-ttu-id="35064-222">[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應針對`type`參數中傳遞的字串執行不區分大小寫的比較。</span><span class="sxs-lookup"><span data-stu-id="35064-222">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should perform a case-insensitive comparison of the string passed in the `type` parameter.</span></span> <span data-ttu-id="35064-223">它也應該允許最少不明確的相符專案。</span><span class="sxs-lookup"><span data-stu-id="35064-223">It should also allow for least ambiguous matches.</span></span> <span data-ttu-id="35064-224">例如，針對 "file" 和 "directory" 類型，只需要第一個字母來區分。</span><span class="sxs-lookup"><span data-stu-id="35064-224">For example, for the types "file" and "directory", only the first letter is required to disambiguate.</span></span> <span data-ttu-id="35064-225">如果參數指出您的提供者無法建立的類型，則[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應寫入 ArgumentException，並提供訊息，指出類型`type`提供者可以建立。</span><span class="sxs-lookup"><span data-stu-id="35064-225">If the `type` parameter indicates a type your provider cannot create, the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should write an ArgumentException with a message indicating the types the provider can create.</span></span>

- <span data-ttu-id="35064-226">針對參數，建議使用[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法的實值，以最小者接受字串。 `newItemValue`</span><span class="sxs-lookup"><span data-stu-id="35064-226">For the `newItemValue` parameter, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method is recommended to accept strings at a minimum.</span></span> <span data-ttu-id="35064-227">它也應該針對相同的路徑，接受[Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法所抓取的物件型別（ItemCmdletprovider）。</span><span class="sxs-lookup"><span data-stu-id="35064-227">It should also accept the type of object that is retrieved by the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method for the same path.</span></span> <span data-ttu-id="35064-228">[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法可以使用[languageprimitives.physicalequality. convertto-html \*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo)方法，將型別轉換成所需的型別（types）。</span><span class="sxs-lookup"><span data-stu-id="35064-228">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method can use the [System.Management.Automation.Languageprimitives.Convertto\*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) method to convert types to the desired type.</span></span>

- <span data-ttu-id="35064-229">您的[ContainerCmdletprovider Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應會呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並先檢查其傳回值，然後才會進行此程式對資料存放區進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="35064-229">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="35064-230">在 Cmdletprovider 的呼叫之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true，然後， [ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該會呼叫該[程式。Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法，做為潛在危險系統修改的額外檢查。</span><span class="sxs-lookup"><span data-stu-id="35064-230">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns true, the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a><span data-ttu-id="35064-231">將動態參數附加至新的-Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35064-231">Attaching Dynamic Parameters to the New-Item Cmdlet</span></span>

<span data-ttu-id="35064-232">有時， `New-Item`此 Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="35064-232">Sometimes the `New-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="35064-233">若要提供這些動態參數，容器提供者必須執行[ContainerCmdletprovider. Newitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="35064-233">To provide these dynamic parameters, the container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span> <span data-ttu-id="35064-234">這個方法會在指定的路徑中抓取專案的參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或 Runtimedefinedparameterdictionary 類似的剖析屬性[。](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)目標.</span><span class="sxs-lookup"><span data-stu-id="35064-234">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="35064-235">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至`New-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35064-235">The Windows PowerShell runtime uses the returned object to add the parameters to the `New-Item` cmdlet.</span></span>

<span data-ttu-id="35064-236">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="35064-236">This provider does not implement this method.</span></span> <span data-ttu-id="35064-237">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="35064-237">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a><span data-ttu-id="35064-238">移除專案</span><span class="sxs-lookup"><span data-stu-id="35064-238">Removing Items</span></span>

<span data-ttu-id="35064-239">若要移除專案，Windows PowerShell 提供者必須覆寫[ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以支援來自 Cmdlet 的`Remove-Item`呼叫。</span><span class="sxs-lookup"><span data-stu-id="35064-239">To remove items, the Windows PowerShell provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to support calls from the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="35064-240">這個方法會在指定路徑的資料存放區中刪除專案。</span><span class="sxs-lookup"><span data-stu-id="35064-240">This method deletes an item from the data store at the specified path.</span></span> <span data-ttu-id="35064-241">如果`Remove-Item` Cmdlet `recurse`的參數設定為`true`，則方法會移除所有子專案，而不論其層級為何。</span><span class="sxs-lookup"><span data-stu-id="35064-241">If the `recurse` parameter of the `Remove-Item` cmdlet is set to `true`, the method removes all child items regardless of their level.</span></span> <span data-ttu-id="35064-242">如果參數設定為`false`，方法只會移除指定路徑中的單一專案。</span><span class="sxs-lookup"><span data-stu-id="35064-242">If the parameter is set to `false`, the method removes only a single item at the specified path.</span></span>

<span data-ttu-id="35064-243">此提供者不支援移除專案。</span><span class="sxs-lookup"><span data-stu-id="35064-243">This provider does not support item removal.</span></span> <span data-ttu-id="35064-244">不過，下列程式碼是[ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="35064-244">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a><span data-ttu-id="35064-245">執行 RemoveItem 的相關事項</span><span class="sxs-lookup"><span data-stu-id="35064-245">Things to Remember About Implementing RemoveItem</span></span>

<span data-ttu-id="35064-246">下列條件可能適用于您的[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="35064-246">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span></span>

- <span data-ttu-id="35064-247">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="35064-247">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="35064-248">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="35064-248">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="35064-249">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="35064-249">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="35064-250">根據預設，除非[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 true，否則此方法的覆寫不應移除物件。</span><span class="sxs-lookup"><span data-stu-id="35064-250">By default, overrides of this method should not remove objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to true.</span></span> <span data-ttu-id="35064-251">如果指定的路徑指出容器，則不需要[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。」</span><span class="sxs-lookup"><span data-stu-id="35064-251">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="35064-252">您的[ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)會負責防止無限遞迴（如有迴圈連結），以及 like。</span><span class="sxs-lookup"><span data-stu-id="35064-252">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="35064-253">應擲回適當的終止例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="35064-253">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

- <span data-ttu-id="35064-254">您的[ContainerCmdletprovider Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法應會呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並先檢查其傳回值，然後才會進行此程式對資料存放區進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="35064-254">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="35064-255">在呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) `true`後傳回後， [ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法應該會呼叫[，而該程式會傳回Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法，做為潛在危險系統修改的額外檢查。</span><span class="sxs-lookup"><span data-stu-id="35064-255">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a><span data-ttu-id="35064-256">將動態參數附加至 Remove 專案 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35064-256">Attaching Dynamic Parameters to the Remove-Item Cmdlet</span></span>

<span data-ttu-id="35064-257">有時， `Remove-Item`此 Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="35064-257">Sometimes the `Remove-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="35064-258">若要提供這些動態參數，容器提供者必須執行[ContainerCmdletprovider. Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="35064-258">To provide these dynamic parameters, the container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="35064-259">這個方法會在指定的路徑中抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或 Runtimedefinedparameterdictionary 類似的剖析屬性[。](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="35064-259">This method retrieves the dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="35064-260">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至`Remove-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35064-260">The Windows PowerShell runtime uses the returned object to add the parameters to the `Remove-Item` cmdlet.</span></span>

<span data-ttu-id="35064-261">此容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="35064-261">This container provider does not implement this method.</span></span> <span data-ttu-id="35064-262">不過，下列程式碼是[ContainerCmdletprovider. Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="35064-262">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a><span data-ttu-id="35064-263">查詢子專案</span><span class="sxs-lookup"><span data-stu-id="35064-263">Querying for Child Items</span></span>

<span data-ttu-id="35064-264">若要查看子專案是否存在於指定的路徑，Windows PowerShell 容器提供者必須覆寫[ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。</span><span class="sxs-lookup"><span data-stu-id="35064-264">To check to see if child items exist at the specified path, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method.</span></span> <span data-ttu-id="35064-265">`true`如果專案具有子系`false` ，則這個方法會傳回，否則會傳回。</span><span class="sxs-lookup"><span data-stu-id="35064-265">This method returns `true` if the item has children, and `false` otherwise.</span></span> <span data-ttu-id="35064-266">如果是 null 或空的路徑，方法會將資料存放區中的任何專案視為子系`true`，並傳回。</span><span class="sxs-lookup"><span data-stu-id="35064-266">For a null or empty path, the method considers any items in the data store to be children and returns `true`.</span></span>

<span data-ttu-id="35064-267">以下是[ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法的覆寫：。</span><span class="sxs-lookup"><span data-stu-id="35064-267">Here is the override for the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method.</span></span> <span data-ttu-id="35064-268">如果 ChunkPath helper 方法建立兩個以上的路徑部分，此方法`false`會傳回，因為只會定義資料庫容器和資料表容器。</span><span class="sxs-lookup"><span data-stu-id="35064-268">If there are more than two path parts created by the ChunkPath helper method, the method returns `false`, since only a database container and a table container are defined.</span></span> <span data-ttu-id="35064-269">如需此協助程式方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)中所討論的 ChunkPath 方法。</span><span class="sxs-lookup"><span data-stu-id="35064-269">For more information about this helper method, see the ChunkPath method is discussed in [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a><span data-ttu-id="35064-270">執行 HasChildItems 的相關事項</span><span class="sxs-lookup"><span data-stu-id="35064-270">Things to Remember About Implementing HasChildItems</span></span>

<span data-ttu-id="35064-271">下列條件可能適用于您的[ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="35064-271">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):</span></span>

- <span data-ttu-id="35064-272">如果容器提供者公開包含有趣掛接點的根，則`true`當 null 或時， [ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法的執行應該會傳回為路徑傳入空字串。</span><span class="sxs-lookup"><span data-stu-id="35064-272">If the container provider exposes a root that contains interesting mount points, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method should return `true` when a null or an empty string is passed in for the path.</span></span>

## <a name="copying-items"></a><span data-ttu-id="35064-273">複製專案</span><span class="sxs-lookup"><span data-stu-id="35064-273">Copying Items</span></span>

<span data-ttu-id="35064-274">若要複製專案，容器提供者必須執行[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以支援來自 Cmdlet 的`Copy-Item`呼叫。</span><span class="sxs-lookup"><span data-stu-id="35064-274">To copy items, the container provider must implement the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to support calls from the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="35064-275">這個方法會將資料項目從 Cmdlet 的`path`參數所指示的位置複製到`copyPath`參數所指示的位置。</span><span class="sxs-lookup"><span data-stu-id="35064-275">This method copies a data item from the location indicated by the `path` parameter of the cmdlet to the location indicated by the `copyPath` parameter.</span></span> <span data-ttu-id="35064-276">如果指定`recurse`參數，方法會複製所有子容器。</span><span class="sxs-lookup"><span data-stu-id="35064-276">If the `recurse` parameter is specified, the method copies all sub-containers.</span></span> <span data-ttu-id="35064-277">如果未指定參數，方法只會複製單一層級的專案。</span><span class="sxs-lookup"><span data-stu-id="35064-277">If the parameter is not specified, the method copies only a single level of items.</span></span>

<span data-ttu-id="35064-278">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="35064-278">This provider does not implement this method.</span></span> <span data-ttu-id="35064-279">不過，下列程式碼是[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="35064-279">However, the following code is the default implementation of [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a><span data-ttu-id="35064-280">執行 CopyItem 的相關事項</span><span class="sxs-lookup"><span data-stu-id="35064-280">Things to Remember About Implementing CopyItem</span></span>

<span data-ttu-id="35064-281">下列條件可能適用于您的[ContainerCmdletProvider. CopyItem 的程式](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)：</span><span class="sxs-lookup"><span data-stu-id="35064-281">The following conditions may apply to your implementation of [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):</span></span>

- <span data-ttu-id="35064-282">定義 provider 類別時，Windows PowerShell 容器提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="35064-282">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="35064-283">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的執行必須確保傳遞至方法的路徑符合指定功能的需求。」的方式。</span><span class="sxs-lookup"><span data-stu-id="35064-283">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="35064-284">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="35064-284">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="35064-285">根據預設，除非[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`，否則此方法的覆寫不應複製現有物件的物件。</span><span class="sxs-lookup"><span data-stu-id="35064-285">By default, overrides of this method should not copy objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="35064-286">例如，FileSystem 提供者不會將 c:\temp\abc.txt 複製到現有的 c:\abc.txt 檔，除非將[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="35064-286">For example, the FileSystem provider will not copy c:\temp\abc.txt over an existing c:\abc.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="35064-287">如果`copyPath`參數中指定的路徑存在，並指出容器，則不需要[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。</span><span class="sxs-lookup"><span data-stu-id="35064-287">If the path specified in the `copyPath` parameter exists and indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="35064-288">在此情況下， [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)會將`path`參數所指示的專案複製到`copyPath`參數所指示的容器，做為子系。</span><span class="sxs-lookup"><span data-stu-id="35064-288">In this case, [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) should copy the item indicated by the `path` parameter to the container indicated by the `copyPath` parameter as a child.</span></span>

- <span data-ttu-id="35064-289">您的[ContainerCmdletProvider。 CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)會負責在有迴圈連結時防止無限遞迴，而且也會發生類似的情況。</span><span class="sxs-lookup"><span data-stu-id="35064-289">Your implementation of [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="35064-290">應擲回適當的終止例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="35064-290">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

- <span data-ttu-id="35064-291">您的[ContainerCmdletProvider CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法應會呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並先檢查其傳回值，然後才會執行此程式對資料存放區進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="35064-291">Your implementation of the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="35064-292">在 Cmdletprovider 的呼叫之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true，然後， [ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法應該會呼叫[（）。Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法，做為潛在危險系統修改的額外檢查。</span><span class="sxs-lookup"><span data-stu-id="35064-292">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns true, the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span> <span data-ttu-id="35064-293">如需呼叫這些方法的詳細資訊，請參閱[重新命名專案](#renaming-items)。</span><span class="sxs-lookup"><span data-stu-id="35064-293">For more information about calling these methods, see [Rename Items](#renaming-items).</span></span>

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a><span data-ttu-id="35064-294">將動態參數附加至複製-Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35064-294">Attaching Dynamic Parameters to the Copy-Item Cmdlet</span></span>

<span data-ttu-id="35064-295">有時， `Copy-Item`此 Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="35064-295">Sometimes the `Copy-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="35064-296">若要提供這些動態參數，Windows PowerShell 容器提供者必須執行[ContainerCmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="35064-296">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="35064-297">這個方法會在指定的路徑中抓取專案的參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或 Runtimedefinedparameterdictionary 類似的剖析屬性[。](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)目標.</span><span class="sxs-lookup"><span data-stu-id="35064-297">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="35064-298">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至`Copy-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35064-298">The Windows PowerShell runtime uses the returned object to add the parameters to the `Copy-Item` cmdlet.</span></span>

<span data-ttu-id="35064-299">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="35064-299">This provider does not implement this method.</span></span> <span data-ttu-id="35064-300">不過，下列程式碼是[ContainerCmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="35064-300">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a><span data-ttu-id="35064-301">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="35064-301">Code Sample</span></span>

<span data-ttu-id="35064-302">如需完整的範例程式碼，請參閱[AccessDbProviderSample04 程式碼範例](./accessdbprovidersample04-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="35064-302">For complete sample code, see [AccessDbProviderSample04 Code Sample](./accessdbprovidersample04-code-sample.md).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="35064-303">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="35064-303">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="35064-304">請參閱[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="35064-304">See [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="35064-305">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="35064-305">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="35064-306">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="35064-306">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="35064-307">請注意，下列範例輸出會使用虛構的 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="35064-307">Be aware that the following example output uses a fictitious Access database.</span></span>

1. <span data-ttu-id="35064-308">`Get-ChildItem`執行 Cmdlet，從 Access 資料庫的 Customers 資料表中取出子專案的清單。</span><span class="sxs-lookup"><span data-stu-id="35064-308">Run the `Get-ChildItem` cmdlet to retrieve the list of child items from a Customers table in the Access database.</span></span>

   ```powershell
   Get-ChildItem mydb:customers
   ```

   <span data-ttu-id="35064-309">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="35064-309">The following output appears.</span></span>

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

2. <span data-ttu-id="35064-310">再次執行`Get-ChildItem` Cmdlet 以取得資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="35064-310">Run the `Get-ChildItem` cmdlet again to retrieve the data of a table.</span></span>

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   <span data-ttu-id="35064-311">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="35064-311">The following output appears.</span></span>

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. <span data-ttu-id="35064-312">現在，使用`Get-Item` Cmdlet 來抓取資料表中第0列的專案。</span><span class="sxs-lookup"><span data-stu-id="35064-312">Now use the `Get-Item` cmdlet to retrieve the items at row 0 in the data table.</span></span>

   ```powershell
   Get-Item mydb:\customers\0
   ```

   <span data-ttu-id="35064-313">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="35064-313">The following output appears.</span></span>

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. <span data-ttu-id="35064-314">重複`Get-Item`使用，以取得資料列0中的專案資料。</span><span class="sxs-lookup"><span data-stu-id="35064-314">Reuse `Get-Item` to retrieve the data for the items in row 0.</span></span>

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   <span data-ttu-id="35064-315">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="35064-315">The following output appears.</span></span>

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

5. <span data-ttu-id="35064-316">現在使用`New-Item` Cmdlet 將資料列加入至現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="35064-316">Now use the `New-Item` cmdlet to add a row to an existing table.</span></span> <span data-ttu-id="35064-317">`Path`參數會指定資料列的完整路徑，而且必須指出大於資料表中現有資料列數目的資料列編號。</span><span class="sxs-lookup"><span data-stu-id="35064-317">The `Path` parameter specifies the full path to the row, and must indicate a row number that is greater than the existing number of rows in the table.</span></span> <span data-ttu-id="35064-318">`Type`參數會指出 "row"，以指定要加入的專案類型。</span><span class="sxs-lookup"><span data-stu-id="35064-318">The `Type` parameter indicates "row" to specify that type of item to add.</span></span> <span data-ttu-id="35064-319">最後， `Value`參數會為數據列指定以逗號分隔的資料行值清單。</span><span class="sxs-lookup"><span data-stu-id="35064-319">Finally, the `Value` parameter specifies a comma-delimited list of column values for the row.</span></span>

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. <span data-ttu-id="35064-320">確認新專案作業的正確性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="35064-320">Verify the correctness of the new item operation as follows.</span></span>

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   <span data-ttu-id="35064-321">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="35064-321">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="35064-322">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35064-322">See Also</span></span>

[<span data-ttu-id="35064-323">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="35064-323">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="35064-324">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="35064-324">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="35064-325">執行 Windows PowerShell 提供者專案</span><span class="sxs-lookup"><span data-stu-id="35064-325">Implementing an Item Windows PowerShell Provider</span></span>](./creating-a-windows-powershell-item-provider.md)

[<span data-ttu-id="35064-326">執行流覽 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="35064-326">Implementing a Navigation Windows PowerShell Provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

[<span data-ttu-id="35064-327">如何註冊 Cmdlet、提供者和主機應用程式</span><span class="sxs-lookup"><span data-stu-id="35064-327">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="35064-328">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="35064-328">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="35064-329">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="35064-329">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)