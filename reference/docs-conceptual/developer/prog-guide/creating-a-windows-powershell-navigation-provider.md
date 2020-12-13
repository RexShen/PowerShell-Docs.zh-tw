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
# <a name="creating-a-windows-powershell-navigation-provider"></a><span data-ttu-id="44544-103">建立 Windows PowerShell 瀏覽提供者</span><span class="sxs-lookup"><span data-stu-id="44544-103">Creating a Windows PowerShell Navigation Provider</span></span>

<span data-ttu-id="44544-104">本主題說明如何建立可流覽資料存放區的 Windows PowerShell 流覽提供者。</span><span class="sxs-lookup"><span data-stu-id="44544-104">This topic describes how to create a Windows PowerShell navigation provider that can navigate the data store.</span></span> <span data-ttu-id="44544-105">這種類型的提供者支援遞迴命令、嵌套的容器和相對路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-105">This type of provider supports recursive commands, nested containers, and relative paths.</span></span>

> [!NOTE]
> <span data-ttu-id="44544-106">您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此提供者的 c # 原始程式檔 (AccessDBSampleProvider05.cs) 。</span><span class="sxs-lookup"><span data-stu-id="44544-106">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="44544-107">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="44544-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="44544-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="44544-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="44544-109">如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="44544-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="44544-110">此處所述的提供者可讓使用者將 Access 資料庫當作磁片磁碟機來處理，讓使用者可以流覽至資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="44544-110">The provider described here enables the user handle an Access database as a drive so that the user can navigate to the data tables in the database.</span></span> <span data-ttu-id="44544-111">建立您自己的流覽提供者時，您可以執行方法來建立導覽所需的磁片磁碟機路徑、將相對路徑標準化、移動資料存放區的專案，以及取得子名稱的方法、取得專案的父路徑，以及測試以識別專案是否為容器。</span><span class="sxs-lookup"><span data-stu-id="44544-111">When creating your own navigation provider, you can implement methods that can make drive-qualified paths required for navigation, normalize relative paths, move items of the data store, as well as methods that get child names, get the parent path of an item, and test to identify if an item is a container.</span></span>

> [!CAUTION]
> <span data-ttu-id="44544-112">請注意，此設計假設有一個具有名稱識別碼之欄位的資料庫，以及欄位的類型為 LongInteger。</span><span class="sxs-lookup"><span data-stu-id="44544-112">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

## <a name="define-the-windows-powershell-provider"></a><span data-ttu-id="44544-113">定義 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="44544-113">Define the Windows PowerShell provider</span></span>

<span data-ttu-id="44544-114">Windows PowerShell 的流覽提供者必須建立一個衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 基類的 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="44544-114">A Windows PowerShell navigation provider must create a .NET class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="44544-115">以下是本節所述之導覽提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="44544-115">Here is the class definition for the navigation provider described in this section.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="31-32":::

<span data-ttu-id="44544-116">請注意，在此提供者中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="44544-116">Note that in this provider, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="44544-117">第一個參數會指定 Windows PowerShell 所使用之提供者的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="44544-117">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="44544-118">第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="44544-118">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="44544-119">對於此提供者，不會新增 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="44544-119">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="44544-120">定義基底功能</span><span class="sxs-lookup"><span data-stu-id="44544-120">Defining Base Functionality</span></span>

<span data-ttu-id="44544-121">如 [設計您的 PS 提供者](./designing-your-windows-powershell-provider.md)所述， [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 基類衍生自數個提供不同提供者功能的其他類別。</span><span class="sxs-lookup"><span data-stu-id="44544-121">As described in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="44544-122">因此，Windows PowerShell 的流覽提供者必須定義這些類別所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="44544-122">A Windows PowerShell navigation provider, therefore, must define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="44544-123">若要執行新增會話特定初始化資訊，以及釋出提供者所使用之資源的功能，請參閱 [建立基本的 PS 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="44544-123">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic PS Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="44544-124">不過，大部分的提供者 (包括此處所述的提供者) 可以使用 Windows PowerShell 所提供的這項功能的預設執行。</span><span class="sxs-lookup"><span data-stu-id="44544-124">However, most providers (including the provider described here) can use the default implementation of this functionality provided by Windows PowerShell.</span></span>

<span data-ttu-id="44544-125">若要透過 Windows PowerShell 磁片磁碟機取得資料存放區的存取權，您必須執行 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 基類的方法。</span><span class="sxs-lookup"><span data-stu-id="44544-125">To get access to the data store through a Windows PowerShell drive, you must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="44544-126">如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="44544-126">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="44544-127">若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="44544-127">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="44544-128">如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="44544-128">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="44544-129">若要取得資料存放區的子專案或其名稱，以及建立、複製、重新命名和移除專案的方法，您必須先執行 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 基類所提供的方法（base class）。</span><span class="sxs-lookup"><span data-stu-id="44544-129">To get to the child items, or their names, of the data store, as well as methods that create, copy, rename, and remove items, you must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="44544-130">如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="44544-130">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

## <a name="creating-a-windows-powershell-path"></a><span data-ttu-id="44544-131">建立 Windows PowerShell 路徑</span><span class="sxs-lookup"><span data-stu-id="44544-131">Creating a Windows PowerShell Path</span></span>

<span data-ttu-id="44544-132">Windows PowerShell 流覽提供者會使用提供者內部 Windows PowerShell 路徑來導覽資料存放區的專案。</span><span class="sxs-lookup"><span data-stu-id="44544-132">Windows PowerShell navigation provider use a provider-internal Windows PowerShell path to navigate the items of the data store.</span></span> <span data-ttu-id="44544-133">若要建立提供者內部路徑，提供者必須執行 [>navigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 方法，以支援來自 Combine-Path Cmdlet 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="44544-133">To create a provider-internal path the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to supports calls from the Combine-Path cmdlet.</span></span> <span data-ttu-id="44544-134">這個方法會使用父路徑與子路徑之間的提供者特定路徑分隔符號，將父系和子路徑結合成提供者內部路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-134">This method combines a parent and child path into a provider-internal path, using a provider-specific path separator between the parent and child paths.</span></span>

<span data-ttu-id="44544-135">預設的執行會以 "/" 或 " \\ " 做為路徑分隔符號，將路徑分隔符號正規化為 " \\ "，將父系和子路徑部分與分隔符號結合，然後傳回包含合併路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="44544-135">The default implementation takes paths with "/" or "\\" as the path separator, normalizes the path separator to "\\", combines the parent and child path parts with the separator between them, and then returns a string that contains the combined paths.</span></span>

<span data-ttu-id="44544-136">此流覽提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="44544-136">This navigation provider does not implement this method.</span></span> <span data-ttu-id="44544-137">但是，下列程式碼是 [>navigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 方法的預設實值。</span><span class="sxs-lookup"><span data-stu-id="44544-137">However, the following code is the default implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a><span data-ttu-id="44544-138">執行 MakePath 的注意事項</span><span class="sxs-lookup"><span data-stu-id="44544-138">Things to Remember About Implementing MakePath</span></span>

<span data-ttu-id="44544-139">下列情況可能適用于您的 [>navigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)的執行：</span><span class="sxs-lookup"><span data-stu-id="44544-139">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span></span>

- <span data-ttu-id="44544-140">您的 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 方法不應該將路徑驗證為提供者命名空間中合法的完整路徑，以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="44544-140">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method should not validate the path as a legal fully-qualified path in the provider namespace.</span></span> <span data-ttu-id="44544-141">請注意，每個參數只能代表路徑的一部分，而組合的部分可能不會產生完整的路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-141">Be aware that each parameter can only represent a part of a path, and the combined parts might not generate a fully-qualified path.</span></span> <span data-ttu-id="44544-142">例如，filesystem 提供者的 [>navigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 方法可能會在參數中接收 "windows\system32" `parent` ，並在參數中接收 "abc.dll" `child` 。</span><span class="sxs-lookup"><span data-stu-id="44544-142">For example, the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method for the filesystem provider might receive "windows\system32" in the `parent` parameter and "abc.dll" in the `child` parameter.</span></span> <span data-ttu-id="44544-143">方法會使用 "" 分隔符號來聯結這些值， \\ 並傳回 "windows\system32\abc.dll"，這不是完整的檔案系統路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-143">The method joins these values with the "\\" separator and returns "windows\system32\abc.dll", which is not a fully-qualified file system path.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="44544-144">[>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)中所提供的路徑部分可能包含提供者命名空間中不允許的字元數。</span><span class="sxs-lookup"><span data-stu-id="44544-144">The path parts provided in the call to [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) might contain characters not allowed in the provider namespace.</span></span> <span data-ttu-id="44544-145">這些字元最有可能用於萬用字元展開，而此方法的執行不應移除它們。</span><span class="sxs-lookup"><span data-stu-id="44544-145">These characters are most likely used for wildcard expansion and the implementation of this method should not remove them.</span></span>

## <a name="retrieving-the-parent-path"></a><span data-ttu-id="44544-146">正在抓取父路徑</span><span class="sxs-lookup"><span data-stu-id="44544-146">Retrieving the Parent Path</span></span>

<span data-ttu-id="44544-147">Windows PowerShell 導覽提供者會執行 [>navigationCmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 方法，以取得指定之完整或部分提供者特定路徑的父部分。</span><span class="sxs-lookup"><span data-stu-id="44544-147">Windows PowerShell navigation providers implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method to retrieve the parent part of the indicated full or partial provider-specific path.</span></span> <span data-ttu-id="44544-148">方法會移除路徑的子部分，並傳回父路徑部分。</span><span class="sxs-lookup"><span data-stu-id="44544-148">The method removes the child part of the path and returns the parent path part.</span></span> <span data-ttu-id="44544-149">`root`參數會指定磁片磁碟機根目錄的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-149">The `root` parameter specifies the fully-qualified path to the root of a drive.</span></span> <span data-ttu-id="44544-150">如果載入的磁片磁碟機未用於抓取作業，這個參數可以是 null 或空的。</span><span class="sxs-lookup"><span data-stu-id="44544-150">This parameter can be null or empty if a mounted drive is not in use for the retrieval operation.</span></span> <span data-ttu-id="44544-151">如果指定了根，則方法必須傳回與根目錄相同樹狀結構中容器的路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-151">If a root is specified, the method must return a path to a container in the same tree as the root.</span></span>

<span data-ttu-id="44544-152">範例流覽提供者不會覆寫這個方法，而是使用預設的實值。</span><span class="sxs-lookup"><span data-stu-id="44544-152">The sample navigation provider does not override this method, but uses the default implementation.</span></span>
<span data-ttu-id="44544-153">它接受使用 "/" 和 " \\ " 做為路徑分隔符號的路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-153">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="44544-154">它會先將路徑正規化為只有 " \\ " 分隔符號，然後將父路徑分割為最後一個 " \\ "，並傳回父路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-154">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the parent path.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a><span data-ttu-id="44544-155">若要記住如何執行 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="44544-155">To Remember About Implementing GetParentPath</span></span>

<span data-ttu-id="44544-156">[>navigationCmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法的執行應該針對提供者命名空間的路徑分隔符號，以詞法方式分割路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-156">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method should split the path lexically on the path separator for the provider namespace.</span></span> <span data-ttu-id="44544-157">例如，filesystem 提供者會使用這個方法來尋找最後的 " \\ "，並傳回分隔符號左邊的所有專案。</span><span class="sxs-lookup"><span data-stu-id="44544-157">For example, the filesystem provider uses this method to look for the last "\\" and returns everything to the left of the separator.</span></span>

## <a name="retrieve-the-child-path-name"></a><span data-ttu-id="44544-158">取出子路徑名稱</span><span class="sxs-lookup"><span data-stu-id="44544-158">Retrieve the Child Path Name</span></span>

<span data-ttu-id="44544-159">您的流覽提供者會 [>navigationCmdletprovider Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 方法，以抓取位於指定的完整或部分提供者特定路徑之專案子系的名稱 (分葉元素) 。</span><span class="sxs-lookup"><span data-stu-id="44544-159">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method to retrieve the name (leaf element) of the child of the item located at the indicated full or partial provider-specific path.</span></span>

<span data-ttu-id="44544-160">範例流覽提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="44544-160">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="44544-161">預設的執行如下所示。</span><span class="sxs-lookup"><span data-stu-id="44544-161">The default implementation is shown below.</span></span> <span data-ttu-id="44544-162">它接受使用 "/" 和 " \\ " 做為路徑分隔符號的路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-162">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="44544-163">它會先將路徑正規化為只有 " \\ " 分隔符號，然後將父路徑分割為最後一個 " \\ "，並傳回子路徑部分的名稱。</span><span class="sxs-lookup"><span data-stu-id="44544-163">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the name of the child path part.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a><span data-ttu-id="44544-164">執行 GetChildName 的注意事項</span><span class="sxs-lookup"><span data-stu-id="44544-164">Things to Remember About Implementing GetChildName</span></span>

<span data-ttu-id="44544-165">[>navigationCmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法的執行應該在路徑分隔符號上以詞法方式分割路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-165">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method should split the path lexically on the path separator.</span></span> <span data-ttu-id="44544-166">如果提供的路徑不包含任何路徑分隔符號，則方法應傳回未修改的路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-166">If the supplied path contains no path separators, the method should return the path unmodified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44544-167">呼叫這個方法時所提供的路徑可能包含在提供者命名空間中不合法的字元。</span><span class="sxs-lookup"><span data-stu-id="44544-167">The path provided in the call to this method might contain characters that are illegal in the provider namespace.</span></span> <span data-ttu-id="44544-168">這些字元最有可能用於萬用字元展開或正則運算式比對，而此方法的執行不應移除它們。</span><span class="sxs-lookup"><span data-stu-id="44544-168">These characters are most likely used for wildcard expansion or regular expression matching, and the implementation of this method should not remove them.</span></span>

## <a name="determining-if-an-item-is-a-container"></a><span data-ttu-id="44544-169">判斷專案是否為容器</span><span class="sxs-lookup"><span data-stu-id="44544-169">Determining if an Item is a Container</span></span>

<span data-ttu-id="44544-170">流覽提供者可以執行 [>navigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 方法，以判斷指定的路徑是否表示容器。</span><span class="sxs-lookup"><span data-stu-id="44544-170">The navigation provider can implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method to determine if the specified path indicates a container.</span></span> <span data-ttu-id="44544-171">如果路徑表示容器，則會傳回 true，否則會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="44544-171">It returns true if the path represents a container, and false otherwise.</span></span> <span data-ttu-id="44544-172">使用者需要此方法才能 `Test-Path` 針對提供的路徑使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="44544-172">The user needs this method to be able to use the `Test-Path` cmdlet for the supplied path.</span></span>

<span data-ttu-id="44544-173">下列程式碼顯示範例導覽提供者中的 [>navigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 實作為。</span><span class="sxs-lookup"><span data-stu-id="44544-173">The following code shows the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementation in our sample navigation provider.</span></span> <span data-ttu-id="44544-174">方法會驗證指定的路徑是否正確，以及資料表是否存在，如果路徑指出容器，則會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="44544-174">The method verifies that the specified path is correct and if the table exists, and returns true if the path indicates a container.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="847-872":::

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a><span data-ttu-id="44544-175">執行 IsItemContainer 的注意事項</span><span class="sxs-lookup"><span data-stu-id="44544-175">Things to Remember About Implementing IsItemContainer</span></span>

<span data-ttu-id="44544-176">您的流覽提供者 .NET 類別可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="44544-176">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="44544-177">在此情況下， [>navigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 的執行必須確保傳遞的路徑符合需求。</span><span class="sxs-lookup"><span data-stu-id="44544-177">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) needs to ensure that the path passed meets requirements.</span></span> <span data-ttu-id="44544-178">若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider. Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 屬性（property）。</span><span class="sxs-lookup"><span data-stu-id="44544-178">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) property.</span></span>

## <a name="moving-an-item"></a><span data-ttu-id="44544-179">移動專案</span><span class="sxs-lookup"><span data-stu-id="44544-179">Moving an Item</span></span>

<span data-ttu-id="44544-180">在支援 Cmdlet 時 `Move-Item` ，您的流覽提供者會執行 [>navigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 方法。</span><span class="sxs-lookup"><span data-stu-id="44544-180">In support of the `Move-Item` cmdlet, your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="44544-181">這個方法會將參數所指定的專案移 `path` 至參數中所提供路徑的容器 `destination` 。</span><span class="sxs-lookup"><span data-stu-id="44544-181">This method moves the item specified by the `path` parameter to the container at the path supplied in the `destination` parameter.</span></span>

<span data-ttu-id="44544-182">範例流覽提供者不會覆寫 [>navigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 方法。</span><span class="sxs-lookup"><span data-stu-id="44544-182">The sample navigation provider does not override the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="44544-183">以下是預設的執行。</span><span class="sxs-lookup"><span data-stu-id="44544-183">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a><span data-ttu-id="44544-184">執行 MoveItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="44544-184">Things to Remember About Implementing MoveItem</span></span>

<span data-ttu-id="44544-185">您的流覽提供者 .NET 類別可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="44544-185">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="44544-186">在此情況下， [>navigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 的執行必須確保傳遞的路徑符合需求。</span><span class="sxs-lookup"><span data-stu-id="44544-186">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) must ensure that the path passed meets requirements.</span></span> <span data-ttu-id="44544-187">若要這樣做，方法應該存取適當的屬性，例如 **CmdletProvider** 屬性。</span><span class="sxs-lookup"><span data-stu-id="44544-187">To do this, the method should access the appropriate property, for example, the **CmdletProvider.Exclude** property.</span></span>

<span data-ttu-id="44544-188">根據預設，除非 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則此方法的覆寫不應將物件移至現有的物件 `true` 。</span><span class="sxs-lookup"><span data-stu-id="44544-188">By default, overrides of this method should not move objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="44544-189">例如，filesystem 提供者不會將 c:\temp\abc.txt 複製到現有的 c:\bar.txt 檔案，除非 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="44544-189">For example, the filesystem provider will not copy c:\temp\abc.txt over an existing c:\bar.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="44544-190">如果參數中所指定的路徑 `destination` 存在且為容器，則不需要 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性。</span><span class="sxs-lookup"><span data-stu-id="44544-190">If the path specified in the `destination` parameter exists and is a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="44544-191">在此情況下， [>navigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 應該將參數所指示的專案移 `path` 至參數所指示的容器 `destination` 做為子系。</span><span class="sxs-lookup"><span data-stu-id="44544-191">In this case, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) should move the item indicated by the `path` parameter to the container indicated by the `destination` parameter as a child.</span></span>

<span data-ttu-id="44544-192">您的 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並檢查其傳回值，然後才執行。</span><span class="sxs-lookup"><span data-stu-id="44544-192">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="44544-193">當對系統狀態進行變更（例如刪除檔案）時，此方法會用來確認執行作業。</span><span class="sxs-lookup"><span data-stu-id="44544-193">This method is used to confirm execution of an operation when a change is made to system state, for example, deleting files.</span></span>
<span data-ttu-id="44544-194">[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 會傳送要變更給使用者的資源名稱，且 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入考慮，以決定應該向使用者顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="44544-194">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="44544-195">呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) `true` 會傳回， [>navigationCmdletprovider.. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 方法應該呼叫 [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ，以呼叫 system.object.. \* 方法來呼叫. 管理方法。</span><span class="sxs-lookup"><span data-stu-id="44544-195">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="44544-196">這個方法會將訊息傳送給使用者，以允許意見反應指出作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="44544-196">This method sends a message to the user to allow feedback to say if the operation should be continued.</span></span> <span data-ttu-id="44544-197">您的提供者應該呼叫 [Cmdletprovider ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 做為額外檢查是否有潛在危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="44544-197">Your provider should call [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a><span data-ttu-id="44544-198">將動態參數附加至 Move-Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="44544-198">Attaching Dynamic Parameters to the Move-Item Cmdlet</span></span>

<span data-ttu-id="44544-199">有時 `Move-Item` Cmdlet 需要在執行時間動態提供的額外參數。</span><span class="sxs-lookup"><span data-stu-id="44544-199">Sometimes the `Move-Item` cmdlet requires additional parameters that are provided dynamically at runtime.</span></span> <span data-ttu-id="44544-200">若要提供這些動態參數，流覽提供者必須執行 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) ，以從指定路徑的專案中取得必要的參數值，並傳回物件，該物件具有剖析屬性（attribute）的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。</span><span class="sxs-lookup"><span data-stu-id="44544-200">To provide these dynamic parameters, the navigation provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method to get the required parameter values from the item at the indicated path, and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="44544-201">此流覽提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="44544-201">This navigation provider does not implement this method.</span></span> <span data-ttu-id="44544-202">但是，下列程式碼是 [>navigationCmdletprovider. Moveitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)的預設執行。</span><span class="sxs-lookup"><span data-stu-id="44544-202">However, the following code is the default implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a><span data-ttu-id="44544-203">標準化相對路徑</span><span class="sxs-lookup"><span data-stu-id="44544-203">Normalizing a Relative Path</span></span>

<span data-ttu-id="44544-204">您的流覽提供者會實 [>navigationCmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 方法，將參數中指出的完整路徑正規化為 `path` 相對於參數所指定的路徑 `basePath` 。</span><span class="sxs-lookup"><span data-stu-id="44544-204">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method to normalize the fully-qualified path indicated in the `path` parameter as being relative to the path specified by the `basePath` parameter.</span></span> <span data-ttu-id="44544-205">方法會傳回正規化路徑的字串表示。</span><span class="sxs-lookup"><span data-stu-id="44544-205">The method returns a string representation of the normalized path.</span></span> <span data-ttu-id="44544-206">如果參數指定的路徑不存在，則會寫入錯誤 `path` 。</span><span class="sxs-lookup"><span data-stu-id="44544-206">It writes an error if the `path` parameter specifies a nonexistent path.</span></span>

<span data-ttu-id="44544-207">範例流覽提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="44544-207">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="44544-208">以下是預設的執行。</span><span class="sxs-lookup"><span data-stu-id="44544-208">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a><span data-ttu-id="44544-209">執行 NormalizeRelativePath 的注意事項</span><span class="sxs-lookup"><span data-stu-id="44544-209">Things to Remember About Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="44544-210">您的 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 必須剖析 `path` 參數，但不一定要使用純粹的語法剖析，而是您的執行。</span><span class="sxs-lookup"><span data-stu-id="44544-210">Your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) should parse the `path` parameter, but it does not have to use purely syntactical parsing.</span></span> <span data-ttu-id="44544-211">建議您將此方法設計為使用路徑來查閱資料存放區中的路徑資訊，並建立符合大小寫和標準化路徑語法的路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-211">You are encouraged to design this method to use the path to look up the path information in the data store and create a path that matches the casing and standardized path syntax.</span></span>

## <a name="code-sample"></a><span data-ttu-id="44544-212">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="44544-212">Code Sample</span></span>

<span data-ttu-id="44544-213">如需完整的範例程式碼，請參閱 [AccessDbProviderSample05 程式碼範例](./accessdbprovidersample05-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="44544-213">For complete sample code, see [AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="44544-214">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="44544-214">Defining Object Types and Formatting</span></span>

<span data-ttu-id="44544-215">提供者可能會將成員新增至現有的物件，或定義新的物件。</span><span class="sxs-lookup"><span data-stu-id="44544-215">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="44544-216">如需詳細資訊，請參閱[擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="44544-216">For more information, see[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="44544-217">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="44544-217">Building the Windows PowerShell provider</span></span>

<span data-ttu-id="44544-218">如需詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="44544-218">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="44544-219">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="44544-219">Testing the Windows PowerShell provider</span></span>

<span data-ttu-id="44544-220">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試，包括衍生所提供的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="44544-220">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including cmdlets made available by derivation.</span></span> <span data-ttu-id="44544-221">此範例將測試範例流覽提供者。</span><span class="sxs-lookup"><span data-stu-id="44544-221">This example will test the sample navigation provider.</span></span>

1. <span data-ttu-id="44544-222">執行新的命令介面，並使用指令程式 `Set-Location` 來設定路徑，以指出存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="44544-222">Run your new shell and use the `Set-Location` cmdlet to set the path to indicate the Access database.</span></span>

   ```powershell
   Set-Location mydb:
   ```

2. <span data-ttu-id="44544-223">現在 `Get-Childitem` ，請執行 Cmdlet 來取得資料庫專案的清單，這些專案是可用的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="44544-223">Now run the `Get-Childitem` cmdlet to retrieve a list of the database items, which are the available database tables.</span></span> <span data-ttu-id="44544-224">針對每個資料表，此 Cmdlet 也會抓取資料表資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="44544-224">For each table, this cmdlet also retrieves the number of table rows.</span></span>

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

3. <span data-ttu-id="44544-225">再次使用指令程式 `Set-Location` 來設定 Employees 資料表的位置。</span><span class="sxs-lookup"><span data-stu-id="44544-225">Use the `Set-Location` cmdlet again to set the location of the Employees data table.</span></span>

   ```powershell
   Set-Location Employees
   ```

4. <span data-ttu-id="44544-226">現在讓我們使用指令程式 `Get-Location` 來取出 employee 資料表的路徑。</span><span class="sxs-lookup"><span data-stu-id="44544-226">Let's now use the `Get-Location` cmdlet to retrieve the path to the Employees table.</span></span>

   ```powershell
   Get-Location
   ```

   ```Output
   Path
   ----
   mydb:\Employees
   ```

5. <span data-ttu-id="44544-227">現在使用 `Get-Childitem` 輸送至 Cmdlet 的 Cmdlet `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="44544-227">Now use the `Get-Childitem` cmdlet piped to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="44544-228">這組 Cmdlet 會抓取 employee 資料表的專案，這是資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="44544-228">This set of cmdlets retrieves the items for the Employees data table, which are the table rows.</span></span> <span data-ttu-id="44544-229">這些格式是由 Cmdlet 所指定 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="44544-229">They are formatted as specified by the `Format-Table` cmdlet.</span></span>

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

6. <span data-ttu-id="44544-230">您現在可以執行 `Get-Item` Cmdlet，以抓取員工資料表中的資料列0專案。</span><span class="sxs-lookup"><span data-stu-id="44544-230">You can now run the `Get-Item` cmdlet to retrieve the items for row 0 of the Employees data table.</span></span>

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

7. <span data-ttu-id="44544-231">再次使用指令 `Get-Item` 程式，以取得資料列0中專案的員工資料。</span><span class="sxs-lookup"><span data-stu-id="44544-231">Use the `Get-Item` cmdlet again to retrieve the employee data for the items in row 0.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="44544-232">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44544-232">See Also</span></span>

[<span data-ttu-id="44544-233">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="44544-233">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="44544-234">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="44544-234">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

<span data-ttu-id="44544-235">[擴充物件類型和格式化](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="44544-235">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

[<span data-ttu-id="44544-236">執行容器 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="44544-236">Implement a Container Windows PowerShell provider</span></span>](./creating-a-windows-powershell-container-provider.md)

<span data-ttu-id="44544-237">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="44544-237">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="44544-238">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="44544-238">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="44544-239">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="44544-239">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
