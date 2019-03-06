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
ms.openlocfilehash: e0d83a742eae2bcde2e691860a5f2b3e5862d2de
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430025"
---
# <a name="creating-a-windows-powershell-container-provider"></a><span data-ttu-id="4f913-102">建立 Windows PowerShell 容器提供者</span><span class="sxs-lookup"><span data-stu-id="4f913-102">Creating a Windows PowerShell Container Provider</span></span>

<span data-ttu-id="4f913-103">本主題描述如何建立可在多層資料存放區的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="4f913-103">This topic describes how to create a Windows PowerShell provider that can work on multi-layer data stores.</span></span> <span data-ttu-id="4f913-104">針對此類型的資料存放區中，存放區的最上層包含根項目，以及每個後續的層級指節點的子項目。</span><span class="sxs-lookup"><span data-stu-id="4f913-104">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="4f913-105">藉由讓使用者能夠在這些子節點上運作，使用者可以階層方式透過資料存放區互動。</span><span class="sxs-lookup"><span data-stu-id="4f913-105">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

<span data-ttu-id="4f913-106">可以作用於多層級的資料存放區的提供者被指 Windows PowerShell 容器提供者。</span><span class="sxs-lookup"><span data-stu-id="4f913-106">Providers that can work on multi-level data stores are referred to as Windows PowerShell container providers.</span></span> <span data-ttu-id="4f913-107">不過，請注意一個容器 （沒有巢狀容器），在它的項目時，可以使用 Windows PowerShell 容器提供者。</span><span class="sxs-lookup"><span data-stu-id="4f913-107">However, be aware that a Windows PowerShell container provider can be used only when there is one container (no nested containers) with items in it.</span></span> <span data-ttu-id="4f913-108">如果沒有巢狀的容器，您必須實作的 Windows PowerShell 巡覽提供者。</span><span class="sxs-lookup"><span data-stu-id="4f913-108">If there are nested containers, then you must implement a Windows PowerShell navigation provider.</span></span> <span data-ttu-id="4f913-109">如需有關如何實作 Windows PowerShell 巡覽提供者的詳細資訊，請參閱[建立 Windows PowerShell 巡覽提供者](./creating-a-windows-powershell-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4f913-109">For more information about implementing Windows PowerShell navigation provider, see [Creating a Windows PowerShell Navigation Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4f913-110">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此提供者的原始程式檔 (AccessDBSampleProvider04.cs)。</span><span class="sxs-lookup"><span data-stu-id="4f913-110">You can download the C# source file (AccessDBSampleProvider04.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4f913-111">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="4f913-111">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4f913-112">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="4f913-112">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="4f913-113">如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4f913-113">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="4f913-114">此處所述的 Windows PowerShell 容器提供者會定義為單一的容器，使用資料表和資料列做為容器的項目定義之資料庫的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4f913-114">The Windows PowerShell container provider described here defines the database as its single container, with the tables and rows of the database defined as items of the container.</span></span>

> [!CAUTION]
> <span data-ttu-id="4f913-115">請注意，這項設計會假設的欄位有名稱識別碼的資料庫和欄位的型別是 LongInteger。</span><span class="sxs-lookup"><span data-stu-id="4f913-115">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

<span data-ttu-id="4f913-116">以下是本主題中的區段清單。</span><span class="sxs-lookup"><span data-stu-id="4f913-116">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="4f913-117">如果您不熟悉如何撰寫 Windows PowerShell 容器提供者，請閱讀這項資訊，它會出現的順序。</span><span class="sxs-lookup"><span data-stu-id="4f913-117">If you are unfamiliar with writing a Windows PowerShell container provider, please read this information in the order that it appears.</span></span> <span data-ttu-id="4f913-118">不過，如果您已熟悉撰寫 Windows PowerShell 容器提供者，請直接前往您所需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="4f913-118">However, if you are familiar with writing a Windows PowerShell container provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="4f913-119">定義 Windows PowerShell 容器提供者類別</span><span class="sxs-lookup"><span data-stu-id="4f913-119">Defining a Windows PowerShell Container Provider Class</span></span>](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [<span data-ttu-id="4f913-120">定義基底的功能</span><span class="sxs-lookup"><span data-stu-id="4f913-120">Defining Base Functionality</span></span>]()

- [<span data-ttu-id="4f913-121">正在擷取子系項目</span><span class="sxs-lookup"><span data-stu-id="4f913-121">Retrieving Child Items</span></span>](#Retrieving-Child-Items)

- [<span data-ttu-id="4f913-122">附加到的動態參數`Get-ChildItem`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f913-122">Attaching Dynamic Parameters to the `Get-ChildItem` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [<span data-ttu-id="4f913-123">擷取子系項目名稱</span><span class="sxs-lookup"><span data-stu-id="4f913-123">Retrieving Child Item Names</span></span>](#Retrieving-Child-Item-Names)

- <span data-ttu-id="4f913-124">[附加到的動態參數`Get-ChildItem`Cmdlet （名稱）](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))</span><span class="sxs-lookup"><span data-stu-id="4f913-124">[Attaching Dynamic Parameters to the `Get-ChildItem` Cmdlet (Name)](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))</span></span>

- [<span data-ttu-id="4f913-125">重新命名項目</span><span class="sxs-lookup"><span data-stu-id="4f913-125">Renaming Items</span></span>](#Renaming-Items)

- [<span data-ttu-id="4f913-126">附加到的動態參數`Rename-Item`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f913-126">Attaching Dynamic Parameters to the  `Rename-Item` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [<span data-ttu-id="4f913-127">建立新的項目</span><span class="sxs-lookup"><span data-stu-id="4f913-127">Creating New Items</span></span>](#Creating-New-Items)

- [<span data-ttu-id="4f913-128">附加到的動態參數`New-Item`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f913-128">Attaching Dynamic Parameters to the `New-Item` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [<span data-ttu-id="4f913-129">移除項目</span><span class="sxs-lookup"><span data-stu-id="4f913-129">Removing a Items</span></span>](#Removing-Items)

- [<span data-ttu-id="4f913-130">附加到的動態參數`Remove-Item`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f913-130">Attaching Dynamic Parameters to the `Remove-Item` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [<span data-ttu-id="4f913-131">查詢的子項目</span><span class="sxs-lookup"><span data-stu-id="4f913-131">Querying for Child Items</span></span>](#Querying-for-Child-Items)

- [<span data-ttu-id="4f913-132">複製項目</span><span class="sxs-lookup"><span data-stu-id="4f913-132">Coping Items</span></span>](#Copying-Items)

- [<span data-ttu-id="4f913-133">附加到的動態參數`Copy-Item`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f913-133">Attaching Dynamic Parameters to the  `Copy-Item` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [<span data-ttu-id="4f913-134">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4f913-134">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="4f913-135">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="4f913-135">Defining Object Types and Formatting</span></span>]()

- [<span data-ttu-id="4f913-136">建置 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4f913-136">Building the Windows PowerShell Provider</span></span>](#Building-the-Windows-PowerShell-Provider)

- [<span data-ttu-id="4f913-137">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4f913-137">Testing the Windows PowerShell Provider</span></span>](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a><span data-ttu-id="4f913-138">定義 Windows PowerShell 容器提供者類別</span><span class="sxs-lookup"><span data-stu-id="4f913-138">Defining a Windows PowerShell Container Provider Class</span></span>

<span data-ttu-id="4f913-139">Windows PowerShell 容器提供者必須定義衍生自.NET 類別[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="4f913-139">A Windows PowerShell container provider must define a .NET class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="4f913-140">以下是這一節所述的 Windows PowerShell 容器提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="4f913-140">Here is the class definition for the Windows PowerShell container provider described in this section.</span></span>

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

<span data-ttu-id="4f913-141">請注意，在此類別定義中， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-141">Notice that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="4f913-142">第一個參數會指定使用 Windows powershell 提供者的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="4f913-142">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="4f913-143">第二個參數指定命令處理期間提供者會公開 Windows PowerShell 執行階段的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="4f913-143">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="4f913-144">此提供者，如有加入任何 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="4f913-144">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="4f913-145">定義基底的功能</span><span class="sxs-lookup"><span data-stu-id="4f913-145">Defining Base Functionality</span></span>

<span data-ttu-id="4f913-146">中所述[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)，則[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別衍生自所提供的其他幾項類別不同的提供者的功能。</span><span class="sxs-lookup"><span data-stu-id="4f913-146">As described in [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="4f913-147">Windows PowerShell 容器提供者，因此，必須定義所有這些類別所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="4f913-147">A Windows PowerShell container provider, therefore, needs to define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="4f913-148">若要實作功能，說明如何加入工作階段特定的初始化資訊，以及用於釋放提供者所使用的資源，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4f913-148">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="4f913-149">不過，大部分的提供者 （包括此處所述的提供者） 可以使用這項功能所提供的 Windows PowerShell 的預設實作。</span><span class="sxs-lookup"><span data-stu-id="4f913-149">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="4f913-150">若要存取資料存放區，提供者必須實作的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="4f913-150">To get access to the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="4f913-151">如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4f913-151">For more information about implementing these methods, see [Creating an Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="4f913-152">若要操作的資料存放區，例如開始、 設定和清除項目，項目的提供者必須實作所提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="4f913-152">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="4f913-153">如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4f913-153">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

## <a name="retrieving-child-items"></a><span data-ttu-id="4f913-154">正在擷取子系項目</span><span class="sxs-lookup"><span data-stu-id="4f913-154">Retrieving Child Items</span></span>

<span data-ttu-id="4f913-155">若要擷取的子系項目，Windows PowerShell 容器提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以支援來自呼叫`Get-ChildItem`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-155">To retrieve a child item, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to support calls from the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="4f913-156">這個方法會從資料存放區擷取子系項目，並將其寫入到管線中，為物件。</span><span class="sxs-lookup"><span data-stu-id="4f913-156">This method retrieves child items from the data store and writes them to the pipeline as objects.</span></span> <span data-ttu-id="4f913-157">如果`recurse`指令程式參數指定，則方法會擷取所有的子系，不論在何種層級。</span><span class="sxs-lookup"><span data-stu-id="4f913-157">If the `recurse` parameter of the cmdlet is specified, the method retrieves all children regardless of what level they are at.</span></span> <span data-ttu-id="4f913-158">如果`recurse`參數沒有指定，則方法會擷取單一層級的子系。</span><span class="sxs-lookup"><span data-stu-id="4f913-158">If the `recurse` parameter is not specified, the method retrieves only a single level of children.</span></span>

<span data-ttu-id="4f913-159">以下是實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)此提供者的方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-159">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method for this provider.</span></span> <span data-ttu-id="4f913-160">請注意，這個方法在路徑表示存取資料庫，並從該資料表的資料列擷取子項目，如果路徑表示的資料表時，會擷取所有的資料庫資料表中的子項目。</span><span class="sxs-lookup"><span data-stu-id="4f913-160">Notice that this method retrieves the child items in all database tables when the path indicates the Access database, and retrieves the child items from the rows of that table if the path indicates a data table.</span></span>

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

#### <a name="things-to-remember-about-implementing-getchilditems"></a><span data-ttu-id="4f913-161">有關實作 GetChildItems 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4f913-161">Things to Remember About Implementing GetChildItems</span></span>

<span data-ttu-id="4f913-162">在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span><span class="sxs-lookup"><span data-stu-id="4f913-162">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span></span>

- <span data-ttu-id="4f913-163">Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="4f913-163">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4f913-164">在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。</span><span class="sxs-lookup"><span data-stu-id="4f913-164">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4f913-165">若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。</span><span class="sxs-lookup"><span data-stu-id="4f913-165">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="4f913-166">此方法的實作應該列入任何形式的存取可能會使項目對使用者顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="4f913-166">The implementation of this method should take into account any form of access to the item that might make the item visible to the user.</span></span> <span data-ttu-id="4f913-167">例如，如果使用者具有寫入權限透過 FileSystem 提供者 （由 Windows PowerShell 提供），但沒有讀取權限的檔案，檔案仍然存在和[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="4f913-167">For example, if a user has write access to a file through the FileSystem provider (supplied by Windows PowerShell), but not read access, the file still exists and [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) returns `true`.</span></span> <span data-ttu-id="4f913-168">您的實作可能需要檢查的父項目，以查看 是否可以列舉子系。</span><span class="sxs-lookup"><span data-stu-id="4f913-168">Your implementation might require the checking of a parent item to see if the child can be enumerated.</span></span>

- <span data-ttu-id="4f913-169">撰寫多個項目，當[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="4f913-169">When writing multiple items, the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method can take some time.</span></span> <span data-ttu-id="4f913-170">您可以設計您的提供者將使用的項目寫入[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法，一次。</span><span class="sxs-lookup"><span data-stu-id="4f913-170">You can design your provider to write the items using the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method one at a time.</span></span> <span data-ttu-id="4f913-171">使用這項技術，將會在資料流中的使用者顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="4f913-171">Using this technique will present the items to the user in a stream.</span></span>

- <span data-ttu-id="4f913-172">您實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)負責防止無限遞迴時有循環的連結，諸如此類的。</span><span class="sxs-lookup"><span data-stu-id="4f913-172">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="4f913-173">應該擲回適當終止的例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="4f913-173">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a><span data-ttu-id="4f913-174">附加至 Get-childitem Cmdlet 的動態參數</span><span class="sxs-lookup"><span data-stu-id="4f913-174">Attaching Dynamic Parameters to the Get-ChildItem Cmdlet</span></span>

<span data-ttu-id="4f913-175">有時候`Get-ChildItem`呼叫的 cmdlet [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)需要在執行階段動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-175">Sometimes the `Get-ChildItem` cmdlet that calls [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4f913-176">若要提供這些動態參數，Windows PowerShell 容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-176">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) method.</span></span> <span data-ttu-id="4f913-177">這個方法會擷取動態參數所指出的路徑處的項目，並傳回物件，此物件具有屬性與欄位類似於 cmdlet 類別屬性的剖析或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="4f913-177">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4f913-178">Windows PowerShell 執行階段會使用傳回的物件加入至參數`Get-ChildItem`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-178">The Windows PowerShell runtime uses the returned object to add the parameters to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="4f913-179">此 Windows PowerShell 容器提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-179">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="4f913-180">不過，下列程式碼是這個方法的預設實作。</span><span class="sxs-lookup"><span data-stu-id="4f913-180">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a><span data-ttu-id="4f913-181">擷取子系項目名稱</span><span class="sxs-lookup"><span data-stu-id="4f913-181">Retrieving Child Item Names</span></span>

<span data-ttu-id="4f913-182">若要擷取子項目的名稱，Windows PowerShell 容器提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以支援來自呼叫`Get-ChildItem`cmdlet 時其`Name`指定參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-182">To retrieve the names of child items, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to support calls from the `Get-ChildItem` cmdlet when its `Name` parameter is specified.</span></span> <span data-ttu-id="4f913-183">這個方法會擷取在指定路徑或子系項目名稱的所有容器的子系項目名稱，如果`returnAllContainers`指定此 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-183">This method retrieves the names of the child items for the specified path or child item names for all containers if the `returnAllContainers` parameter of the cmdlet is specified.</span></span> <span data-ttu-id="4f913-184">子系名稱是分葉的部分路徑。</span><span class="sxs-lookup"><span data-stu-id="4f913-184">A child name is the leaf portion of a path.</span></span> <span data-ttu-id="4f913-185">例如，路徑 c:\windows\system32\abc.dll 子名稱是"abc.dll 」。</span><span class="sxs-lookup"><span data-stu-id="4f913-185">For example, the child name for the path c:\windows\system32\abc.dll is "abc.dll".</span></span> <span data-ttu-id="4f913-186">目錄 c:\windows\system32 的子系名稱是"system32"。</span><span class="sxs-lookup"><span data-stu-id="4f913-186">The child name for the directory c:\windows\system32 is "system32".</span></span>

<span data-ttu-id="4f913-187">以下是實作[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)此提供者的方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-187">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method for this provider.</span></span> <span data-ttu-id="4f913-188">請注意此方法會擷取資料表名稱，是否指定的路徑表示的 Access 資料庫 （磁碟機） 和資料列號碼如果的路徑表示的資料表。</span><span class="sxs-lookup"><span data-stu-id="4f913-188">Notice that the method retrieves table names if the specified path indicates the Access database (drive) and row numbers if the path indicates a table.</span></span>

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

#### <a name="things-to-remember-about-implementing-getchildnames"></a><span data-ttu-id="4f913-189">有關實作 GetChildNames 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4f913-189">Things to Remember About Implementing GetChildNames</span></span>

<span data-ttu-id="4f913-190">在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span><span class="sxs-lookup"><span data-stu-id="4f913-190">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):</span></span>

- <span data-ttu-id="4f913-191">Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="4f913-191">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4f913-192">在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。</span><span class="sxs-lookup"><span data-stu-id="4f913-192">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4f913-193">若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。</span><span class="sxs-lookup"><span data-stu-id="4f913-193">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4f913-194">此規則的例外狀況發生時`returnAllContainers`指定此 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-194">An exception to this rule occurs when the `returnAllContainers` parameter of the cmdlet is specified.</span></span> <span data-ttu-id="4f913-195">在此情況下，此方法應該擷取任何子容器名稱，即使它不符合的值[System.Management.Automation.Provider.Cmdletprovider.Filter\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter)， [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)，或[System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)屬性。</span><span class="sxs-lookup"><span data-stu-id="4f913-195">In this case, the method should retrieve any child name for a container, even if it does not match the values of the [System.Management.Automation.Provider.Cmdletprovider.Filter\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), or [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) properties.</span></span>

- <span data-ttu-id="4f913-196">根據預設，會覆寫這個方法不應該擷取會在除非通常不對使用者顯示的物件名稱[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)指定屬性。</span><span class="sxs-lookup"><span data-stu-id="4f913-196">By default, overrides of this method should not retrieve names of objects that are generally hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is specified.</span></span> <span data-ttu-id="4f913-197">如果指定的路徑表示容器[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。</span><span class="sxs-lookup"><span data-stu-id="4f913-197">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="4f913-198">您實作[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)負責防止無限遞迴時有循環的連結，諸如此類的。</span><span class="sxs-lookup"><span data-stu-id="4f913-198">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="4f913-199">應該擲回適當終止的例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="4f913-199">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a><span data-ttu-id="4f913-200">將動態參數附加至 Get-childitem Cmdlet （名稱）</span><span class="sxs-lookup"><span data-stu-id="4f913-200">Attaching Dynamic Parameters to the Get-ChildItem Cmdlet (Name)</span></span>

<span data-ttu-id="4f913-201">有時候`Get-ChildItem`指令程式 (使用`Name`參數) 需要在執行階段動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-201">Sometimes the `Get-ChildItem` cmdlet (with the `Name` parameter) requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4f913-202">若要提供這些動態參數，Windows PowerShell 容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-202">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) method.</span></span> <span data-ttu-id="4f913-203">這個方法會擷取位於指定路徑的項目動態參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="4f913-203">This method retrieves the dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4f913-204">Windows PowerShell 執行階段會使用傳回的物件加入至參數`Get-ChildItem`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-204">The Windows PowerShell runtime uses the returned object to add the parameters to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="4f913-205">此提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-205">This provider does not implement this method.</span></span> <span data-ttu-id="4f913-206">不過，下列程式碼是這個方法的預設實作。</span><span class="sxs-lookup"><span data-stu-id="4f913-206">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a><span data-ttu-id="4f913-207">重新命名項目</span><span class="sxs-lookup"><span data-stu-id="4f913-207">Renaming Items</span></span>

<span data-ttu-id="4f913-208">若要重新命名項目，Windows PowerShell 容器提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，以支援來自呼叫`Rename-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-208">To rename an item, a Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method to support calls from the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="4f913-209">這個方法會變更指定的路徑處的項目名稱提供的新名稱。</span><span class="sxs-lookup"><span data-stu-id="4f913-209">This method changes the name of the item at the specified path to the new name provided.</span></span> <span data-ttu-id="4f913-210">新的名稱必須一律是相對於父項目 （容器）。</span><span class="sxs-lookup"><span data-stu-id="4f913-210">The new name must always be relative to the parent item (container).</span></span>

<span data-ttu-id="4f913-211">此提供者不會覆寫[System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-211">This provider does not override the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method.</span></span> <span data-ttu-id="4f913-212">不過，以下是預設的實作。</span><span class="sxs-lookup"><span data-stu-id="4f913-212">However, the following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a><span data-ttu-id="4f913-213">有關實作 RenameItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4f913-213">Things to Remember About Implementing RenameItem</span></span>

<span data-ttu-id="4f913-214">在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):</span><span class="sxs-lookup"><span data-stu-id="4f913-214">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):</span></span>

- <span data-ttu-id="4f913-215">Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="4f913-215">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4f913-216">在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。</span><span class="sxs-lookup"><span data-stu-id="4f913-216">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4f913-217">若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。</span><span class="sxs-lookup"><span data-stu-id="4f913-217">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="4f913-218">[System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法是修改之名稱的項目，而不移動作業。</span><span class="sxs-lookup"><span data-stu-id="4f913-218">The [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method is intended for the modification of the name of an item only, and not for move operations.</span></span> <span data-ttu-id="4f913-219">如果方法的實作應該寫入錯誤`newName`參數包含路徑分隔符號，或可能會導致要變更其父代位置的項目。</span><span class="sxs-lookup"><span data-stu-id="4f913-219">Your implementation of the method should write an error if the `newName` parameter contains path separators, or might otherwise cause the item to change its parent location.</span></span>

- <span data-ttu-id="4f913-220">根據預設，這個方法的覆寫應該不重新命名物件，除非[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)指定屬性。</span><span class="sxs-lookup"><span data-stu-id="4f913-220">By default, overrides of this method should not rename objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is specified.</span></span> <span data-ttu-id="4f913-221">如果指定的路徑表示容器[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。</span><span class="sxs-lookup"><span data-stu-id="4f913-221">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="4f913-222">您實作[System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="4f913-222">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="4f913-223">這個方法用來變更系統狀態，例如，重新命名檔案時，請確認執行作業。</span><span class="sxs-lookup"><span data-stu-id="4f913-223">This method is used to confirm execution of an operation when a change is made to system state, for example, renaming files.</span></span> <span data-ttu-id="4f913-224">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)傳送給使用者，變更納入考量，任何命令列設定或喜好設定變數中的 Windows PowerShell 執行階段資源的名稱決定應該要顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="4f913-224">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="4f913-225">若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-225">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="4f913-226">這個方法會傳送一則訊息確認訊息給使用者，以允許其他意見反應，說如果應該繼續執行作業。</span><span class="sxs-lookup"><span data-stu-id="4f913-226">This method sends a message a confirmation message to the user to allow additional feedback to say if the operation should be continued.</span></span> <span data-ttu-id="4f913-227">提供者應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作為額外的檢查，如有潛在危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="4f913-227">A provider should call [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a><span data-ttu-id="4f913-228">將動態參數附加至 Rename-item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f913-228">Attaching Dynamic Parameters to the Rename-Item Cmdlet</span></span>

<span data-ttu-id="4f913-229">有時候`Rename-Item`cmdlet 需要在執行階段動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-229">Sometimes the `Rename-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4f913-230">若要提供這些動態參數，Windows PowerShell 容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-230">To provide these dynamic parameters, Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span> <span data-ttu-id="4f913-231">這個方法會擷取位於指定路徑的項目參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="4f913-231">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4f913-232">Windows PowerShell 執行階段會使用傳回的物件加入至參數`Rename-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-232">The Windows PowerShell runtime uses the returned object to add the parameters to the `Rename-Item` cmdlet.</span></span>

<span data-ttu-id="4f913-233">此容器提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-233">This container provider does not implement this method.</span></span> <span data-ttu-id="4f913-234">不過，下列程式碼是這個方法的預設實作。</span><span class="sxs-lookup"><span data-stu-id="4f913-234">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a><span data-ttu-id="4f913-235">建立新的項目</span><span class="sxs-lookup"><span data-stu-id="4f913-235">Creating New Items</span></span>

<span data-ttu-id="4f913-236">若要建立新的項目，容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以支援來自呼叫`New-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-236">To create new items, a container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to support calls from the `New-Item` cmdlet.</span></span> <span data-ttu-id="4f913-237">這個方法會建立在位於指定路徑的資料項目。</span><span class="sxs-lookup"><span data-stu-id="4f913-237">This method creates a data item located at the specified path.</span></span> <span data-ttu-id="4f913-238">`type` Cmdlet 參數包含新的項目定義提供者類型。</span><span class="sxs-lookup"><span data-stu-id="4f913-238">The `type` parameter of the cmdlet contains the provider-defined type for the new item.</span></span> <span data-ttu-id="4f913-239">例如，FileSystem 提供者會使用`type`參數的值為"file"或"directory"。</span><span class="sxs-lookup"><span data-stu-id="4f913-239">For example, the FileSystem provider uses a `type` parameter with a value of "file" or "directory".</span></span> <span data-ttu-id="4f913-240">`newItemValue`指令程式參數指定新的項目提供者特定值。</span><span class="sxs-lookup"><span data-stu-id="4f913-240">The `newItemValue` parameter of the cmdlet specifies a provider-specific value for the new item.</span></span>

<span data-ttu-id="4f913-241">以下是實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)此提供者的方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-241">Here is the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method for this provider.</span></span>

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

#### <a name="things-to-remember-about-implementing-newitem"></a><span data-ttu-id="4f913-242">有關實作 NewItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4f913-242">Things to Remember About Implementing NewItem</span></span>

<span data-ttu-id="4f913-243">在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span><span class="sxs-lookup"><span data-stu-id="4f913-243">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span></span>

- <span data-ttu-id="4f913-244">[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該執行傳入的字串不區分大小寫比較`type`參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-244">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should perform a case-insensitive comparison of the string passed in the `type` parameter.</span></span> <span data-ttu-id="4f913-245">它也應該允許至少模稜兩可的符合項目。</span><span class="sxs-lookup"><span data-stu-id="4f913-245">It should also allow for least ambiguous matches.</span></span> <span data-ttu-id="4f913-246">比方說，針對類型 「 檔案 」 和 「 目錄 」 中，只有第一個字母，才能釐清。</span><span class="sxs-lookup"><span data-stu-id="4f913-246">For example, for the types "file" and "directory", only the first letter is required to disambiguate.</span></span> <span data-ttu-id="4f913-247">如果`type`參數會指出無法建立您的提供者，型別[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該重寫 ArgumentException 的訊息指出類型可以建立提供者。</span><span class="sxs-lookup"><span data-stu-id="4f913-247">If the `type` parameter indicates a type your provider cannot create, the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should write an ArgumentException with a message indicating the types the provider can create.</span></span>

- <span data-ttu-id="4f913-248">針對`newItemValue`參數，請實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法會建議您接受最小值的字串。</span><span class="sxs-lookup"><span data-stu-id="4f913-248">For the `newItemValue` parameter, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method is recommended to accept strings at a minimum.</span></span> <span data-ttu-id="4f913-249">它也應該接受所擷取物件的型別[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)相同路徑的方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-249">It should also accept the type of object that is retrieved by the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method for the same path.</span></span> <span data-ttu-id="4f913-250">[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法也可以使用[System.Management.Automation.Languageprimitives.Convertto\*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo)方法，將轉換類型所需的類型。</span><span class="sxs-lookup"><span data-stu-id="4f913-250">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method can use the [System.Management.Automation.Languageprimitives.Convertto\*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) method to convert types to the desired type.</span></span>

- <span data-ttu-id="4f913-251">您實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="4f913-251">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="4f913-252">若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true， [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法有潛在危險的系統修改為額外的檢查。</span><span class="sxs-lookup"><span data-stu-id="4f913-252">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns true, the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a><span data-ttu-id="4f913-253">附加至 New-item Cmdlet 的動態參數</span><span class="sxs-lookup"><span data-stu-id="4f913-253">Attaching Dynamic Parameters to the New-Item Cmdlet</span></span>

<span data-ttu-id="4f913-254">有時候`New-Item`cmdlet 需要在執行階段動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-254">Sometimes the `New-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4f913-255">若要提供這些動態參數，容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-255">To provide these dynamic parameters, the container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span> <span data-ttu-id="4f913-256">這個方法會擷取位於指定路徑的項目參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="4f913-256">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4f913-257">Windows PowerShell 執行階段會使用傳回的物件加入至參數`New-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-257">The Windows PowerShell runtime uses the returned object to add the parameters to the `New-Item` cmdlet.</span></span>

<span data-ttu-id="4f913-258">此提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-258">This provider does not implement this method.</span></span> <span data-ttu-id="4f913-259">不過，下列程式碼是這個方法的預設實作。</span><span class="sxs-lookup"><span data-stu-id="4f913-259">However, the following code is the default implementation of this method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a><span data-ttu-id="4f913-260">移除項目</span><span class="sxs-lookup"><span data-stu-id="4f913-260">Removing Items</span></span>

<span data-ttu-id="4f913-261">若要移除的項目，則 Windows PowerShell 提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以支援來自呼叫`Remove-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-261">To remove items, the Windows PowerShell provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to support calls from the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="4f913-262">這個方法會刪除項目從資料存放區，在指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="4f913-262">This method deletes an item from the data store at the specified path.</span></span> <span data-ttu-id="4f913-263">如果`recurse`的參數`Remove-Item`cmdlet 設定為`true`，則方法會移除所有的子項目，不論其層級。</span><span class="sxs-lookup"><span data-stu-id="4f913-263">If the `recurse` parameter of the `Remove-Item` cmdlet is set to `true`, the method removes all child items regardless of their level.</span></span> <span data-ttu-id="4f913-264">如果參數設定為`false`，則方法會移除單一項目在指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="4f913-264">If the parameter is set to `false`, the method removes only a single item at the specified path.</span></span>

<span data-ttu-id="4f913-265">此提供者不支援項目移除。</span><span class="sxs-lookup"><span data-stu-id="4f913-265">This provider does not support item removal.</span></span> <span data-ttu-id="4f913-266">不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)。</span><span class="sxs-lookup"><span data-stu-id="4f913-266">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a><span data-ttu-id="4f913-267">有關實作 RemoveItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4f913-267">Things to Remember About Implementing RemoveItem</span></span>

<span data-ttu-id="4f913-268">在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span><span class="sxs-lookup"><span data-stu-id="4f913-268">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):</span></span>

- <span data-ttu-id="4f913-269">Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="4f913-269">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4f913-270">在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。</span><span class="sxs-lookup"><span data-stu-id="4f913-270">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4f913-271">若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。</span><span class="sxs-lookup"><span data-stu-id="4f913-271">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="4f913-272">根據預設，會覆寫這個方法不應該移除物件除非[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 true。</span><span class="sxs-lookup"><span data-stu-id="4f913-272">By default, overrides of this method should not remove objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to true.</span></span> <span data-ttu-id="4f913-273">如果指定的路徑表示容器[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。</span><span class="sxs-lookup"><span data-stu-id="4f913-273">If the specified path indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span>

- <span data-ttu-id="4f913-274">您實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)負責防止無限遞迴時有循環的連結，諸如此類的。</span><span class="sxs-lookup"><span data-stu-id="4f913-274">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="4f913-275">應該擲回適當終止的例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="4f913-275">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

- <span data-ttu-id="4f913-276">您實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="4f913-276">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="4f913-277">若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法有潛在危險的系統修改為額外的檢查。</span><span class="sxs-lookup"><span data-stu-id="4f913-277">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a><span data-ttu-id="4f913-278">將動態參數附加至 Remove-item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f913-278">Attaching Dynamic Parameters to the Remove-Item Cmdlet</span></span>

<span data-ttu-id="4f913-279">有時候`Remove-Item`cmdlet 需要在執行階段動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-279">Sometimes the `Remove-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4f913-280">若要提供這些動態參數，容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-280">To provide these dynamic parameters, the container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="4f913-281">這個方法會擷取位於指定路徑的項目動態參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="4f913-281">This method retrieves the dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4f913-282">Windows PowerShell 執行階段會使用傳回的物件加入至參數`Remove-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-282">The Windows PowerShell runtime uses the returned object to add the parameters to the `Remove-Item` cmdlet.</span></span>

<span data-ttu-id="4f913-283">此容器提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-283">This container provider does not implement this method.</span></span> <span data-ttu-id="4f913-284">不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)。</span><span class="sxs-lookup"><span data-stu-id="4f913-284">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a><span data-ttu-id="4f913-285">查詢的子項目</span><span class="sxs-lookup"><span data-stu-id="4f913-285">Querying for Child Items</span></span>

<span data-ttu-id="4f913-286">若要查看子項目有指定的路徑，Windows PowerShell 容器提供者必須覆寫[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-286">To check to see if child items exist at the specified path, the Windows PowerShell container provider must override the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method.</span></span> <span data-ttu-id="4f913-287">這個方法會傳回`true`如果項目子系，和`false`否則。</span><span class="sxs-lookup"><span data-stu-id="4f913-287">This method returns `true` if the item has children, and `false` otherwise.</span></span> <span data-ttu-id="4f913-288">為 null 或空白的路徑，此方法會考慮任何資料存放區中為子系的項目並傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="4f913-288">For a null or empty path, the method considers any items in the data store to be children and returns `true`.</span></span>

<span data-ttu-id="4f913-289">以下是 覆寫[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-289">Here is the override for the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method.</span></span> <span data-ttu-id="4f913-290">如果有兩個以上的路徑部分 ChunkPath 協助程式方法所建立的則方法會傳回`false`，因為只有一個資料庫的容器和資料表容器所定義。</span><span class="sxs-lookup"><span data-stu-id="4f913-290">If there are more than two path parts created by the ChunkPath helper method, the method returns `false`, since only a database container and a table container are defined.</span></span> <span data-ttu-id="4f913-291">如需有關這個 helper 方法的詳細資訊，請參閱 ChunkPath 方法中會討論[建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4f913-291">For more information about this helper method, see the ChunkPath method is discussed in [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a><span data-ttu-id="4f913-292">有關實作 HasChildItems 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4f913-292">Things to Remember About Implementing HasChildItems</span></span>

<span data-ttu-id="4f913-293">在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):</span><span class="sxs-lookup"><span data-stu-id="4f913-293">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):</span></span>

- <span data-ttu-id="4f913-294">如果容器提供者會公開包含有趣的掛接點，實作的根[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法應傳回`true`為 null 或空字串傳遞時的路徑。</span><span class="sxs-lookup"><span data-stu-id="4f913-294">If the container provider exposes a root that contains interesting mount points, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) method should return `true` when a null or an empty string is passed in for the path.</span></span>

## <a name="copying-items"></a><span data-ttu-id="4f913-295">複製項目</span><span class="sxs-lookup"><span data-stu-id="4f913-295">Copying Items</span></span>

<span data-ttu-id="4f913-296">若要複製的項目，容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以支援來自呼叫`Copy-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-296">To copy items, the container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to support calls from the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="4f913-297">這個方法會從指定的位置複製資料項目`path`參數所指示位置 cmdlet`copyPath`參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-297">This method copies a data item from the location indicated by the `path` parameter of the cmdlet to the location indicated by the `copyPath` parameter.</span></span> <span data-ttu-id="4f913-298">如果`recurse`參數指定，則方法會複製所有的子容器。</span><span class="sxs-lookup"><span data-stu-id="4f913-298">If the `recurse` parameter is specified, the method copies all sub-containers.</span></span> <span data-ttu-id="4f913-299">如果未指定參數，則方法會複製項目中的單一層級。</span><span class="sxs-lookup"><span data-stu-id="4f913-299">If the parameter is not specified, the method copies only a single level of items.</span></span>

<span data-ttu-id="4f913-300">此提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-300">This provider does not implement this method.</span></span> <span data-ttu-id="4f913-301">不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)。</span><span class="sxs-lookup"><span data-stu-id="4f913-301">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a><span data-ttu-id="4f913-302">有關實作 CopyItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4f913-302">Things to Remember About Implementing CopyItem</span></span>

<span data-ttu-id="4f913-303">在下列情況可能適用於您實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):</span><span class="sxs-lookup"><span data-stu-id="4f913-303">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):</span></span>

- <span data-ttu-id="4f913-304">Windows PowerShell 容器提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="4f913-304">When defining the provider class, a Windows PowerShell container provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4f913-305">在這些情況下，實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要確定傳遞給方法的路徑符合指定需求功能。</span><span class="sxs-lookup"><span data-stu-id="4f913-305">In these cases, the implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method needs to ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="4f913-306">若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。</span><span class="sxs-lookup"><span data-stu-id="4f913-306">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="4f913-307">根據預設，會覆寫這個方法不應該複製物件現有的物件除非[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="4f913-307">By default, overrides of this method should not copy objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="4f913-308">例如，FileSystem 提供者不會複製 c:\temp\abc.txt 透過現有 c:\abc.txt 檔案除非[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="4f913-308">For example, the FileSystem provider will not copy c:\temp\abc.txt over an existing c:\abc.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="4f913-309">如果在指定的路徑`copyPath`參數存在，並指出容器[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。</span><span class="sxs-lookup"><span data-stu-id="4f913-309">If the path specified in the `copyPath` parameter exists and indicates a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="4f913-310">在此情況下， [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)應該複製所指定的項目`path`所指定的參數，以容器`copyPath`參數做為子系。</span><span class="sxs-lookup"><span data-stu-id="4f913-310">In this case, [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) should copy the item indicated by the `path` parameter to the container indicated by the `copyPath` parameter as a child.</span></span>

- <span data-ttu-id="4f913-311">您實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)負責防止無限遞迴時有循環的連結，諸如此類的。</span><span class="sxs-lookup"><span data-stu-id="4f913-311">Your implementation of [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) is responsible for preventing infinite recursion when there are circular links, and the like.</span></span> <span data-ttu-id="4f913-312">應該擲回適當終止的例外狀況，以反映這種情況。</span><span class="sxs-lookup"><span data-stu-id="4f913-312">An appropriate terminating exception should be thrown to reflect such a condition.</span></span>

- <span data-ttu-id="4f913-313">您實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="4f913-313">Your implementation of the [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="4f913-314">若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 true， [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法有潛在危險的系統修改為額外的檢查。</span><span class="sxs-lookup"><span data-stu-id="4f913-314">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns true, the [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method as an additional check for potentially dangerous system modifications.</span></span> <span data-ttu-id="4f913-315">如需有關呼叫這些方法的詳細資訊，請參閱 <<c0> [ 重新命名的項目](#Renaming-Items)。</span><span class="sxs-lookup"><span data-stu-id="4f913-315">For more information about calling these methods, see [Rename Items](#Renaming-Items).</span></span>

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a><span data-ttu-id="4f913-316">將動態參數附加至 Copy-item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f913-316">Attaching Dynamic Parameters to the Copy-Item Cmdlet</span></span>

<span data-ttu-id="4f913-317">有時候`Copy-Item`cmdlet 需要在執行階段動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-317">Sometimes the `Copy-Item` cmdlet requires additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="4f913-318">若要提供這些動態參數，Windows PowerShell 容器提供者必須實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)處理這些方法參數。</span><span class="sxs-lookup"><span data-stu-id="4f913-318">To provide these dynamic parameters, the Windows PowerShell container provider must implement the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="4f913-319">這個方法會擷取位於指定路徑的項目參數，並傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="4f913-319">This method retrieves the parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="4f913-320">Windows PowerShell 執行階段會使用傳回的物件加入至參數`Copy-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f913-320">The Windows PowerShell runtime uses the returned object to add the parameters to the `Copy-Item` cmdlet.</span></span>

<span data-ttu-id="4f913-321">此提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="4f913-321">This provider does not implement this method.</span></span> <span data-ttu-id="4f913-322">不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)。</span><span class="sxs-lookup"><span data-stu-id="4f913-322">However, the following code is the default implementation of [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a><span data-ttu-id="4f913-323">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4f913-323">Code Sample</span></span>

<span data-ttu-id="4f913-324">完整的範例程式碼，請參閱[AccessDbProviderSample04 程式碼範例](./accessdbprovidersample04-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="4f913-324">For complete sample code, see [AccessDbProviderSample04 Code Sample](./accessdbprovidersample04-code-sample.md).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="4f913-325">建置 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4f913-325">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="4f913-326">請參閱[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="4f913-326">See [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="4f913-327">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4f913-327">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="4f913-328">當您的 Windows PowerShell 提供者已向 Windows PowerShell 時，您可以藉由在命令列上執行受支援的 cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="4f913-328">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="4f913-329">請注意，下列範例輸出會使用虛構的 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4f913-329">Be aware that the following example output uses a fictitious Access database.</span></span>

1. <span data-ttu-id="4f913-330">執行`Get-ChildItem`cmdlet 來從 Access 資料庫中的 [客戶] 資料表中擷取的子系項目清單。</span><span class="sxs-lookup"><span data-stu-id="4f913-330">Run the `Get-ChildItem` cmdlet to retrieve the list of child items from a Customers table in the Access database.</span></span>

   ```powershell
   Get-ChildItem mydb:customers
   ```

   <span data-ttu-id="4f913-331">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4f913-331">The following output appears.</span></span>

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

2. <span data-ttu-id="4f913-332">執行`Get-ChildItem`cmdlet 一次來擷取資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="4f913-332">Run the `Get-ChildItem` cmdlet again to retrieve the data of a table.</span></span>

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   <span data-ttu-id="4f913-333">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4f913-333">The following output appears.</span></span>

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. <span data-ttu-id="4f913-334">現在使用`Get-Item`cmdlet 來擷取資料表中的資料列 0 的項目。</span><span class="sxs-lookup"><span data-stu-id="4f913-334">Now use the `Get-Item` cmdlet to retrieve the items at row 0 in the data table.</span></span>

   ```powershell
   Get-Item mydb:\customers\0
   ```

   <span data-ttu-id="4f913-335">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4f913-335">The following output appears.</span></span>

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. <span data-ttu-id="4f913-336">重複使用`Get-Item`擷取的資料列 0 中的項目。</span><span class="sxs-lookup"><span data-stu-id="4f913-336">Reuse `Get-Item` to retrieve the data for the items in row 0.</span></span>

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   <span data-ttu-id="4f913-337">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4f913-337">The following output appears.</span></span>

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

5. <span data-ttu-id="4f913-338">現在使用`New-Item`cmdlet 將資料列新增至現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="4f913-338">Now use the `New-Item` cmdlet to add a row to an existing table.</span></span> <span data-ttu-id="4f913-339">`Path`參數指定的資料列的完整路徑，並必須指出資料列數目大於現有的資料表中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="4f913-339">The `Path` parameter specifies the full path to the row, and must indicate a row number that is greater than the existing number of rows in the table.</span></span> <span data-ttu-id="4f913-340">`Type`參數會指示 「 資料列 」 來指定要加入項目該類型。</span><span class="sxs-lookup"><span data-stu-id="4f913-340">The `Type` parameter indicates "row" to specify that type of item to add.</span></span> <span data-ttu-id="4f913-341">最後，`Value`參數指定的資料列的資料行值的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="4f913-341">Finally, the `Value` parameter specifies a comma-delimited list of column values for the row.</span></span>

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAdress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. <span data-ttu-id="4f913-342">請確認新的項目作業的正確性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="4f913-342">Verify the correctness of the new item operation as follows.</span></span>

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   <span data-ttu-id="4f913-343">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4f913-343">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4f913-344">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f913-344">See Also</span></span>

[<span data-ttu-id="4f913-345">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4f913-345">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="4f913-346">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4f913-346">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="4f913-347">實作項目 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4f913-347">Implementing an Item Windows PowerShell Provider</span></span>](./creating-a-windows-powershell-item-provider.md)

[<span data-ttu-id="4f913-348">實作瀏覽 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4f913-348">Implementing a Navigation Windows PowerShell Provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

[<span data-ttu-id="4f913-349">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="4f913-349">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="4f913-350">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4f913-350">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="4f913-351">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="4f913-351">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)