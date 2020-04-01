---
title: 建立 Windows PowerShell 瀏覽提供者
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
ms.openlocfilehash: 7ca7e3ca6feeba018ad793d074caf67cd9506a68
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500812"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a><span data-ttu-id="6625f-102">建立 Windows PowerShell 瀏覽提供者</span><span class="sxs-lookup"><span data-stu-id="6625f-102">Creating a Windows PowerShell Navigation Provider</span></span>

<span data-ttu-id="6625f-103">本主題說明如何建立可流覽資料存放區的 Windows PowerShell 流覽提供者。</span><span class="sxs-lookup"><span data-stu-id="6625f-103">This topic describes how to create a Windows PowerShell navigation provider that can navigate the data store.</span></span> <span data-ttu-id="6625f-104">這種類型的提供者支援遞迴命令、嵌套容器和相對路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-104">This type of provider supports recursive commands, nested containers, and relative paths.</span></span>

> [!NOTE]
> <span data-ttu-id="6625f-105">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的原始程式檔（AccessDBSampleProvider05.cs）。</span><span class="sxs-lookup"><span data-stu-id="6625f-105">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6625f-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="6625f-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="6625f-107">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="6625f-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="6625f-108">如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6625f-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="6625f-109">這裡所述的提供者可讓使用者將 Access 資料庫當做磁片磁碟機來處理，讓使用者可以流覽至資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="6625f-109">The provider described here enables the user handle an Access database as a drive so that the user can navigate to the data tables in the database.</span></span> <span data-ttu-id="6625f-110">在建立您自己的導覽提供者時，您可以執行方法，以建立導覽所需的磁片磁碟機路徑、將相對路徑標準化、移動資料存放區的專案，以及取得子名稱的方法、取得專案的父路徑，以及測試識別專案是否為容器。</span><span class="sxs-lookup"><span data-stu-id="6625f-110">When creating your own navigation provider, you can implement methods that can make drive-qualified paths required for navigation, normalize relative paths, move items of the data store, as well as methods that get child names, get the parent path of an item, and test to identify if an item is a container.</span></span>

> [!CAUTION]
> <span data-ttu-id="6625f-111">請注意，這項設計假設有一個具有名稱識別碼之欄位的資料庫，而且欄位的類型是 LongInteger。</span><span class="sxs-lookup"><span data-stu-id="6625f-111">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

## <a name="define-the-windows-powershell-provider"></a><span data-ttu-id="6625f-112">定義 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6625f-112">Define the Windows PowerShell provider</span></span>

<span data-ttu-id="6625f-113">Windows PowerShell 流覽提供者必須建立一個衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基類的 .net 類別，。</span><span class="sxs-lookup"><span data-stu-id="6625f-113">A Windows PowerShell navigation provider must create a .NET class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="6625f-114">以下是本節所述之導覽提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="6625f-114">Here is the class definition for the navigation provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

<span data-ttu-id="6625f-115">請注意，在此提供者中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="6625f-115">Note that in this provider, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="6625f-116">第一個參數會為 Windows PowerShell 所使用的提供者指定易記的名稱。</span><span class="sxs-lookup"><span data-stu-id="6625f-116">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="6625f-117">第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="6625f-117">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="6625f-118">對於此提供者，不會新增任何 Windows PowerShell 特有的功能。</span><span class="sxs-lookup"><span data-stu-id="6625f-118">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="6625f-119">定義基本功能</span><span class="sxs-lookup"><span data-stu-id="6625f-119">Defining Base Functionality</span></span>

<span data-ttu-id="6625f-120">如[設計您的 PS 提供者](./designing-your-windows-powershell-provider.md)中所述， [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基類衍生自提供不同提供者功能的其他幾個類別。</span><span class="sxs-lookup"><span data-stu-id="6625f-120">As described in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="6625f-121">因此，Windows PowerShell 流覽提供者必須定義這些類別所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="6625f-121">A Windows PowerShell navigation provider, therefore, must define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="6625f-122">若要執行功能來新增會話特定的初始化資訊，以及釋放提供者所使用的資源，請參閱[建立基本的 PS 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6625f-122">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic PS Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="6625f-123">不過，大部分的提供者（包括這裡所述的提供者）都可以使用 Windows PowerShell 所提供的這項功能的預設執行。</span><span class="sxs-lookup"><span data-stu-id="6625f-123">However, most providers (including the provider described here) can use the default implementation of this functionality provided by Windows PowerShell.</span></span>

<span data-ttu-id="6625f-124">若要透過 Windows PowerShell 磁片磁碟機取得資料存放區的存取權，您必須執行[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的方法。</span><span class="sxs-lookup"><span data-stu-id="6625f-124">To get access to the data store through a Windows PowerShell drive, you must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="6625f-125">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6625f-125">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="6625f-126">若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="6625f-126">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="6625f-127">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6625f-127">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="6625f-128">若要取得資料存放區的子專案（或其名稱），以及建立、複製、重新命名和移除專案的方法，您必須執行[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="6625f-128">To get to the child items, or their names, of the data store, as well as methods that create, copy, rename, and remove items, you must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="6625f-129">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6625f-129">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

## <a name="creating-a-windows-powershell-path"></a><span data-ttu-id="6625f-130">建立 Windows PowerShell 路徑</span><span class="sxs-lookup"><span data-stu-id="6625f-130">Creating a Windows PowerShell Path</span></span>

<span data-ttu-id="6625f-131">Windows PowerShell 流覽提供者會使用提供者內部的 Windows PowerShell 路徑來流覽資料存放區的專案。</span><span class="sxs-lookup"><span data-stu-id="6625f-131">Windows PowerShell navigation provider use a provider-internal Windows PowerShell path to navigate the items of the data store.</span></span> <span data-ttu-id="6625f-132">若要建立提供者內部路徑，提供者必須執行[NavigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法，以支援來自合併-path Cmdlet 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="6625f-132">To create a provider-internal path the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to supports calls from the Combine-Path cmdlet.</span></span> <span data-ttu-id="6625f-133">這個方法會使用父系和子路徑之間提供者特定的路徑分隔符號，將父系和子路徑結合成提供者內部路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-133">This method combines a parent and child path into a provider-internal path, using a provider-specific path separator between the parent and child paths.</span></span>

<span data-ttu-id="6625f-134">預設的執行會採用 "/" 或 "\\" 路徑做為路徑分隔符號、將路徑分隔符號正規化為 "\\"、結合父系和子路徑部分與它們之間的分隔符號，然後傳回包含合併路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="6625f-134">The default implementation takes paths with "/" or "\\" as the path separator, normalizes the path separator to "\\", combines the parent and child path parts with the separator between them, and then returns a string that contains the combined paths.</span></span>

<span data-ttu-id="6625f-135">此導覽提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="6625f-135">This navigation provider does not implement this method.</span></span> <span data-ttu-id="6625f-136">不過，下列程式碼是[NavigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法的預設實值。</span><span class="sxs-lookup"><span data-stu-id="6625f-136">However, the following code is the default implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a><span data-ttu-id="6625f-137">執行 MakePath 的相關事項</span><span class="sxs-lookup"><span data-stu-id="6625f-137">Things to Remember About Implementing MakePath</span></span>

<span data-ttu-id="6625f-138">下列條件可能適用于您的[NavigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="6625f-138">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span></span>

- <span data-ttu-id="6625f-139">您的[NavigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法的執行不應在提供者命名空間中驗證路徑是否為合法的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-139">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method should not validate the path as a legal fully-qualified path in the provider namespace.</span></span> <span data-ttu-id="6625f-140">請注意，每個參數只能代表路徑的一部分，而組合的元件可能不會產生完整路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-140">Be aware that each parameter can only represent a part of a path, and the combined parts might not generate a fully-qualified path.</span></span> <span data-ttu-id="6625f-141">例如，filesystem 提供者的[NavigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法可能會在 `parent` 參數中接收 "windows\system32"，並在 `child` 參數中收到 "abc"。</span><span class="sxs-lookup"><span data-stu-id="6625f-141">For example, the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method for the filesystem provider might receive "windows\system32" in the `parent` parameter and "abc.dll" in the `child` parameter.</span></span> <span data-ttu-id="6625f-142">方法會將這些值與 "\\" 分隔符號聯結，並傳回 "windows\system32\abc.dll"，這不是完整的檔案系統路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-142">The method joins these values with the "\\" separator and returns "windows\system32\abc.dll", which is not a fully-qualified file system path.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="6625f-143">[NavigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)的呼叫中所提供的路徑部分可能包含提供者命名空間中不允許的字元。</span><span class="sxs-lookup"><span data-stu-id="6625f-143">The path parts provided in the call to [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) might contain characters not allowed in the provider namespace.</span></span> <span data-ttu-id="6625f-144">這些字元最有可能用於萬用字元擴充，而此方法的執行不應將其移除。</span><span class="sxs-lookup"><span data-stu-id="6625f-144">These characters are most likely used for wildcard expansion and the implementation of this method should not remove them.</span></span>

## <a name="retrieving-the-parent-path"></a><span data-ttu-id="6625f-145">正在抓取父路徑</span><span class="sxs-lookup"><span data-stu-id="6625f-145">Retrieving the Parent Path</span></span>

<span data-ttu-id="6625f-146">Windows PowerShell 導覽提供者會執行[NavigationCmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法，以取得指定完整或部分提供者特定路徑的父系部分。</span><span class="sxs-lookup"><span data-stu-id="6625f-146">Windows PowerShell navigation providers implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method to retrieve the parent part of the indicated full or partial provider-specific path.</span></span> <span data-ttu-id="6625f-147">方法會移除路徑的子部分，並傳回父路徑部分。</span><span class="sxs-lookup"><span data-stu-id="6625f-147">The method removes the child part of the path and returns the parent path part.</span></span> <span data-ttu-id="6625f-148">`root` 參數會指定磁片磁碟機根目錄的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-148">The `root` parameter specifies the fully-qualified path to the root of a drive.</span></span> <span data-ttu-id="6625f-149">如果載入的磁片磁碟機不是用於抓取作業，此參數可以是 null 或空白。</span><span class="sxs-lookup"><span data-stu-id="6625f-149">This parameter can be null or empty if a mounted drive is not in use for the retrieval operation.</span></span> <span data-ttu-id="6625f-150">如果指定了根，此方法必須傳回與根相同之樹狀結構中容器的路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-150">If a root is specified, the method must return a path to a container in the same tree as the root.</span></span>

<span data-ttu-id="6625f-151">範例導覽提供者不會覆寫這個方法，而是使用預設的實作為。</span><span class="sxs-lookup"><span data-stu-id="6625f-151">The sample navigation provider does not override this method, but uses the default implementation.</span></span>
<span data-ttu-id="6625f-152">它接受使用 "/" 和 "\\" 做為路徑分隔符號的路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-152">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="6625f-153">它會先將路徑正規化，使其只有「\\」分隔符號，然後在最後一個「\\」分割父路徑，並傳回父路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-153">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the parent path.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a><span data-ttu-id="6625f-154">若要記住如何執行 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="6625f-154">To Remember About Implementing GetParentPath</span></span>

<span data-ttu-id="6625f-155">您的[NavigationCmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法應會在提供者命名空間的路徑分隔符號上分割路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-155">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method should split the path lexically on the path separator for the provider namespace.</span></span> <span data-ttu-id="6625f-156">例如，filesystem 提供者會使用這個方法來尋找最後一個 "\\"，並傳回分隔符號左邊的所有內容。</span><span class="sxs-lookup"><span data-stu-id="6625f-156">For example, the filesystem provider uses this method to look for the last "\\" and returns everything to the left of the separator.</span></span>

## <a name="retrieve-the-child-path-name"></a><span data-ttu-id="6625f-157">取出子路徑名稱</span><span class="sxs-lookup"><span data-stu-id="6625f-157">Retrieve the Child Path Name</span></span>

<span data-ttu-id="6625f-158">您的導覽提供者會執行[NavigationCmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法，以取得位於指定的完整或部分提供者特定路徑之專案子系的名稱（分葉元素）。</span><span class="sxs-lookup"><span data-stu-id="6625f-158">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method to retrieve the name (leaf element) of the child of the item located at the indicated full or partial provider-specific path.</span></span>

<span data-ttu-id="6625f-159">範例導覽提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="6625f-159">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="6625f-160">預設的執行如下所示。</span><span class="sxs-lookup"><span data-stu-id="6625f-160">The default implementation is shown below.</span></span> <span data-ttu-id="6625f-161">它接受使用 "/" 和 "\\" 做為路徑分隔符號的路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-161">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="6625f-162">它會先將路徑正規化，使其只有 "\\" 分隔符號，然後在最後一個 "\\" 分割父路徑，並傳回子路徑部分的名稱。</span><span class="sxs-lookup"><span data-stu-id="6625f-162">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the name of the child path part.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a><span data-ttu-id="6625f-163">執行 GetChildName 的相關事項</span><span class="sxs-lookup"><span data-stu-id="6625f-163">Things to Remember About Implementing GetChildName</span></span>

<span data-ttu-id="6625f-164">您的[NavigationCmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法應會在路徑分隔符號上以詞法方式分割路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-164">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method should split the path lexically on the path separator.</span></span> <span data-ttu-id="6625f-165">如果提供的路徑未包含路徑分隔符號，此方法應該會傳回未修改的路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-165">If the supplied path contains no path separators, the method should return the path unmodified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6625f-166">呼叫此方法時所提供的路徑可能包含在提供者命名空間中不合法的字元。</span><span class="sxs-lookup"><span data-stu-id="6625f-166">The path provided in the call to this method might contain characters that are illegal in the provider namespace.</span></span> <span data-ttu-id="6625f-167">這些字元最可能用於萬用字元擴充或正則運算式比對，而此方法的執行不應將其移除。</span><span class="sxs-lookup"><span data-stu-id="6625f-167">These characters are most likely used for wildcard expansion or regular expression matching, and the implementation of this method should not remove them.</span></span>

## <a name="determining-if-an-item-is-a-container"></a><span data-ttu-id="6625f-168">判斷專案是否為容器</span><span class="sxs-lookup"><span data-stu-id="6625f-168">Determining if an Item is a Container</span></span>

<span data-ttu-id="6625f-169">導覽提供者可以執行[NavigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法，以判斷指定的路徑是否表示容器。</span><span class="sxs-lookup"><span data-stu-id="6625f-169">The navigation provider can implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method to determine if the specified path indicates a container.</span></span> <span data-ttu-id="6625f-170">如果路徑代表容器，則會傳回 true，否則會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="6625f-170">It returns true if the path represents a container, and false otherwise.</span></span> <span data-ttu-id="6625f-171">使用者需要此方法才能針對提供的路徑使用 `Test-Path` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6625f-171">The user needs this method to be able to use the `Test-Path` cmdlet for the supplied path.</span></span>

<span data-ttu-id="6625f-172">下列程式碼顯示範例導覽提供者中的[NavigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)執行。</span><span class="sxs-lookup"><span data-stu-id="6625f-172">The following code shows the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementation in our sample navigation provider.</span></span> <span data-ttu-id="6625f-173">方法會驗證指定的路徑是否正確，以及資料表是否存在，如果路徑指出容器，則會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="6625f-173">The method verifies that the specified path is correct and if the table exists, and returns true if the path indicates a container.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a><span data-ttu-id="6625f-174">執行 IsItemContainer 的相關事項</span><span class="sxs-lookup"><span data-stu-id="6625f-174">Things to Remember About Implementing IsItemContainer</span></span>

<span data-ttu-id="6625f-175">您的導覽提供者 .NET 類別可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中，宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="6625f-175">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="6625f-176">在此情況下， [NavigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)的執行必須確保傳遞的路徑符合需求。</span><span class="sxs-lookup"><span data-stu-id="6625f-176">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) needs to ensure that the path passed meets requirements.</span></span> <span data-ttu-id="6625f-177">若要這樣做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)屬性（property）。</span><span class="sxs-lookup"><span data-stu-id="6625f-177">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) property.</span></span>

## <a name="moving-an-item"></a><span data-ttu-id="6625f-178">移動專案</span><span class="sxs-lookup"><span data-stu-id="6625f-178">Moving an Item</span></span>

<span data-ttu-id="6625f-179">為了支援 `Move-Item` Cmdlet，您的導覽提供者會執行[NavigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。</span><span class="sxs-lookup"><span data-stu-id="6625f-179">In support of the `Move-Item` cmdlet, your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="6625f-180">這個方法會在 `destination` 參數中提供的路徑上，將 `path` 參數所指定的專案移至容器。</span><span class="sxs-lookup"><span data-stu-id="6625f-180">This method moves the item specified by the `path` parameter to the container at the path supplied in the `destination` parameter.</span></span>

<span data-ttu-id="6625f-181">範例導覽提供者不會覆寫[NavigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。</span><span class="sxs-lookup"><span data-stu-id="6625f-181">The sample navigation provider does not override the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="6625f-182">以下是預設的執行。</span><span class="sxs-lookup"><span data-stu-id="6625f-182">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a><span data-ttu-id="6625f-183">執行 MoveItem 的相關事項</span><span class="sxs-lookup"><span data-stu-id="6625f-183">Things to Remember About Implementing MoveItem</span></span>

<span data-ttu-id="6625f-184">您的導覽提供者 .NET 類別可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中，宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="6625f-184">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="6625f-185">在此情況下， [NavigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)的執行必須確保傳遞的路徑符合需求。</span><span class="sxs-lookup"><span data-stu-id="6625f-185">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) must ensure that the path passed meets requirements.</span></span> <span data-ttu-id="6625f-186">若要這麼做，方法應該存取適當的屬性，例如**CmdletProvider**屬性。</span><span class="sxs-lookup"><span data-stu-id="6625f-186">To do this, the method should access the appropriate property, for example, the **CmdletProvider.Exclude** property.</span></span>

<span data-ttu-id="6625f-187">根據預設，除非[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`，否則此方法的覆寫不應在現有物件上移動物件。</span><span class="sxs-lookup"><span data-stu-id="6625f-187">By default, overrides of this method should not move objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="6625f-188">例如，filesystem 提供者不會將 c:\temp\abc.txt 複製到現有的 c:\bar.txt 檔，除非已將[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6625f-188">For example, the filesystem provider will not copy c:\temp\abc.txt over an existing c:\bar.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="6625f-189">如果 `destination` 參數中指定的路徑存在，而且是容器，則不需要[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性。</span><span class="sxs-lookup"><span data-stu-id="6625f-189">If the path specified in the `destination` parameter exists and is a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="6625f-190">在此情況下， [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)會將 `path` 參數所指示的專案，移至 `destination` 參數所指示的容器做為子系。</span><span class="sxs-lookup"><span data-stu-id="6625f-190">In this case, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) should move the item indicated by the `path` parameter to the container indicated by the `destination` parameter as a child.</span></span>

<span data-ttu-id="6625f-191">您的 NavigationCmdletprovider 必須先呼叫[Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法，然後在對資料存放區進行任何變更之前，先檢查它的傳回值，然後再執行此[程式](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)。</span><span class="sxs-lookup"><span data-stu-id="6625f-191">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="6625f-192">這個方法是用來在對系統狀態進行變更（例如刪除檔案）時，確認作業的執行。</span><span class="sxs-lookup"><span data-stu-id="6625f-192">This method is used to confirm execution of an operation when a change is made to system state, for example, deleting files.</span></span>
<span data-ttu-id="6625f-193">[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳送要變更的資源名稱給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數列入決定要向使用者顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="6625f-193">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="6625f-194">呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 `true`，則[NavigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法應會呼叫 system.servicemodel. Cmdletprovider [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ShouldContinue 方法（.........）。</span><span class="sxs-lookup"><span data-stu-id="6625f-194">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="6625f-195">這個方法會將訊息傳送給使用者，以便在應該繼續作業的情況下，提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="6625f-195">This method sends a message to the user to allow feedback to say if the operation should be continued.</span></span> <span data-ttu-id="6625f-196">您的提供者應該呼叫[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作為額外檢查，以進行潛在危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="6625f-196">Your provider should call [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a><span data-ttu-id="6625f-197">將動態參數附加至移動專案 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6625f-197">Attaching Dynamic Parameters to the Move-Item Cmdlet</span></span>

<span data-ttu-id="6625f-198">有時候 `Move-Item` Cmdlet 需要在執行時間動態提供的其他參數。</span><span class="sxs-lookup"><span data-stu-id="6625f-198">Sometimes the `Move-Item` cmdlet requires additional parameters that are provided dynamically at runtime.</span></span> <span data-ttu-id="6625f-199">若要提供這些動態參數，導覽提供者必須執行[NavigationCmdletprovider. Moveitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法，以從指定路徑的專案中取得必要的參數值，並傳回具有屬性和欄位的物件，而該物件具有類似 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="6625f-199">To provide these dynamic parameters, the navigation provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method to get the required parameter values from the item at the indicated path, and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="6625f-200">此導覽提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="6625f-200">This navigation provider does not implement this method.</span></span> <span data-ttu-id="6625f-201">不過，下列程式碼是[NavigationCmdletprovider. Moveitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="6625f-201">However, the following code is the default implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a><span data-ttu-id="6625f-202">正規化相對路徑</span><span class="sxs-lookup"><span data-stu-id="6625f-202">Normalizing a Relative Path</span></span>

<span data-ttu-id="6625f-203">您的導覽提供者會執行[NavigationCmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法，以將 `path` 參數中指出的完整路徑正規化為相對於 `basePath` 參數所指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-203">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method to normalize the fully-qualified path indicated in the `path` parameter as being relative to the path specified by the `basePath` parameter.</span></span> <span data-ttu-id="6625f-204">方法會傳回正規化路徑的字串標記法。</span><span class="sxs-lookup"><span data-stu-id="6625f-204">The method returns a string representation of the normalized path.</span></span> <span data-ttu-id="6625f-205">如果 `path` 參數指定了不存在的路徑，它就會寫入錯誤。</span><span class="sxs-lookup"><span data-stu-id="6625f-205">It writes an error if the `path` parameter specifies a nonexistent path.</span></span>

<span data-ttu-id="6625f-206">範例導覽提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="6625f-206">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="6625f-207">以下是預設的執行。</span><span class="sxs-lookup"><span data-stu-id="6625f-207">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a><span data-ttu-id="6625f-208">執行 NormalizeRelativePath 的相關事項</span><span class="sxs-lookup"><span data-stu-id="6625f-208">Things to Remember About Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="6625f-209">您的[NavigationCmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)應剖析 `path` 參數，但不需要使用純粹的語法剖析。（）</span><span class="sxs-lookup"><span data-stu-id="6625f-209">Your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) should parse the `path` parameter, but it does not have to use purely syntactical parsing.</span></span> <span data-ttu-id="6625f-210">建議您設計這個方法，以使用路徑來查閱資料存放區中的路徑資訊，並建立符合大小寫和標準化路徑語法的路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-210">You are encouraged to design this method to use the path to look up the path information in the data store and create a path that matches the casing and standardized path syntax.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6625f-211">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6625f-211">Code Sample</span></span>

<span data-ttu-id="6625f-212">如需完整的範例程式碼，請參閱[AccessDbProviderSample05 程式碼範例](./accessdbprovidersample05-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6625f-212">For complete sample code, see [AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="6625f-213">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="6625f-213">Defining Object Types and Formatting</span></span>

<span data-ttu-id="6625f-214">提供者可能會將成員新增至現有的物件，或定義新的物件。</span><span class="sxs-lookup"><span data-stu-id="6625f-214">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="6625f-215">如需詳細資訊，請參閱[擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="6625f-215">For more information, see[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="6625f-216">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6625f-216">Building the Windows PowerShell provider</span></span>

<span data-ttu-id="6625f-217">如需詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="6625f-217">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="6625f-218">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6625f-218">Testing the Windows PowerShell provider</span></span>

<span data-ttu-id="6625f-219">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試，包括衍生所提供的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6625f-219">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including cmdlets made available by derivation.</span></span> <span data-ttu-id="6625f-220">這個範例會測試範例導覽提供者。</span><span class="sxs-lookup"><span data-stu-id="6625f-220">This example will test the sample navigation provider.</span></span>

1. <span data-ttu-id="6625f-221">執行新的 shell，並使用 `Set-Location` Cmdlet 來設定路徑，以指出 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6625f-221">Run your new shell and use the `Set-Location` cmdlet to set the path to indicate the Access database.</span></span>

   ```powershell
   Set-Location mydb:
   ```

2. <span data-ttu-id="6625f-222">現在，請執行 `Get-Childitem` Cmdlet 來抓取資料庫專案的清單，這是可用的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="6625f-222">Now run the `Get-Childitem` cmdlet to retrieve a list of the database items, which are the available database tables.</span></span> <span data-ttu-id="6625f-223">針對每個資料表，此 Cmdlet 也會抓取資料表資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="6625f-223">For each table, this cmdlet also retrieves the number of table rows.</span></span>

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

3. <span data-ttu-id="6625f-224">再次使用 `Set-Location` Cmdlet 來設定 Employees 資料表的位置。</span><span class="sxs-lookup"><span data-stu-id="6625f-224">Use the `Set-Location` cmdlet again to set the location of the Employees data table.</span></span>

   ```powershell
   Set-Location Employees
   ```

4. <span data-ttu-id="6625f-225">現在，讓我們使用 `Get-Location` Cmdlet 來抓取 Employees 資料表的路徑。</span><span class="sxs-lookup"><span data-stu-id="6625f-225">Let's now use the `Get-Location` cmdlet to retrieve the path to the Employees table.</span></span>

   ```powershell
   Get-Location
   ```

   ```Output
   Path
   ----
   mydb:\Employees
   ```

5. <span data-ttu-id="6625f-226">現在使用輸送至 `Format-Table` Cmdlet 的 `Get-Childitem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6625f-226">Now use the `Get-Childitem` cmdlet piped to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="6625f-227">這組 Cmdlet 會抓取 Employees 資料表的專案，這是資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="6625f-227">This set of cmdlets retrieves the items for the Employees data table, which are the table rows.</span></span> <span data-ttu-id="6625f-228">其格式如 `Format-Table` Cmdlet 所指定。</span><span class="sxs-lookup"><span data-stu-id="6625f-228">They are formatted as specified by the `Format-Table` cmdlet.</span></span>

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

6. <span data-ttu-id="6625f-229">您現在可以執行 `Get-Item` Cmdlet 來抓取 employee 資料表的資料列0的專案。</span><span class="sxs-lookup"><span data-stu-id="6625f-229">You can now run the `Get-Item` cmdlet to retrieve the items for row 0 of the Employees data table.</span></span>

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

7. <span data-ttu-id="6625f-230">再次使用 `Get-Item` Cmdlet，以取得資料列0中專案的員工資料。</span><span class="sxs-lookup"><span data-stu-id="6625f-230">Use the `Get-Item` cmdlet again to retrieve the employee data for the items in row 0.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6625f-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6625f-231">See Also</span></span>

[<span data-ttu-id="6625f-232">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6625f-232">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="6625f-233">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6625f-233">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

<span data-ttu-id="6625f-234">[擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6625f-234">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

[<span data-ttu-id="6625f-235">執行容器 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6625f-235">Implement a Container Windows PowerShell provider</span></span>](./creating-a-windows-powershell-container-provider.md)

<span data-ttu-id="6625f-236">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6625f-236">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="6625f-237">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="6625f-237">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6625f-238">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6625f-238">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
