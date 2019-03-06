---
title: 建立 Windows PowerShell 巡覽提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: cbc8ce0600553f9e9ab973d6f92ea5eafde310e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430023"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a><span data-ttu-id="1474f-102">建立 Windows PowerShell 瀏覽提供者</span><span class="sxs-lookup"><span data-stu-id="1474f-102">Creating a Windows PowerShell Navigation Provider</span></span>

<span data-ttu-id="1474f-103">本主題描述如何建立 Windows PowerShell 巡覽提供者，可以瀏覽資料存放區。</span><span class="sxs-lookup"><span data-stu-id="1474f-103">This topic describes how to create a Windows PowerShell navigation provider that can navigate the data store.</span></span> <span data-ttu-id="1474f-104">這種類型的提供者支援遞迴命令，巢狀的容器和相對路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-104">This type of provider supports recursive commands, nested containers, and relative paths.</span></span>

> [!NOTE]
> <span data-ttu-id="1474f-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此提供者的原始程式檔 (AccessDBSampleProvider05.cs)。</span><span class="sxs-lookup"><span data-stu-id="1474f-105">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1474f-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="1474f-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1474f-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="1474f-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="1474f-108">如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="1474f-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="1474f-109">此處所述的提供者可讓使用者控制代碼的 Access 資料庫做為磁碟機，以便使用者瀏覽至資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="1474f-109">The provider described here enables the user handle an Access database as a drive so that the user can navigate to the data tables in the database.</span></span> <span data-ttu-id="1474f-110">當建立您自己的巡覽提供者，您可以實作方法，可讓瀏覽所需的磁碟機限定路徑、 相對路徑正規化，移動的資料存放區，以及取得子系名稱，取得父路徑的項目，且測試方法的項目若要識別的項目是一個容器。</span><span class="sxs-lookup"><span data-stu-id="1474f-110">When creating your own navigation provider, you can implement methods that can make drive-qualified paths required for navigation, normalize relative paths, move items of the data store, as well as methods that get child names, get the parent path of an item, and test to identify if an item is a container.</span></span>

> [!CAUTION]
> <span data-ttu-id="1474f-111">請注意，這項設計會假設的欄位有名稱識別碼的資料庫和欄位的型別是 LongInteger。</span><span class="sxs-lookup"><span data-stu-id="1474f-111">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

<span data-ttu-id="1474f-112">下列清單包含本主題中的區段。</span><span class="sxs-lookup"><span data-stu-id="1474f-112">The following list includes sections in this topic.</span></span> <span data-ttu-id="1474f-113">如果您不熟悉如何撰寫 Windows PowerShell 巡覽提供者，請閱讀這項資訊，它會出現的順序。</span><span class="sxs-lookup"><span data-stu-id="1474f-113">If you are unfamiliar with writing a Windows PowerShell navigation provider, read this information in the order that it appears.</span></span> <span data-ttu-id="1474f-114">不過，如果您已熟悉撰寫 Windows PowerShell 巡覽提供者，請直接前往您所需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="1474f-114">However, if you are familiar with writing a Windows PowerShell navigation provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="1474f-115">定義的 PS 導覽提供者類別</span><span class="sxs-lookup"><span data-stu-id="1474f-115">Defining a PS Navigation Provider Class</span></span>](#Define-the-Windows-PowerShell-provider)

- [<span data-ttu-id="1474f-116">定義基底的功能</span><span class="sxs-lookup"><span data-stu-id="1474f-116">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="1474f-117">建立 PS 路徑</span><span class="sxs-lookup"><span data-stu-id="1474f-117">Creating a PS Path</span></span>](#Creating-a-Windows-PowerShell-Path)

- [<span data-ttu-id="1474f-118">正在擷取父路徑</span><span class="sxs-lookup"><span data-stu-id="1474f-118">Retrieving the Parent Path</span></span>](#Retrieving-the-Parent-Path)

- [<span data-ttu-id="1474f-119">擷取的子路徑名稱</span><span class="sxs-lookup"><span data-stu-id="1474f-119">Retrieving the Child Path Name</span></span>](#Retrieve-the-Child-Path-Name)

- [<span data-ttu-id="1474f-120">判斷項目是否為容器</span><span class="sxs-lookup"><span data-stu-id="1474f-120">Determining if an Item is a Container</span></span>](#Determining-if-an-Item-is-a-Container)

- [<span data-ttu-id="1474f-121">移動項目</span><span class="sxs-lookup"><span data-stu-id="1474f-121">Moving an Item</span></span>](#Moving-an-Item)

- [<span data-ttu-id="1474f-122">附加到的動態參數`Move-Item`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1474f-122">Attaching Dynamic Parameters to the `Move-Item` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [<span data-ttu-id="1474f-123">相對路徑正規化</span><span class="sxs-lookup"><span data-stu-id="1474f-123">Normalizing a Relative Path</span></span>](#Normalizing-a-Relative-Path)

- [<span data-ttu-id="1474f-124">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="1474f-124">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="1474f-125">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="1474f-125">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="1474f-126">建置 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1474f-126">Building the Windows PowerShell Provider</span></span>](#Building-the-Windows-PowerShell-provider)

- [<span data-ttu-id="1474f-127">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1474f-127">Testing the Windows PowerShell Provider</span></span>](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a><span data-ttu-id="1474f-128">定義 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1474f-128">Define the Windows PowerShell provider</span></span>

<span data-ttu-id="1474f-129">Windows PowerShell 巡覽提供者必須建立一個.NET 類別衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="1474f-129">A Windows PowerShell navigation provider must create a .NET class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="1474f-130">以下是這一節所述的瀏覽提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="1474f-130">Here is the class definition for the navigation provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

<span data-ttu-id="1474f-131">請注意，在此提供者[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="1474f-131">Note that in this provider, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="1474f-132">第一個參數會指定使用 Windows powershell 提供者的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="1474f-132">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="1474f-133">第二個參數指定命令處理期間提供者會公開 Windows PowerShell 執行階段的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="1474f-133">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="1474f-134">此提供者，如有加入任何 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="1474f-134">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="1474f-135">定義基底的功能</span><span class="sxs-lookup"><span data-stu-id="1474f-135">Defining Base Functionality</span></span>

<span data-ttu-id="1474f-136">中所述[設計您的 PS Provider](./designing-your-windows-powershell-provider.md)，則[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基底類別衍生自數個其他類別，提供不同的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="1474f-136">As described in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="1474f-137">Windows PowerShell 巡覽提供者，因此，必須定義所有這些類別所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="1474f-137">A Windows PowerShell navigation provider, therefore, must define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="1474f-138">若要實作功能，說明如何加入工作階段特定的初始化資訊，以及用於釋放提供者所使用的資源，請參閱[建立基本的 PS 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="1474f-138">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic PS Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="1474f-139">不過，大部分的提供者 （包括此處所述的提供者） 可以使用這項功能 Windows PowerShell 所提供的預設實作。</span><span class="sxs-lookup"><span data-stu-id="1474f-139">However, most providers (including the provider described here) can use the default implementation of this functionality provided by Windows PowerShell.</span></span>

<span data-ttu-id="1474f-140">若要存取資料存放區透過 Windows PowerShell 磁碟機，您必須實作的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="1474f-140">To get access to the data store through a Windows PowerShell drive, you must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="1474f-141">如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="1474f-141">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="1474f-142">若要操作的資料存放區，例如開始、 設定和清除項目，項目的提供者必須實作所提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="1474f-142">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="1474f-143">如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="1474f-143">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="1474f-144">取得子系的項目或其名稱、 資料存放區，以及建立、 複製、 重新命名，然後移除項目，方法中，您必須實作所提供的方法[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="1474f-144">To get to the child items, or their names, of the data store, as well as methods that create, copy, rename, and remove items, you must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="1474f-145">如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="1474f-145">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

## <a name="creating-a-windows-powershell-path"></a><span data-ttu-id="1474f-146">建立 Windows PowerShell 路徑</span><span class="sxs-lookup"><span data-stu-id="1474f-146">Creating a Windows PowerShell Path</span></span>

<span data-ttu-id="1474f-147">Windows PowerShell 巡覽提供者會使用提供者內部的 Windows PowerShell 路徑來瀏覽資料存放區的項目。</span><span class="sxs-lookup"><span data-stu-id="1474f-147">Windows PowerShell navigation provider use a provider-internal Windows PowerShell path to navigate the items of the data store.</span></span> <span data-ttu-id="1474f-148">若要建立的提供者內部路徑提供者必須實作[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)支援的方法呼叫從合併路徑 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1474f-148">To create a provider-internal path the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to supports calls from the Combine-Path cmdlet.</span></span> <span data-ttu-id="1474f-149">這個方法會將父和子路徑結合成一個提供者內部的路徑，使用提供者專屬的路徑分隔符號之間的父和子路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-149">This method combines a parent and child path into a provider-internal path, using a provider-specific path separator between the parent and child paths.</span></span>

<span data-ttu-id="1474f-150">預設實作會使用路徑"/"或"\\"做為路徑分隔符號，將正規化路徑分隔符號，「\\」 結合它們之間的分隔符號中的父和子路徑的任何部分，則會傳回字串，包含合併的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-150">The default implementation takes paths with "/" or "\\" as the path separator, normalizes the path separator to "\\", combines the parent and child path parts with the separator between them, and then returns a string that contains the combined paths.</span></span>

<span data-ttu-id="1474f-151">此瀏覽提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="1474f-151">This navigation provider does not implement this method.</span></span> <span data-ttu-id="1474f-152">不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法。</span><span class="sxs-lookup"><span data-stu-id="1474f-152">However, the following code is the default implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a><span data-ttu-id="1474f-153">有關實作 MakePath 的注意事項</span><span class="sxs-lookup"><span data-stu-id="1474f-153">Things to Remember About Implementing MakePath</span></span>

<span data-ttu-id="1474f-154">在下列情況可能適用於您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span><span class="sxs-lookup"><span data-stu-id="1474f-154">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span></span>

- <span data-ttu-id="1474f-155">您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法不應驗證為合法完整路徑，提供者命名空間中的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-155">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method should not validate the path as a legal fully-qualified path in the provider namespace.</span></span> <span data-ttu-id="1474f-156">請注意，每個參數只能代表路徑的一部分，並合併組件可能不會產生完整的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-156">Be aware that each parameter can only represent a part of a path, and the combined parts might not generate a fully-qualified path.</span></span> <span data-ttu-id="1474f-157">例如， [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) filesystem 提供者的方法中可能會收到 「 windows\system32"`parent`參數和 「 abc.dll"中的`child`參數。</span><span class="sxs-lookup"><span data-stu-id="1474f-157">For example, the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method for the filesystem provider might receive "windows\system32" in the `parent` parameter and "abc.dll" in the `child` parameter.</span></span> <span data-ttu-id="1474f-158">方法會加入這些值取代"\\」 分隔符號，並傳回 「 windows\system32\abc.dll"，也就是不完整的檔案系統路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-158">The method joins these values with the "\\" separator and returns "windows\system32\abc.dll", which is not a fully-qualified file system path.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="1474f-159">呼叫中提供的路徑部分[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)可能包含提供者命名空間中不允許的字元。</span><span class="sxs-lookup"><span data-stu-id="1474f-159">The path parts provided in the call to [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) might contain characters not allowed in the provider namespace.</span></span> <span data-ttu-id="1474f-160">這些字元會很有可能會用於萬用字元展開，而且此方法的實作不應該移除它們。</span><span class="sxs-lookup"><span data-stu-id="1474f-160">These characters are most likely used for wildcard expansion and the implementation of this method should not remove them.</span></span>

## <a name="retrieving-the-parent-path"></a><span data-ttu-id="1474f-161">正在擷取父路徑</span><span class="sxs-lookup"><span data-stu-id="1474f-161">Retrieving the Parent Path</span></span>

<span data-ttu-id="1474f-162">Windows PowerShell 巡覽提供者可實作[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法來擷取父組件所指定完整或部分提供者專屬的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-162">Windows PowerShell navigation providers implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method to retrieve the parent part of the indicated full or partial provider-specific path.</span></span> <span data-ttu-id="1474f-163">方法會移除子路徑的一部分，並傳回父系的路徑部分。</span><span class="sxs-lookup"><span data-stu-id="1474f-163">The method removes the child part of the path and returns the parent path part.</span></span> <span data-ttu-id="1474f-164">`root`參數指定磁碟機根目錄的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-164">The `root` parameter specifies the fully-qualified path to the root of a drive.</span></span> <span data-ttu-id="1474f-165">這個參數可以是 null 或空白，如果掛接的磁碟機不是用於擷取作業。</span><span class="sxs-lookup"><span data-stu-id="1474f-165">This parameter can be null or empty if a mounted drive is not in use for the retrieval operation.</span></span> <span data-ttu-id="1474f-166">如果指定的根，則此方法必須傳回路徑，以 root 身分執行的相同樹狀結構中的容器。</span><span class="sxs-lookup"><span data-stu-id="1474f-166">If a root is specified, the method must return a path to a container in the same tree as the root.</span></span>

<span data-ttu-id="1474f-167">範例導覽提供者未覆寫這個方法，但使用的預設實作。</span><span class="sxs-lookup"><span data-stu-id="1474f-167">The sample navigation provider does not override this method, but uses the default implementation.</span></span> <span data-ttu-id="1474f-168">它可接受同時使用的路徑"/"和"\\」 做為路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="1474f-168">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="1474f-169">第一次將正規化路徑只有 「\\"分隔符號，然後將關閉的父路徑分割最後一個"\\"，並傳回父路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-169">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the parent path.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a><span data-ttu-id="1474f-170">要記住關於實作 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="1474f-170">To Remember About Implementing GetParentPath</span></span>

<span data-ttu-id="1474f-171">您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法應該分割語彙上提供者命名空間的路徑分隔符號的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-171">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method should split the path lexically on the path separator for the provider namespace.</span></span> <span data-ttu-id="1474f-172">例如，filesystem 提供者會使用這個方法來尋找上次"\\」，並傳回所有項目分隔符號的左邊。</span><span class="sxs-lookup"><span data-stu-id="1474f-172">For example, the filesystem provider uses this method to look for the last "\\" and returns everything to the left of the separator.</span></span>

## <a name="retrieve-the-child-path-name"></a><span data-ttu-id="1474f-173">擷取的子路徑名稱</span><span class="sxs-lookup"><span data-stu-id="1474f-173">Retrieve the Child Path Name</span></span>

<span data-ttu-id="1474f-174">您的瀏覽提供者會實作[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法來擷取項目的子系的名稱 （分葉項目） 位於指定完整或部分提供者專屬的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-174">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method to retrieve the name (leaf element) of the child of the item located at the indicated full or partial provider-specific path.</span></span>

<span data-ttu-id="1474f-175">範例導覽提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="1474f-175">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="1474f-176">如下所示的預設實作。</span><span class="sxs-lookup"><span data-stu-id="1474f-176">The default implementation is shown below.</span></span> <span data-ttu-id="1474f-177">它可接受同時使用的路徑"/"和"\\」 做為路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="1474f-177">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="1474f-178">第一次將正規化路徑只有 「\\"分隔符號，然後將關閉的父路徑分割最後一個"\\"，並傳回子物件名稱的路徑部分。</span><span class="sxs-lookup"><span data-stu-id="1474f-178">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the name of the child path part.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a><span data-ttu-id="1474f-179">有關實作 GetChildName 的注意事項</span><span class="sxs-lookup"><span data-stu-id="1474f-179">Things to Remember About Implementing GetChildName</span></span>

<span data-ttu-id="1474f-180">您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法應該分割上的路徑分隔符號語彙的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-180">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method should split the path lexically on the path separator.</span></span> <span data-ttu-id="1474f-181">如果提供的路徑不包含任何路徑分隔符號，則此方法應該傳回未經修改的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-181">If the supplied path contains no path separators, the method should return the path unmodified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1474f-182">這個方法的呼叫中提供的路徑可能會包含在提供者命名空間中不合法的字元。</span><span class="sxs-lookup"><span data-stu-id="1474f-182">The path provided in the call to this method might contain characters that are illegal in the provider namespace.</span></span> <span data-ttu-id="1474f-183">這些字元最有可能用於萬用字元展開或規則運算式比對，而且此方法的實作不應該移除它們。</span><span class="sxs-lookup"><span data-stu-id="1474f-183">These characters are most likely used for wildcard expansion or regular expression matching, and the implementation of this method should not remove them.</span></span>

## <a name="determining-if-an-item-is-a-container"></a><span data-ttu-id="1474f-184">判斷項目是否為容器</span><span class="sxs-lookup"><span data-stu-id="1474f-184">Determining if an Item is a Container</span></span>

<span data-ttu-id="1474f-185">瀏覽提供者可實作[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)來判斷是否指定的路徑表示容器的方法。</span><span class="sxs-lookup"><span data-stu-id="1474f-185">The navigation provider can implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method to determine if the specified path indicates a container.</span></span> <span data-ttu-id="1474f-186">它會傳回路徑可代表容器和 false 否則如果為 true。</span><span class="sxs-lookup"><span data-stu-id="1474f-186">It returns true if the path represents a container, and false otherwise.</span></span> <span data-ttu-id="1474f-187">使用者必須要能夠使用這個方法`Test-Path`cmdlet 提供的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-187">The user needs this method to be able to use the `Test-Path` cmdlet for the supplied path.</span></span>

<span data-ttu-id="1474f-188">下列程式碼示範[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)我們的範例導覽提供者中實作。</span><span class="sxs-lookup"><span data-stu-id="1474f-188">The following code shows the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementation in our sample navigation provider.</span></span> <span data-ttu-id="1474f-189">此方法會驗證指定的路徑正確無誤，而且如果資料表存在，而且如果的路徑表示容器會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="1474f-189">The method verifies that  the specified path is correct and if the table exists, and returns true if the path indicates a container.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a><span data-ttu-id="1474f-190">有關實作 IsItemContainer 的注意事項</span><span class="sxs-lookup"><span data-stu-id="1474f-190">Things to Remember About Implementing IsItemContainer</span></span>

<span data-ttu-id="1474f-191">您的瀏覽提供者.NET 類別可以宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除，從[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="1474f-191">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="1474f-192">在此情況下，實作[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)必須確保傳遞路徑符合需求。</span><span class="sxs-lookup"><span data-stu-id="1474f-192">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) needs to ensure that the path passed meets requirements.</span></span> <span data-ttu-id="1474f-193">若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)屬性。</span><span class="sxs-lookup"><span data-stu-id="1474f-193">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) property.</span></span>

## <a name="moving-an-item"></a><span data-ttu-id="1474f-194">移動項目</span><span class="sxs-lookup"><span data-stu-id="1474f-194">Moving an Item</span></span>

<span data-ttu-id="1474f-195">支援`Move-Item`cmdlet，您的瀏覽提供者會實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。</span><span class="sxs-lookup"><span data-stu-id="1474f-195">In support of the `Move-Item` cmdlet, your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="1474f-196">這個方法會移動指定的項目`path`容器中所提供的路徑參數`destination`參數。</span><span class="sxs-lookup"><span data-stu-id="1474f-196">This method moves the item specified by the `path` parameter to the container at the path supplied in the `destination` parameter.</span></span>

<span data-ttu-id="1474f-197">範例導覽提供者不會覆寫[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。</span><span class="sxs-lookup"><span data-stu-id="1474f-197">The sample navigation provider does not override the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="1474f-198">以下是預設的實作。</span><span class="sxs-lookup"><span data-stu-id="1474f-198">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a><span data-ttu-id="1474f-199">有關實作 MoveItem 的注意事項</span><span class="sxs-lookup"><span data-stu-id="1474f-199">Things to Remember About Implementing MoveItem</span></span>

<span data-ttu-id="1474f-200">您的瀏覽提供者.NET 類別可以宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除，從[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="1474f-200">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="1474f-201">在此情況下，實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)必須確定傳遞路徑符合需求。</span><span class="sxs-lookup"><span data-stu-id="1474f-201">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) must ensure that the path passed meets requirements.</span></span> <span data-ttu-id="1474f-202">若要這樣做，方法應該存取適當的屬性，例如， **CmdletProvider.Exclude**屬性。</span><span class="sxs-lookup"><span data-stu-id="1474f-202">To do this, the method should access the appropriate property, for example, the **CmdletProvider.Exclude** property.</span></span>

<span data-ttu-id="1474f-203">根據預設，會覆寫這個方法不能移動物件現有的物件除非[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="1474f-203">By default, overrides of this method should not move objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="1474f-204">例如，filesystem 提供者不會複製 c:\temp\abc.txt 透過現有 c:\bar.txt 檔案除非[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="1474f-204">For example, the filesystem provider will not copy c:\temp\abc.txt over an existing c:\bar.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="1474f-205">如果在指定的路徑`destination`參數存在，而且是一個容器中， [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性不是必要。</span><span class="sxs-lookup"><span data-stu-id="1474f-205">If the path specified in the `destination` parameter exists and is a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="1474f-206">在此情況下， [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)所指定的項目應該移`path`所指定的參數，以容器`destination`參數做為子系。</span><span class="sxs-lookup"><span data-stu-id="1474f-206">In this case, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) should move the item indicated by the `path` parameter to the container indicated by the `destination` parameter as a child.</span></span>

<span data-ttu-id="1474f-207">您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和資料存放區進行任何變更之前，先檢查它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="1474f-207">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="1474f-208">這個方法用來變更系統狀態，例如，刪除檔案時，請確認執行作業。</span><span class="sxs-lookup"><span data-stu-id="1474f-208">This method is used to confirm execution of an operation when a change is made to system state, for example, deleting files.</span></span> <span data-ttu-id="1474f-209">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)傳送給使用者，變更納入考量，任何命令列設定或喜好設定變數中的 Windows PowerShell 執行階段資源的名稱判斷應該顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="1474f-209">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="1474f-210">若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。</span><span class="sxs-lookup"><span data-stu-id="1474f-210">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="1474f-211">這個方法會將訊息傳送給使用者，以允許說如果應該繼續執行作業的意見反應。</span><span class="sxs-lookup"><span data-stu-id="1474f-211">This method sends a message to the user to allow feedback to say if the operation should be continued.</span></span> <span data-ttu-id="1474f-212">您的提供者應該呼叫[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作為額外的檢查，如有潛在危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="1474f-212">Your provider should call [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a><span data-ttu-id="1474f-213">附加至 Move-item Cmdlet 的動態參數</span><span class="sxs-lookup"><span data-stu-id="1474f-213">Attaching Dynamic Parameters to the Move-Item Cmdlet</span></span>

<span data-ttu-id="1474f-214">有時候`Move-Item`cmdlet 需要在執行階段以動態方式提供的其他參數。</span><span class="sxs-lookup"><span data-stu-id="1474f-214">Sometimes the `Move-Item` cmdlet requires additional parameters that are provided dynamically at runtime.</span></span> <span data-ttu-id="1474f-215">若要提供這些動態參數，請瀏覽提供者必須實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法來取得必要的參數值從位於指定的路徑，並傳回的項目具有屬性和欄位的剖析時的物件屬性類似於 cmdlet 類別或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="1474f-215">To provide these dynamic parameters, the navigation provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method to get the required parameter values from the item at the indicated path, and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="1474f-216">此瀏覽提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="1474f-216">This navigation provider does not implement this method.</span></span> <span data-ttu-id="1474f-217">不過，下列程式碼是預設的實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)。</span><span class="sxs-lookup"><span data-stu-id="1474f-217">However, the following code is the default implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a><span data-ttu-id="1474f-218">相對路徑正規化</span><span class="sxs-lookup"><span data-stu-id="1474f-218">Normalizing a Relative Path</span></span>

<span data-ttu-id="1474f-219">您的瀏覽提供者會實作[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法，以標準化完整的路徑中指出`path`參數相對於所指定的路徑為`basePath`參數。</span><span class="sxs-lookup"><span data-stu-id="1474f-219">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method to normalize the fully-qualified path indicated in the `path` parameter as being relative to the path specified by the `basePath` parameter.</span></span> <span data-ttu-id="1474f-220">方法會傳回標準化路徑的字串表示。</span><span class="sxs-lookup"><span data-stu-id="1474f-220">The method returns a string representation of the normalized path.</span></span> <span data-ttu-id="1474f-221">它會寫入錯誤，如果`path`參數會指定不存在的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-221">It writes an error if the `path` parameter specifies a nonexistent path.</span></span>

<span data-ttu-id="1474f-222">範例導覽提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="1474f-222">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="1474f-223">以下是預設的實作。</span><span class="sxs-lookup"><span data-stu-id="1474f-223">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a><span data-ttu-id="1474f-224">有關實作 NormalizeRelativePath 的注意事項</span><span class="sxs-lookup"><span data-stu-id="1474f-224">Things to Remember About Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="1474f-225">您實作[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)應剖析`path`參數，但它不需要使用純粹語法的剖析。</span><span class="sxs-lookup"><span data-stu-id="1474f-225">Your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) should parse the `path` parameter, but it does not have to use purely syntactical parsing.</span></span> <span data-ttu-id="1474f-226">這個方法，以使用路徑來查詢資料存放區中的路徑資訊，並建立路徑符合大小寫的設計建議，以及標準化路徑語法。</span><span class="sxs-lookup"><span data-stu-id="1474f-226">You are encouraged to design this method to use the path to look up the path information in the data store and create a path that matches the casing and standardized path syntax.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1474f-227">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="1474f-227">Code Sample</span></span>

<span data-ttu-id="1474f-228">完整的範例程式碼，請參閱[AccessDbProviderSample05 程式碼範例](./accessdbprovidersample05-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="1474f-228">For complete sample code, see [AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="1474f-229">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="1474f-229">Defining Object Types and Formatting</span></span>

<span data-ttu-id="1474f-230">它可讓提供者將成員加入至現有的物件，或定義新的物件。</span><span class="sxs-lookup"><span data-stu-id="1474f-230">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="1474f-231">如需詳細資訊，請參閱 <<c0> [ 延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="1474f-231">For more information, see[Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="1474f-232">建置的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1474f-232">Building the Windows PowerShell provider</span></span>

<span data-ttu-id="1474f-233">如需詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="1474f-233">For more information, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="1474f-234">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1474f-234">Testing the Windows PowerShell provider</span></span>

<span data-ttu-id="1474f-235">當您的 Windows PowerShell 提供者已向 Windows PowerShell 時，您可以藉由在命令列，包括衍生所提供的指令程式上執行的受支援的 cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="1474f-235">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including cmdlets made available by derivation.</span></span> <span data-ttu-id="1474f-236">此範例會測試範例導覽提供者。</span><span class="sxs-lookup"><span data-stu-id="1474f-236">This example will test the sample navigation provider.</span></span>

1. <span data-ttu-id="1474f-237">執行新的殼層，並使用`Set-Location`cmdlet 來設定表示和存取資料庫的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-237">Run your new shell and use the `Set-Location` cmdlet to set the path to indicate the Access database.</span></span>

   ```powershell
   Set-Location mydb:
   ```

2. <span data-ttu-id="1474f-238">現在執行`Get-Childitem`cmdlet 來擷取一份資料庫項目，也就是可用的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="1474f-238">Now run the `Get-Childitem` cmdlet to retrieve a list of the database items, which are the available database tables.</span></span> <span data-ttu-id="1474f-239">每個資料表，此 cmdlet 也會擷取資料表資料列數目。</span><span class="sxs-lookup"><span data-stu-id="1474f-239">For each table, this cmdlet also retrieves the number of table rows.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
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

3. <span data-ttu-id="1474f-240">使用`Set-Location`cmdlet，將員工資料資料表的位置。</span><span class="sxs-lookup"><span data-stu-id="1474f-240">Use the `Set-Location` cmdlet again to set the location of the Employees data table.</span></span>

   ```powershell
   Set-Location Employees
   ```

4. <span data-ttu-id="1474f-241">現在我們將使用`Get-Location`cmdlet 來擷取員工資料表的路徑。</span><span class="sxs-lookup"><span data-stu-id="1474f-241">Let's now use the `Get-Location` cmdlet to retrieve the path to the Employees table.</span></span>

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. <span data-ttu-id="1474f-242">現在，使用`Get-Childitem`cmdlet 經由管道輸出至`Format-Table`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1474f-242">Now use the `Get-Childitem` cmdlet piped to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="1474f-243">這組指令程式會擷取針對員工資料表，也就是資料表的資料列的項目。</span><span class="sxs-lookup"><span data-stu-id="1474f-243">This set of cmdlets retrieves the items for the Employees data table, which are the table rows.</span></span> <span data-ttu-id="1474f-244">它們會格式化依照`Format-Table`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1474f-244">They are formatted as specified by the `Format-Table` cmdlet.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
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

6. <span data-ttu-id="1474f-245">您現在可以執行`Get-Item`cmdlet 來擷取員工資料表的資料列 0 的項目。</span><span class="sxs-lookup"><span data-stu-id="1474f-245">You can now run the `Get-Item` cmdlet to retrieve the items for row 0 of the Employees data table.</span></span>

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. <span data-ttu-id="1474f-246">使用`Get-Item`cmdlet 一次來擷取員工資料的資料列 0 中的項目。</span><span class="sxs-lookup"><span data-stu-id="1474f-246">Use the `Get-Item` cmdlet again to retrieve the employee data for the items in row 0.</span></span>

   ```powershell
   (Get-Item 0).data
   ```

   ```output
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

## <a name="see-also"></a><span data-ttu-id="1474f-247">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1474f-247">See Also</span></span>

[<span data-ttu-id="1474f-248">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1474f-248">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="1474f-249">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1474f-249">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="1474f-250">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="1474f-250">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="1474f-251">實作容器的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1474f-251">Implement a Container Windows PowerShell provider</span></span>](./creating-a-windows-powershell-container-provider.md)

[<span data-ttu-id="1474f-252">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="1474f-252">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="1474f-253">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="1474f-253">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1474f-254">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1474f-254">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)