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
# <a name="creating-a-windows-powershell-container-provider"></a><span data-ttu-id="4716a-103">建立 Windows PowerShell 容器提供者</span><span class="sxs-lookup"><span data-stu-id="4716a-103">Creating a Windows PowerShell Container Provider</span></span>

<span data-ttu-id="4716a-104">本主題說明如何建立可在多層式資料存放區上運作的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="4716a-104">This topic describes how to create a Windows PowerShell provider that can work on multi-layer data stores.</span></span> <span data-ttu-id="4716a-105">對於這種類型的資料存放區，存放區的最上層包含根專案，而且每個後續層級稱為子專案的節點。</span><span class="sxs-lookup"><span data-stu-id="4716a-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="4716a-106">藉由允許使用者在這些子節點上工作，使用者就可以透過資料存放區以階層方式進行互動。</span><span class="sxs-lookup"><span data-stu-id="4716a-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

<span data-ttu-id="4716a-107">可在多層級資料存放區上運作的提供者稱為 Windows PowerShell 的容器提供者。</span><span class="sxs-lookup"><span data-stu-id="4716a-107">Providers that can work on multi-level data stores are referred to as Windows PowerShell container providers.</span></span> <span data-ttu-id="4716a-108">不過，請注意，只有當有一個容器 () 的專案中沒有任何嵌套容器時，才可以使用 Windows PowerShell 的容器提供者。</span><span class="sxs-lookup"><span data-stu-id="4716a-108">However, be aware that a Windows PowerShell container provider can be used only when there is one container (no nested containers) with items in it.</span></span> <span data-ttu-id="4716a-109">如果有嵌套的容器，則您必須執行 Windows PowerShell 的流覽提供者。</span><span class="sxs-lookup"><span data-stu-id="4716a-109">If there are nested containers, then you must implement a Windows PowerShell navigation provider.</span></span> <span data-ttu-id="4716a-110">如需有關如何執行 Windows PowerShell 流覽提供者的詳細資訊，請參閱 [建立 Windows PowerShell 流覽提供者](./creating-a-windows-powershell-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4716a-110">For more information about implementing Windows PowerShell navigation provider, see [Creating a Windows PowerShell Navigation Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4716a-111">您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此提供者的 c # 原始程式檔 (AccessDBSampleProvider04.cs) 。</span><span class="sxs-lookup"><span data-stu-id="4716a-111">You can download the C# source file (AccessDBSampleProvider04.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4716a-112">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="4716a-112">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="4716a-113">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="4716a-113">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="4716a-114">如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4716a-114">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="4716a-115">此處所述的 Windows PowerShell 容器提供者將資料庫定義為其單一容器，並將資料庫的資料表和資料列定義為容器的專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-115">The Windows PowerShell container provider described here defines the database as its single container, with the tables and rows of the database defined as items of the container.</span></span>

> [!CAUTION]
> <span data-ttu-id="4716a-116">請注意，此設計假設有一個具有名稱識別碼之欄位的資料庫，以及欄位的類型為 LongInteger。</span><span class="sxs-lookup"><span data-stu-id="4716a-116">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

## <a name="defining-a-windows-powershell-container-provider-class"></a><span data-ttu-id="4716a-117">定義 Windows PowerShell 的容器提供者類別</span><span class="sxs-lookup"><span data-stu-id="4716a-117">Defining a Windows PowerShell Container Provider Class</span></span>

<span data-ttu-id="4716a-118">Windows PowerShell 的容器提供者必須定義一個衍生自 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 基類的 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="4716a-118">A Windows PowerShell container provider must define a .NET class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="4716a-119">以下是本節所述 Windows PowerShell 容器提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="4716a-119">Here is the class definition for the Windows PowerShell container provider described in this section.</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
public class AccessDBProvider : ContainerCmdletProvider
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="34-35":::

<span data-ttu-id="4716a-120">請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="4716a-120">Notice that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="4716a-121">第一個參數會指定 Windows PowerShell 所使用之提供者的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="4716a-121">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="4716a-122">第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="4716a-122">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="4716a-123">對於此提供者，不會新增 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="4716a-123">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="4716a-124">定義基底功能</span><span class="sxs-lookup"><span data-stu-id="4716a-124">Defining Base Functionality</span></span>

<span data-ttu-id="4716a-125">如 [設計您的 Windows PowerShell 提供](./designing-your-windows-powershell-provider.md)者所述， [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別衍生自數個提供不同提供者功能的其他類別。</span><span class="sxs-lookup"><span data-stu-id="4716a-125">As described in [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="4716a-126">因此，Windows PowerShell 的容器提供者需要定義這些類別所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="4716a-126">A Windows PowerShell container provider, therefore, needs to define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="4716a-127">若要執行新增會話特定初始化資訊，以及釋出提供者所使用之資源的功能，請參閱 [建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4716a-127">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="4716a-128">不過，大部分的提供者 (包括此處所述的提供者) 可以使用 Windows PowerShell 所提供的這項功能的預設執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-128">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="4716a-129">若要取得資料存放區的存取權，提供者必須執行 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 基類的方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-129">To get access to the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="4716a-130">如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4716a-130">For more information about implementing these methods, see [Creating an Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="4716a-131">若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-131">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="4716a-132">如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4716a-132">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

## <a name="retrieving-child-items"></a><span data-ttu-id="4716a-133">正在抓取子專案</span><span class="sxs-lookup"><span data-stu-id="4716a-133">Retrieving Child Items</span></span>

<span data-ttu-id="4716a-134">若要取出子專案，Windows PowerShell 的容器提供者必須覆寫 [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法，以支援來自 Cmdlet 的呼叫 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-134">To retrieve a child item, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to support calls from the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="4716a-135">這個方法會從資料存放區中抓取子專案，並將它們以物件的形式寫入管線。</span><span class="sxs-lookup"><span data-stu-id="4716a-135">This method retrieves child items from the data store and writes them to the pipeline as objects.</span></span> <span data-ttu-id="4716a-136">如果 `recurse` 指定了 Cmdlet 的參數，此方法就會抓取所有子系，而不論其所在層級為何。</span><span class="sxs-lookup"><span data-stu-id="4716a-136">If the `recurse` parameter of the cmdlet is specified, the method retrieves all children regardless of what level they are at.</span></span> <span data-ttu-id="4716a-137">如果 `recurse` 未指定參數，方法只會抓取單一的子系層級。</span><span class="sxs-lookup"><span data-stu-id="4716a-137">If the `recurse` parameter is not specified, the method retrieves only a single level of children.</span></span>

<span data-ttu-id="4716a-138">以下是此提供者的 [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行方式。</span><span class="sxs-lookup"><span data-stu-id="4716a-138">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method for this provider.</span></span> <span data-ttu-id="4716a-139">請注意，當路徑指出 Access 資料庫時，這個方法會抓取所有資料庫資料表中的子專案，並在路徑指出資料表時，從該資料表的資料列中抓取子專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-139">Notice that this method retrieves the child items in all database tables when the path indicates the Access database, and retrieves the child items from the rows of that table if the path indicates a data table.</span></span>

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

#### <a name="things-to-remember-about-implementing-getchilditems"></a><span data-ttu-id="4716a-140">執行 GetChildItems 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4716a-140">Things to Remember About Implementing GetChildItems</span></span>

<span data-ttu-id="4716a-141">下列情況可能適用于您的 [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行：</span><span class="sxs-lookup"><span data-stu-id="4716a-141">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span></span>

- <span data-ttu-id="4716a-142">定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="4716a-142">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4716a-143">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」</span><span class="sxs-lookup"><span data-stu-id="4716a-143">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4716a-144">若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include \* properties. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 \* 屬性）。</span><span class="sxs-lookup"><span data-stu-id="4716a-144">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="4716a-145">此方法的執行應該將任何形式的存取權考慮到可能讓使用者看見專案的專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-145">The implementation of this method should take into account any form of access to the item that might make the item visible to the user.</span></span> <span data-ttu-id="4716a-146">例如，如果使用者透過檔案系統提供者來寫入檔案的寫入權限 (由 Windows PowerShell) 提供，但無法讀取存取權，則該檔案仍然存在，而且 [system.management.automation.provider.itemCmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 會傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-146">For example, if a user has write access to a file through the FileSystem provider (supplied by Windows PowerShell), but not read access, the file still exists and [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) returns `true`.</span></span> <span data-ttu-id="4716a-147">您的執行可能需要檢查父項目，才能查看是否可以列舉子系。</span><span class="sxs-lookup"><span data-stu-id="4716a-147">Your implementation might require the checking of a parent item to see if the child can be enumerated.</span></span>

- <span data-ttu-id="4716a-148">撰寫多個專案時， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="4716a-148">When writing multiple items, the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method can take some time.</span></span> <span data-ttu-id="4716a-149">您可以設計提供者，一次使用一個 [Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 方法來撰寫專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-149">You can design your provider to write the items using the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method one at a time.</span></span> <span data-ttu-id="4716a-150">使用這項技術會向使用者呈現資料流程中的專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-150">Using this technique will present the items to the user in a stream.</span></span>

- <span data-ttu-id="4716a-151">當有迴圈連結時，您的 ContainerCmdletprovider 會負責防止無限遞迴，例如，您的 [系統管理](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 。</span><span class="sxs-lookup"><span data-stu-id="4716a-151">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="4716a-152">應擲回適當的終止例外狀況，以反映這類情況。</span><span class="sxs-lookup"><span data-stu-id="4716a-152">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a><span data-ttu-id="4716a-153">將動態參數附加至 Get-ChildItem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4716a-153">Attaching Dynamic Parameters to the Get-ChildItem Cmdlet</span></span>

<span data-ttu-id="4716a-154">有時候， `Get-ChildItem` 呼叫 ContainerCmdletprovider 的 Cmdlet 會需要在執行時間動態指定的其他參數（ [Provider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ）。</span><span class="sxs-lookup"><span data-stu-id="4716a-154">Sometimes the `Get-ChildItem` cmdlet that calls [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4716a-155">若要提供這些動態參數，Windows PowerShell 的容器提供者必須執行 [ContainerCmdletprovider. Getchilditemsdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-155">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) method.</span></span> <span data-ttu-id="4716a-156">這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。</span><span class="sxs-lookup"><span data-stu-id="4716a-156">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4716a-157">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4716a-157">The Windows PowerShell runtime uses the returned object to add the parameters to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="4716a-158">此 Windows PowerShell 容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-158">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="4716a-159">但是，下列程式碼是此方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-159">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a><span data-ttu-id="4716a-160">正在抓取子專案名稱</span><span class="sxs-lookup"><span data-stu-id="4716a-160">Retrieving Child Item Names</span></span>

<span data-ttu-id="4716a-161">若要抓取子專案的名稱，Windows PowerShell 的容器提供者必須覆寫 [ContainerCmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 方法，以便 `Get-ChildItem` 在指定參數時支援來自 Cmdlet 的呼叫 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-161">To retrieve the names of child items, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to support calls from the `Get-ChildItem` cmdlet when its `Name` parameter is specified.</span></span> <span data-ttu-id="4716a-162">如果指定了 Cmdlet 的參數，這個方法會抓取所有容器之指定路徑或子專案名稱的子專案名稱 `returnAllContainers` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-162">This method retrieves the names of the child items for the specified path or child item names for all containers if the `returnAllContainers` parameter of the cmdlet is specified.</span></span> <span data-ttu-id="4716a-163">子系名稱是路徑的分葉部分。</span><span class="sxs-lookup"><span data-stu-id="4716a-163">A child name is the leaf portion of a path.</span></span> <span data-ttu-id="4716a-164">例如，路徑 c:\windows\system32\abc.dll 的子名稱為 "abc.dll"。</span><span class="sxs-lookup"><span data-stu-id="4716a-164">For example, the child name for the path c:\windows\system32\abc.dll is "abc.dll".</span></span> <span data-ttu-id="4716a-165">目錄 c:\windows\system32 的子名稱為 "system32"。</span><span class="sxs-lookup"><span data-stu-id="4716a-165">The child name for the directory c:\windows\system32 is "system32".</span></span>

<span data-ttu-id="4716a-166">以下是此提供者的 [ContainerCmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 方法的執行方式。</span><span class="sxs-lookup"><span data-stu-id="4716a-166">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method for this provider.</span></span> <span data-ttu-id="4716a-167">請注意，如果指定的路徑指出 Access 資料庫 (磁片磁碟機) 和資料列編號（如果路徑指出資料表），此方法就會抓取資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="4716a-167">Notice that the method retrieves table names if the specified path indicates the Access database (drive) and row numbers if the path indicates a table.</span></span>

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

#### <a name="things-to-remember-about-implementing-getchildnames"></a><span data-ttu-id="4716a-168">執行 GetChildNames 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4716a-168">Things to Remember About Implementing GetChildNames</span></span>

<span data-ttu-id="4716a-169">下列情況可能適用于您的 [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的執行：</span><span class="sxs-lookup"><span data-stu-id="4716a-169">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span></span>

- <span data-ttu-id="4716a-170">定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="4716a-170">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4716a-171">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」</span><span class="sxs-lookup"><span data-stu-id="4716a-171">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4716a-172">若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include \* properties. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 \* 屬性）。</span><span class="sxs-lookup"><span data-stu-id="4716a-172">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4716a-173">指定 Cmdlet 的參數時，就會發生此規則的例外狀況 `returnAllContainers` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-173">An exception to this rule occurs when the `returnAllContainers` parameter of the cmdlet is specified.</span></span> <span data-ttu-id="4716a-174">在此情況下，此方法應該會取出容器的任何子系名稱，即使它不符合[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter)的值也是一樣。 [Cmdletprovider.. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)或[Cmdletprovider..... Exclude \* properties..](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)</span><span class="sxs-lookup"><span data-stu-id="4716a-174">In this case, the method should retrieve any child name for a container, even if it does not match the values of the [System.Management.Automation.Provider.Cmdletprovider.Filter\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), or [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) properties.</span></span>

- <span data-ttu-id="4716a-175">根據預設，除非指定 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性，否則這個方法的覆寫不應抓取使用者通常會隱藏的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="4716a-175">By default, overrides of this method should not retrieve names of objects that are generally hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is specified.</span></span> <span data-ttu-id="4716a-176">如果指定的路徑指出容器，則不需要 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。」</span><span class="sxs-lookup"><span data-stu-id="4716a-176">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="4716a-177">當有迴圈連結時，您的 ContainerCmdletprovider 會負責防止無限遞迴，例如，您的 [系統管理](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 。</span><span class="sxs-lookup"><span data-stu-id="4716a-177">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="4716a-178">應擲回適當的終止例外狀況，以反映這類情況。</span><span class="sxs-lookup"><span data-stu-id="4716a-178">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a><span data-ttu-id="4716a-179">將動態參數附加至 Get-ChildItem Cmdlet (名稱) </span><span class="sxs-lookup"><span data-stu-id="4716a-179">Attaching Dynamic Parameters to the Get-ChildItem Cmdlet (Name)</span></span>

<span data-ttu-id="4716a-180">有時 `Get-ChildItem` Cmdlet (與 `Name` 參數) 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4716a-180">Sometimes the `Get-ChildItem` cmdlet (with the `Name` parameter) requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4716a-181">若要提供這些動態參數，Windows PowerShell 的容器提供者必須執行 [ContainerCmdletprovider. Getchildnamesdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-181">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) method.</span></span> <span data-ttu-id="4716a-182">這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件的屬性和欄位具有類似 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="4716a-182">This method retrieves the dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4716a-183">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4716a-183">The Windows PowerShell runtime uses the returned object to add the parameters to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="4716a-184">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-184">This provider does not implement this method.</span></span> <span data-ttu-id="4716a-185">但是，下列程式碼是此方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-185">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a><span data-ttu-id="4716a-186">重新命名專案</span><span class="sxs-lookup"><span data-stu-id="4716a-186">Renaming Items</span></span>

<span data-ttu-id="4716a-187">若要重新命名專案，Windows PowerShell 的容器提供者必須覆寫 [ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 方法，以支援來自 Cmdlet 的呼叫 `Rename-Item` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-187">To rename an item, a Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method to support calls from the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="4716a-188">這個方法會將指定路徑的專案名稱變更為提供的新名稱。</span><span class="sxs-lookup"><span data-stu-id="4716a-188">This method changes the name of the item at the specified path to the new name provided.</span></span> <span data-ttu-id="4716a-189">新名稱必須一律相對於父代 (container) 的專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-189">The new name must always be relative to the parent item (container).</span></span>

<span data-ttu-id="4716a-190">此提供者不會覆寫 [ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-190">This provider does not override the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method.</span></span> <span data-ttu-id="4716a-191">但是，下列是預設的執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-191">However, the following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a><span data-ttu-id="4716a-192">執行 RenameItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4716a-192">Things to Remember About Implementing RenameItem</span></span>

<span data-ttu-id="4716a-193">下列情況可能適用于您的 [ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)的執行：</span><span class="sxs-lookup"><span data-stu-id="4716a-193">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):</span></span>

- <span data-ttu-id="4716a-194">定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="4716a-194">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4716a-195">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」</span><span class="sxs-lookup"><span data-stu-id="4716a-195">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4716a-196">若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include \* properties. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 \* 屬性）。</span><span class="sxs-lookup"><span data-stu-id="4716a-196">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="4716a-197">[ContainerCmdletprovider. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法僅適用于修改專案的名稱，而不是用於移動作業的專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-197">The [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method is intended for the modification of the name of an item only, and not for move operations.</span></span>
  <span data-ttu-id="4716a-198">如果 `newName` 參數包含路徑分隔符號，或可能導致專案變更其父位置，則您的方法的執行應該會寫入錯誤。</span><span class="sxs-lookup"><span data-stu-id="4716a-198">Your implementation of the method should write an error if the `newName` parameter contains path separators, or might otherwise cause the item to change its parent location.</span></span>

- <span data-ttu-id="4716a-199">根據預設，除非指定 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性，否則這個方法的覆寫不應重新命名物件。</span><span class="sxs-lookup"><span data-stu-id="4716a-199">By default, overrides of this method should not rename objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is specified.</span></span> <span data-ttu-id="4716a-200">如果指定的路徑指出容器，則不需要 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。」</span><span class="sxs-lookup"><span data-stu-id="4716a-200">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="4716a-201">您的 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-201">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="4716a-202">當對系統狀態進行變更（例如重新命名檔案）時，會使用這個方法來確認作業的執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-202">This method is used to confirm execution of an operation when a change is made to system state, for example, renaming files.</span></span>
  <span data-ttu-id="4716a-203">[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會傳送要變更給使用者的資源名稱，且 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入考慮，以決定應顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="4716a-203">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="4716a-204">呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) `true` 會傳回， [ContainerCmdletprovider.. Renameitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 方法應該呼叫 [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ，以呼叫 system.object.. \* 方法來呼叫. 管理方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-204">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="4716a-205">這個方法會將確認訊息傳送給使用者，以允許額外的意見反應來指出作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="4716a-205">This method sends a message a confirmation message to the user to allow additional feedback to say if the operation should be continued.</span></span> <span data-ttu-id="4716a-206">提供者應該呼叫 [Cmdletprovider ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 做為額外的檢查，以進行可能有危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="4716a-206">A provider should call [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a><span data-ttu-id="4716a-207">將動態參數附加至 Rename-Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4716a-207">Attaching Dynamic Parameters to the Rename-Item Cmdlet</span></span>

<span data-ttu-id="4716a-208">有時 `Rename-Item` Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4716a-208">Sometimes the `Rename-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4716a-209">若要提供這些動態參數，Windows PowerShell 容器提供者必須執行 [ContainerCmdletprovider. Renameitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-209">To provide these dynamic parameters, Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span> <span data-ttu-id="4716a-210">這個方法會在指定的路徑上抓取專案的參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。</span><span class="sxs-lookup"><span data-stu-id="4716a-210">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4716a-211">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Rename-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4716a-211">The Windows PowerShell runtime uses the returned object to add the parameters to the `Rename-Item` cmdlet.</span></span>

<span data-ttu-id="4716a-212">此容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-212">This container provider does not implement this method.</span></span> <span data-ttu-id="4716a-213">但是，下列程式碼是此方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-213">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a><span data-ttu-id="4716a-214">建立新專案</span><span class="sxs-lookup"><span data-stu-id="4716a-214">Creating New Items</span></span>

<span data-ttu-id="4716a-215">若要建立新的專案，容器提供者必須執行 [ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法，以支援來自 Cmdlet 的呼叫 `New-Item` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-215">To create new items, a container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to support calls from the `New-Item` cmdlet.</span></span> <span data-ttu-id="4716a-216">這個方法會建立位於指定路徑的資料項目。</span><span class="sxs-lookup"><span data-stu-id="4716a-216">This method creates a data item located at the specified path.</span></span> <span data-ttu-id="4716a-217">`type`Cmdlet 的參數包含新專案的提供者定義型別。</span><span class="sxs-lookup"><span data-stu-id="4716a-217">The `type` parameter of the cmdlet contains the provider-defined type for the new item.</span></span> <span data-ttu-id="4716a-218">例如，FileSystem 提供者會使用 `type` 值為 "file" 或 "directory" 的參數。</span><span class="sxs-lookup"><span data-stu-id="4716a-218">For example, the FileSystem provider uses a `type` parameter with a value of "file" or "directory".</span></span> <span data-ttu-id="4716a-219">`newItemValue`Cmdlet 的參數會指定新專案的提供者特定值。</span><span class="sxs-lookup"><span data-stu-id="4716a-219">The `newItemValue` parameter of the cmdlet specifies a provider-specific value for the new item.</span></span>

<span data-ttu-id="4716a-220">以下是此提供者的 [ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法的執行方式。</span><span class="sxs-lookup"><span data-stu-id="4716a-220">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method for this provider.</span></span>

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

#### <a name="things-to-remember-about-implementing-newitem"></a><span data-ttu-id="4716a-221">執行 NewItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4716a-221">Things to Remember About Implementing NewItem</span></span>

<span data-ttu-id="4716a-222">下列情況可能適用于您的 [ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行：</span><span class="sxs-lookup"><span data-stu-id="4716a-222">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span></span>

- <span data-ttu-id="4716a-223">[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該針對參數中所傳遞的字串，執行不區分大小寫的比較 `type` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-223">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should perform a case-insensitive comparison of the string passed in the `type` parameter.</span></span>
  <span data-ttu-id="4716a-224">它也應該允許最少不明確的相符專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-224">It should also allow for least ambiguous matches.</span></span> <span data-ttu-id="4716a-225">例如，針對 "file" 和 "directory" 類型，只需要第一個字母來區分。</span><span class="sxs-lookup"><span data-stu-id="4716a-225">For example, for the types "file" and "directory", only the first letter is required to disambiguate.</span></span> <span data-ttu-id="4716a-226">如果 `type` 參數指出您的提供者無法建立的類型，則 [ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法應該寫入 ArgumentException，並顯示訊息，指出提供者可建立的類型。</span><span class="sxs-lookup"><span data-stu-id="4716a-226">If the `type` parameter indicates a type your provider cannot create, the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should write an ArgumentException with a message indicating the types the provider can create.</span></span>

- <span data-ttu-id="4716a-227">若為 `newItemValue` 參數，建議您將 [ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法的實作為最小接受字串。</span><span class="sxs-lookup"><span data-stu-id="4716a-227">For the `newItemValue` parameter, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method is recommended to accept strings at a minimum.</span></span> <span data-ttu-id="4716a-228">此外，它也應該接受針對相同路徑， [system.management.automation.provider.itemCmdletprovider. Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 方法所抓取的物件類型。</span><span class="sxs-lookup"><span data-stu-id="4716a-228">It should also accept the type of object that is retrieved by the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method for the same path.</span></span> <span data-ttu-id="4716a-229">[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法可以使用[languageprimitives.physicalequality. Convertto \*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo)方法，將型別轉換成所需的型別（type）。</span><span class="sxs-lookup"><span data-stu-id="4716a-229">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method can use the [System.Management.Automation.Languageprimitives.Convertto\*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) method to convert types to the desired type.</span></span>

- <span data-ttu-id="4716a-230">您的 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-230">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="4716a-231">在呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會傳回 true，則 [ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法應該呼叫 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ，以做為可能有危險的系統修改的額外檢查，以進行額外的檢查，以進行檢查。</span><span class="sxs-lookup"><span data-stu-id="4716a-231">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns true, the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a><span data-ttu-id="4716a-232">將動態參數附加至 New-Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4716a-232">Attaching Dynamic Parameters to the New-Item Cmdlet</span></span>

<span data-ttu-id="4716a-233">有時 `New-Item` Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4716a-233">Sometimes the `New-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4716a-234">若要提供這些動態參數，容器提供者必須執行 [ContainerCmdletprovider. Newitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-234">To provide these dynamic parameters, the container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span> <span data-ttu-id="4716a-235">這個方法會在指定的路徑上抓取專案的參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。</span><span class="sxs-lookup"><span data-stu-id="4716a-235">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4716a-236">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `New-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4716a-236">The Windows PowerShell runtime uses the returned object to add the parameters to the `New-Item` cmdlet.</span></span>

<span data-ttu-id="4716a-237">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-237">This provider does not implement this method.</span></span> <span data-ttu-id="4716a-238">但是，下列程式碼是此方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-238">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a><span data-ttu-id="4716a-239">移除專案</span><span class="sxs-lookup"><span data-stu-id="4716a-239">Removing Items</span></span>

<span data-ttu-id="4716a-240">若要移除專案，Windows PowerShell 提供者必須覆寫 [ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 方法，以支援來自 Cmdlet 的呼叫 `Remove-Item` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-240">To remove items, the Windows PowerShell provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to support calls from the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="4716a-241">這個方法會從指定路徑的資料存放區中刪除專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-241">This method deletes an item from the data store at the specified path.</span></span> <span data-ttu-id="4716a-242">如果 `recurse` Cmdlet 的參數 `Remove-Item` 設定為 `true` ，則方法會移除所有子專案，而不論其層級為何。</span><span class="sxs-lookup"><span data-stu-id="4716a-242">If the `recurse` parameter of the `Remove-Item` cmdlet is set to `true`, the method removes all child items regardless of their level.</span></span> <span data-ttu-id="4716a-243">如果參數設定為 `false` ，方法只會移除指定路徑上的單一專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-243">If the parameter is set to `false`, the method removes only a single item at the specified path.</span></span>

<span data-ttu-id="4716a-244">此提供者不支援移除專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-244">This provider does not support item removal.</span></span> <span data-ttu-id="4716a-245">但是，下列程式碼是 [ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-245">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a><span data-ttu-id="4716a-246">執行 RemoveItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4716a-246">Things to Remember About Implementing RemoveItem</span></span>

<span data-ttu-id="4716a-247">下列情況可能適用于您的 [ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)的執行：</span><span class="sxs-lookup"><span data-stu-id="4716a-247">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span></span>

- <span data-ttu-id="4716a-248">定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="4716a-248">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4716a-249">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」</span><span class="sxs-lookup"><span data-stu-id="4716a-249">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4716a-250">若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include \* properties. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 \* 屬性）。</span><span class="sxs-lookup"><span data-stu-id="4716a-250">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="4716a-251">根據預設，除非 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為 true，否則這個方法的覆寫不應移除物件。</span><span class="sxs-lookup"><span data-stu-id="4716a-251">By default, overrides of this method should not remove objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to true.</span></span> <span data-ttu-id="4716a-252">如果指定的路徑指出容器，則不需要 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。」</span><span class="sxs-lookup"><span data-stu-id="4716a-252">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="4716a-253">當有迴圈連結時，您的 ContainerCmdletprovider 會負責防止無限遞迴，例如，您的 [系統管理](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 。</span><span class="sxs-lookup"><span data-stu-id="4716a-253">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="4716a-254">應擲回適當的終止例外狀況，以反映這類情況。</span><span class="sxs-lookup"><span data-stu-id="4716a-254">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

- <span data-ttu-id="4716a-255">您的 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-255">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="4716a-256">在呼叫 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 之後，ShouldProcess `true` 會傳回， [ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 方法應該呼叫 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 來做額外檢查，以瞭解是否有潛在危險的系統修改，並將其視為額外的檢查，以進行檢查。</span><span class="sxs-lookup"><span data-stu-id="4716a-256">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a><span data-ttu-id="4716a-257">將動態參數附加至 Remove-Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4716a-257">Attaching Dynamic Parameters to the Remove-Item Cmdlet</span></span>

<span data-ttu-id="4716a-258">有時 `Remove-Item` Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4716a-258">Sometimes the `Remove-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4716a-259">為了提供這些動態參數，容器提供者必須執行 [ContainerCmdletprovider. Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="4716a-259">To provide these dynamic parameters, the container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="4716a-260">這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件的屬性和欄位具有類似 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="4716a-260">This method retrieves the dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4716a-261">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Remove-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4716a-261">The Windows PowerShell runtime uses the returned object to add the parameters to the `Remove-Item` cmdlet.</span></span>

<span data-ttu-id="4716a-262">此容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-262">This container provider does not implement this method.</span></span> <span data-ttu-id="4716a-263">但是，下列程式碼是 [ContainerCmdletprovider. Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-263">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a><span data-ttu-id="4716a-264">查詢子專案</span><span class="sxs-lookup"><span data-stu-id="4716a-264">Querying for Child Items</span></span>

<span data-ttu-id="4716a-265">若要檢查子專案是否存在於指定的路徑，Windows PowerShell 的容器提供者必須覆寫 [ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-265">To check to see if child items exist at the specified path, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method.</span></span> <span data-ttu-id="4716a-266">如果專案有子系，則這個方法會傳回 `true` ，否則會傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-266">This method returns `true` if the item has children, and `false` otherwise.</span></span> <span data-ttu-id="4716a-267">如果是 null 或空的路徑，方法會將資料存放區中的任何專案視為子系，並傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-267">For a null or empty path, the method considers any items in the data store to be children and returns `true`.</span></span>

<span data-ttu-id="4716a-268">以下是 [ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 方法的覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-268">Here is the override for the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method.</span></span> <span data-ttu-id="4716a-269">如果 ChunkPath helper 方法建立了兩個以上的路徑部分，則方法會傳回 `false` ，因為只會定義資料庫容器和資料表容器。</span><span class="sxs-lookup"><span data-stu-id="4716a-269">If there are more than two path parts created by the ChunkPath helper method, the method returns `false`, since only a database container and a table container are defined.</span></span> <span data-ttu-id="4716a-270">如需此 helper 方法的詳細資訊，請參閱 [建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)中所討論的 ChunkPath 方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-270">For more information about this helper method, see the ChunkPath method is discussed in [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="1094-1097":::

#### <a name="things-to-remember-about-implementing-haschilditems"></a><span data-ttu-id="4716a-271">執行 HasChildItems 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4716a-271">Things to Remember About Implementing HasChildItems</span></span>

<span data-ttu-id="4716a-272">下列情況可能適用于您的 [ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)的執行：</span><span class="sxs-lookup"><span data-stu-id="4716a-272">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):</span></span>

- <span data-ttu-id="4716a-273">如果容器提供者公開包含有趣掛接點的根目錄，則在為路徑傳入 null 或空字串時，應會傳回[ContainerCmdletprovider. Haschilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法的執行。 `true`</span><span class="sxs-lookup"><span data-stu-id="4716a-273">If the container provider exposes a root that contains interesting mount points, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method should return `true` when a null or an empty string is passed in for the path.</span></span>

## <a name="copying-items"></a><span data-ttu-id="4716a-274">複製專案</span><span class="sxs-lookup"><span data-stu-id="4716a-274">Copying Items</span></span>

<span data-ttu-id="4716a-275">若要複製專案，容器提供者必須執行 [ContainerCmdletProvider CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 方法，以支援來自 Cmdlet 的呼叫 `Copy-Item` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-275">To copy items, the container provider must implement the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to support calls from the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="4716a-276">這個方法會從 Cmdlet 的參數所指定的位置，將資料項目複製 `path` 到參數所指示的位置 `copyPath` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-276">This method copies a data item from the location indicated by the `path` parameter of the cmdlet to the location indicated by the `copyPath` parameter.</span></span> <span data-ttu-id="4716a-277">如果 `recurse` 指定了參數，則方法會複製所有子容器。</span><span class="sxs-lookup"><span data-stu-id="4716a-277">If the `recurse` parameter is specified, the method copies all sub-containers.</span></span> <span data-ttu-id="4716a-278">如果未指定參數，方法只會複製單一層級的專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-278">If the parameter is not specified, the method copies only a single level of items.</span></span>

<span data-ttu-id="4716a-279">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-279">This provider does not implement this method.</span></span> <span data-ttu-id="4716a-280">但是，下列程式碼是 [ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-280">However, the following code is the default implementation of [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a><span data-ttu-id="4716a-281">執行 CopyItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4716a-281">Things to Remember About Implementing CopyItem</span></span>

<span data-ttu-id="4716a-282">下列情況可能適用于您的 [ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)的執行：</span><span class="sxs-lookup"><span data-stu-id="4716a-282">The following conditions may apply to your implementation of [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):</span></span>

- <span data-ttu-id="4716a-283">定義提供者類別時，Windows PowerShell 的容器提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="4716a-283">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4716a-284">在這些情況下， [ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法的執行必須確保傳遞給方法的路徑符合指定之功能的需求。。」</span><span class="sxs-lookup"><span data-stu-id="4716a-284">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4716a-285">若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include \* properties. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 \* 屬性）。</span><span class="sxs-lookup"><span data-stu-id="4716a-285">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="4716a-286">根據預設，除非 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則此方法的覆寫不應將物件複製到現有的物件 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-286">By default, overrides of this method should not copy objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="4716a-287">例如，FileSystem 提供者不會將 c:\temp\abc.txt 複製到現有的 c:\abc.txt 檔案，除非 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4716a-287">For example, the FileSystem provider will not copy c:\temp\abc.txt over an existing c:\abc.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="4716a-288">如果在參數中指定的路徑 `copyPath` 存在且指出容器，則不需要 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。</span><span class="sxs-lookup"><span data-stu-id="4716a-288">If the path specified in the `copyPath` parameter exists and indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="4716a-289">在此情況下， [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 會將參數所指示的專案複製 `path` 到參數所指示的容器 `copyPath` 做為子系。</span><span class="sxs-lookup"><span data-stu-id="4716a-289">In this case, [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) should copy the item indicated by the `path` parameter to the container indicated by the `copyPath` parameter as a child.</span></span>

- <span data-ttu-id="4716a-290">當有迴圈連結時，您的 ContainerCmdletProvider 會負責防止無限遞迴，例如，您的 [系統管理](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 。</span><span class="sxs-lookup"><span data-stu-id="4716a-290">Your implementation of [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="4716a-291">應擲回適當的終止例外狀況，以反映這類情況。</span><span class="sxs-lookup"><span data-stu-id="4716a-291">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

- <span data-ttu-id="4716a-292">您的 [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-292">Your implementation of the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="4716a-293">在呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會傳回 true，則 [ContainerCmdletProvider.. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 方法應該呼叫 [方法，](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 以做為可能有危險的系統修改的額外檢查，以做額外的檢查的檢查。</span><span class="sxs-lookup"><span data-stu-id="4716a-293">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns true, the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span> <span data-ttu-id="4716a-294">如需呼叫這些方法的詳細資訊，請參閱 [重新命名專案](#renaming-items)。</span><span class="sxs-lookup"><span data-stu-id="4716a-294">For more information about calling these methods, see [Rename Items](#renaming-items).</span></span>

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a><span data-ttu-id="4716a-295">將動態參數附加至 Copy-Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4716a-295">Attaching Dynamic Parameters to the Copy-Item Cmdlet</span></span>

<span data-ttu-id="4716a-296">有時 `Copy-Item` Cmdlet 需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4716a-296">Sometimes the `Copy-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4716a-297">為了提供這些動態參數，Windows PowerShell 的容器提供者必須執行 [ContainerCmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="4716a-297">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="4716a-298">這個方法會在指定的路徑上抓取專案的參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。</span><span class="sxs-lookup"><span data-stu-id="4716a-298">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4716a-299">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 `Copy-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4716a-299">The Windows PowerShell runtime uses the returned object to add the parameters to the `Copy-Item` cmdlet.</span></span>

<span data-ttu-id="4716a-300">此提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="4716a-300">This provider does not implement this method.</span></span> <span data-ttu-id="4716a-301">但是，下列程式碼是 [ContainerCmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="4716a-301">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a><span data-ttu-id="4716a-302">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4716a-302">Code Sample</span></span>

<span data-ttu-id="4716a-303">如需完整的範例程式碼，請參閱 [AccessDbProviderSample04 程式碼範例](./accessdbprovidersample04-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="4716a-303">For complete sample code, see [AccessDbProviderSample04 Code Sample](./accessdbprovidersample04-code-sample.md).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="4716a-304">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4716a-304">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="4716a-305">瞭解 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="4716a-305">See [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="4716a-306">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4716a-306">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="4716a-307">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="4716a-307">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="4716a-308">請注意，下列範例輸出會使用虛構的 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4716a-308">Be aware that the following example output uses a fictitious Access database.</span></span>

1. <span data-ttu-id="4716a-309">執行 `Get-ChildItem` Cmdlet，從 Access 資料庫的 Customers 資料表中取出子專案清單。</span><span class="sxs-lookup"><span data-stu-id="4716a-309">Run the `Get-ChildItem` cmdlet to retrieve the list of child items from a Customers table in the Access database.</span></span>

   ```powershell
   Get-ChildItem mydb:customers
   ```

   <span data-ttu-id="4716a-310">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4716a-310">The following output appears.</span></span>

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

2. <span data-ttu-id="4716a-311">再次執行 `Get-ChildItem` Cmdlet 以取出資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="4716a-311">Run the `Get-ChildItem` cmdlet again to retrieve the data of a table.</span></span>

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   <span data-ttu-id="4716a-312">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4716a-312">The following output appears.</span></span>

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. <span data-ttu-id="4716a-313">現在，使用 `Get-Item` Cmdlet 取出資料表中第0列的專案。</span><span class="sxs-lookup"><span data-stu-id="4716a-313">Now use the `Get-Item` cmdlet to retrieve the items at row 0 in the data table.</span></span>

   ```powershell
   Get-Item mydb:\customers\0
   ```

   <span data-ttu-id="4716a-314">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4716a-314">The following output appears.</span></span>

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. <span data-ttu-id="4716a-315">重複使用 `Get-Item` 以取得資料列0中專案的資料。</span><span class="sxs-lookup"><span data-stu-id="4716a-315">Reuse `Get-Item` to retrieve the data for the items in row 0.</span></span>

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   <span data-ttu-id="4716a-316">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4716a-316">The following output appears.</span></span>

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

5. <span data-ttu-id="4716a-317">現在，使用指令 `New-Item` 程式將資料列新增至現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="4716a-317">Now use the `New-Item` cmdlet to add a row to an existing table.</span></span> <span data-ttu-id="4716a-318">`Path`參數指定資料列的完整路徑，而且必須指出大於資料表中現有資料列數目的資料列編號。</span><span class="sxs-lookup"><span data-stu-id="4716a-318">The `Path` parameter specifies the full path to the row, and must indicate a row number that is greater than the existing number of rows in the table.</span></span> <span data-ttu-id="4716a-319">`Type`參數表示 "row"，以指定要加入的專案類型。</span><span class="sxs-lookup"><span data-stu-id="4716a-319">The `Type` parameter indicates "row" to specify that type of item to add.</span></span>
   <span data-ttu-id="4716a-320">最後， `Value` 參數會指定資料列的資料行值清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="4716a-320">Finally, the `Value` parameter specifies a comma-delimited list of column values for the row.</span></span>

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. <span data-ttu-id="4716a-321">確認新專案作業的正確性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="4716a-321">Verify the correctness of the new item operation as follows.</span></span>

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   <span data-ttu-id="4716a-322">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4716a-322">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4716a-323">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4716a-323">See Also</span></span>

[<span data-ttu-id="4716a-324">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4716a-324">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="4716a-325">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4716a-325">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="4716a-326">執行專案 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4716a-326">Implementing an Item Windows PowerShell Provider</span></span>](./creating-a-windows-powershell-item-provider.md)

[<span data-ttu-id="4716a-327">執行導覽 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4716a-327">Implementing a Navigation Windows PowerShell Provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

<span data-ttu-id="4716a-328">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4716a-328">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="4716a-329">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4716a-329">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="4716a-330">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="4716a-330">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
