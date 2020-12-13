---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 提供者概觀
description: Windows PowerShell 提供者概觀
ms.openlocfilehash: 2f1c5f5991a64fb2b85ece7feba915164ebd34ee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355505"
---
# <a name="windows-powershell-provider-overview"></a><span data-ttu-id="212c6-103">Windows PowerShell 提供者概觀</span><span class="sxs-lookup"><span data-stu-id="212c6-103">Windows PowerShell Provider Overview</span></span>

<span data-ttu-id="212c6-104">Windows PowerShell 提供者可讓任何資料存放區公開為檔案系統，就像是載入的磁片磁碟機一樣。</span><span class="sxs-lookup"><span data-stu-id="212c6-104">A Windows PowerShell provider allows any data store to be exposed like a file system as if it were a mounted drive.</span></span> <span data-ttu-id="212c6-105">例如，內建的登錄提供者可讓您流覽登錄，就像流覽 `c` 電腦的磁片磁碟機一樣。</span><span class="sxs-lookup"><span data-stu-id="212c6-105">For example, the built-in Registry provider allows you to navigate the registry like you would navigate the `c` drive of your computer.</span></span> <span data-ttu-id="212c6-106">提供者也可以覆寫 Cmdlet (例如、等）， `Item` `Get-Item` ) 讓您的 `Set-Item` 資料存放區中的資料可以被處理，例如在流覽檔案系統時處理檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="212c6-106">A provider can also override the `Item` cmdlets (for example, `Get-Item`, `Set-Item`, etc.) such that the data in your data store can be treated like files and directories are treated when navigating a file system.</span></span> <span data-ttu-id="212c6-107">如需提供者和磁片磁碟機的詳細資訊，以及 Windows PowerShell 中內建提供者的詳細資訊，請參閱 [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)。</span><span class="sxs-lookup"><span data-stu-id="212c6-107">For more information about providers and drives, and the built-in providers in Windows PowerShell, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <a name="providers-and-drives"></a><span data-ttu-id="212c6-108">提供者和磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="212c6-108">Providers and Drives</span></span>

<span data-ttu-id="212c6-109">提供者會定義用來存取、流覽和編輯資料存放區的邏輯，而磁片磁碟機會指定資料存放區的特定進入點 (或提供者所定義類型的部分資料存放區) 。</span><span class="sxs-lookup"><span data-stu-id="212c6-109">A Provider defines the logic that is used to access, navigate, and edit a data store, while a drive specifies a specific entry point to a data store (or a portion of a data store) that is of the type defined by the provider.</span></span> <span data-ttu-id="212c6-110">例如，登錄提供者可讓您存取登錄中的 hive 和金鑰，而 HKLM 和 HKCU 磁片磁碟機會在登錄中指定對應的 hive。</span><span class="sxs-lookup"><span data-stu-id="212c6-110">For example, the Registry provider allows you to access hives and keys in a registry, and the HKLM and HKCU drives specify the corresponding hives within the registry.</span></span> <span data-ttu-id="212c6-111">HKLM 和 HKCU 磁片磁碟機都使用登錄提供者。</span><span class="sxs-lookup"><span data-stu-id="212c6-111">The HKLM and HKCU drives both use the Registry provider.</span></span>

<span data-ttu-id="212c6-112">當您撰寫提供者時，可以指定提供者可供使用時自動建立的預設磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="212c6-112">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="212c6-113">您也會定義方法，以建立使用該提供者的新磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="212c6-113">You also define a method to create new drives that use that provider.</span></span>

## <a name="type-of-providers"></a><span data-ttu-id="212c6-114">提供者類型</span><span class="sxs-lookup"><span data-stu-id="212c6-114">Type of Providers</span></span>

<span data-ttu-id="212c6-115">有數種類型的提供者，每個提供者都提供不同層級的功能。</span><span class="sxs-lookup"><span data-stu-id="212c6-115">There are several types of providers, each of which provides a different level of functionality.</span></span> <span data-ttu-id="212c6-116">提供者會實作為衍生自[SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory) 
 **CmdletProvider** 類別的其中一個下階的類別。</span><span class="sxs-lookup"><span data-stu-id="212c6-116">A provider is implemented as a class that derives from one of the descendants of the [System.Management.Automation.SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory)
**CmdletProvider** class.</span></span> <span data-ttu-id="212c6-117">如需不同類型的提供者的詳細資訊，請參閱 [提供者類型](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="212c6-117">For information about the different types of providers, see [Provider types](./provider-types.md).</span></span>

## <a name="provider-cmdlets"></a><span data-ttu-id="212c6-118">提供者 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="212c6-118">Provider cmdlets</span></span>

<span data-ttu-id="212c6-119">提供者可以執行對應至 Cmdlet 的方法，並在該提供者的磁片磁碟機中使用這些 Cmdlet 時，為這些 Cmdlet 建立自訂行為。</span><span class="sxs-lookup"><span data-stu-id="212c6-119">Providers can implement methods that correspond to cmdlets, creating custom behaviors for those cmdlets when used in a drive for that provider.</span></span> <span data-ttu-id="212c6-120">視提供者類型而定，有不同的 Cmdlet 組可用。</span><span class="sxs-lookup"><span data-stu-id="212c6-120">Depending on the type of provider, different sets of cmdlets are available.</span></span> <span data-ttu-id="212c6-121">如需提供者中可供自訂的完整 Cmdlet 清單，請參閱 [提供者 Cmdlet](./provider-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="212c6-121">For a complete list of the cmdlets available for customization in providers, see [Provider cmdlets](./provider-cmdlets.md).</span></span>

## <a name="provider-paths"></a><span data-ttu-id="212c6-122">提供者路徑</span><span class="sxs-lookup"><span data-stu-id="212c6-122">Provider paths</span></span>

<span data-ttu-id="212c6-123">使用者流覽提供者磁片磁碟機，例如檔案系統。</span><span class="sxs-lookup"><span data-stu-id="212c6-123">Users navigate provider drives like file systems.</span></span> <span data-ttu-id="212c6-124">因此，它們預期路徑的語法會對應到檔案系統流覽中使用的路徑。</span><span class="sxs-lookup"><span data-stu-id="212c6-124">Because of this, they expect the syntax of paths to correspond to the paths used in file system navigation.</span></span> <span data-ttu-id="212c6-125">當使用者執行提供者 Cmdlet 時，會指定要存取之專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="212c6-125">When a user runs a provider cmdlet, they specify a path to the item to be accessed.</span></span> <span data-ttu-id="212c6-126">您可以透過數種方式來解讀指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="212c6-126">The path that is specified can be interpreted in several ways.</span></span> <span data-ttu-id="212c6-127">提供者應支援下列一或多個路徑類型。</span><span class="sxs-lookup"><span data-stu-id="212c6-127">A provider should support one or more of the following path types.</span></span>

### <a name="drive-qualified-paths"></a><span data-ttu-id="212c6-128">磁片磁碟機限定路徑</span><span class="sxs-lookup"><span data-stu-id="212c6-128">Drive-qualified paths</span></span>

<span data-ttu-id="212c6-129">磁片磁碟機限定路徑是專案名稱、專案所在的容器和子容器的組合，以及用來存取專案的 Windows PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="212c6-129">A drive-qualified path is a combination of the item name, the container and subcontainers in which the item is located, and the Windows PowerShell drive through which the item is accessed.</span></span> <span data-ttu-id="212c6-130"> (磁片磁碟機是由用來存取資料存放區的提供者所定義。</span><span class="sxs-lookup"><span data-stu-id="212c6-130">(Drives are defined by the provider that is used to access the data store.</span></span> <span data-ttu-id="212c6-131">此路徑的開頭為磁片磁碟機名稱，後面接著冒號 (： ) 。</span><span class="sxs-lookup"><span data-stu-id="212c6-131">This path starts with the drive name followed by a colon (:).</span></span> <span data-ttu-id="212c6-132">例如：`get-childitem C:`</span><span class="sxs-lookup"><span data-stu-id="212c6-132">For example: `get-childitem C:`</span></span>

### <a name="provider-qualified-paths"></a><span data-ttu-id="212c6-133">提供者限定的路徑</span><span class="sxs-lookup"><span data-stu-id="212c6-133">Provider-qualified paths</span></span>

<span data-ttu-id="212c6-134">為了讓 Windows PowerShell 引擎初始化和取消初始化您的提供者，提供者必須支援提供者限定的路徑。</span><span class="sxs-lookup"><span data-stu-id="212c6-134">To allow the Windows PowerShell engine to initialize and uninitialize your provider, the provider must support a provider-qualified path.</span></span> <span data-ttu-id="212c6-135">例如，使用者可以初始化和解除初始化 FileSystem 提供者，因為它會定義下列提供者限定的路徑： `FileSystem::\\uncshare\abc\bar` 。</span><span class="sxs-lookup"><span data-stu-id="212c6-135">For example, the user can initialize and uninitialize the FileSystem provider because it defines the following provider-qualified path: `FileSystem::\\uncshare\abc\bar`.</span></span>

### <a name="provider-direct-paths"></a><span data-ttu-id="212c6-136">提供者-直接路徑</span><span class="sxs-lookup"><span data-stu-id="212c6-136">Provider-direct paths</span></span>

<span data-ttu-id="212c6-137">若要允許遠端存取您的 Windows PowerShell 提供者，它應該支援提供者直接路徑，直接傳遞給目前位置的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="212c6-137">To allow remote access to your Windows PowerShell provider, it should support a provider-direct path to pass directly to the Windows PowerShell provider for the current location.</span></span> <span data-ttu-id="212c6-138">例如，登錄 Windows PowerShell 提供者可以使用 `\\server\regkeypath` 做為提供者直接路徑。</span><span class="sxs-lookup"><span data-stu-id="212c6-138">For example, the registry Windows PowerShell provider can use `\\server\regkeypath` as a provider-direct path.</span></span>

### <a name="provider-internal-paths"></a><span data-ttu-id="212c6-139">提供者-內部路徑</span><span class="sxs-lookup"><span data-stu-id="212c6-139">Provider-internal paths</span></span>

<span data-ttu-id="212c6-140">若要允許提供者 Cmdlet 使用非 Windows PowerShell 的應用程式開發介面來存取資料 () Api，您的 Windows PowerShell 提供者應該支援提供者內部路徑。</span><span class="sxs-lookup"><span data-stu-id="212c6-140">To allow the provider cmdlet to access data using non-Windows PowerShell application programming interfaces (APIs), your Windows PowerShell provider should support a provider-internal path.</span></span> <span data-ttu-id="212c6-141">此路徑會以提供者限定路徑中的 "：：" 來表示。</span><span class="sxs-lookup"><span data-stu-id="212c6-141">This path is indicated after the "::" in the provider-qualified path.</span></span> <span data-ttu-id="212c6-142">例如，filesystem Windows PowerShell 提供者的提供者內部路徑為 `\\uncshare\abc\bar` 。</span><span class="sxs-lookup"><span data-stu-id="212c6-142">For example, the provider-internal path for the filesystem Windows PowerShell provider is `\\uncshare\abc\bar`.</span></span>

## <a name="overriding-cmdlet-parameters"></a><span data-ttu-id="212c6-143">覆寫 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="212c6-143">Overriding cmdlet parameters</span></span>

<span data-ttu-id="212c6-144">某些提供者特定 Cmdlet 的行為可由提供者覆寫。</span><span class="sxs-lookup"><span data-stu-id="212c6-144">The behavior of some provider-specific cmdlets can be overridden by a provider.</span></span> <span data-ttu-id="212c6-145">如需可覆寫的參數清單，以及如何在您的提供者類別中覆寫這些參數的清單，請參閱 [提供者 Cmdlet 參數](./provider-cmdlet-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="212c6-145">For a list of parameters that can be overridden, and how to override them in your provider class, see [Provider cmdlet parameters](./provider-cmdlet-parameters.md)</span></span>

## <a name="dynamic-parameters"></a><span data-ttu-id="212c6-146">動態參數</span><span class="sxs-lookup"><span data-stu-id="212c6-146">Dynamic parameters</span></span>

<span data-ttu-id="212c6-147">當使用者針對 Cmdlet 的其中一個靜態參數指定特定值時，提供者可以定義新增至提供者 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="212c6-147">Providers can define dynamic parameters that are added to a provider cmdlet when the user specifies a certain value for one of the static parameters of the cmdlet.</span></span> <span data-ttu-id="212c6-148">提供者會藉由執行一或多個動態參數方法來執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="212c6-148">A provider does this by implementing one or more dynamic parameter methods.</span></span> <span data-ttu-id="212c6-149">如需可用來新增動態參數的 Cmdlet 參數清單，以及用來執行這些參數的方法，請參閱 [提供者 Cmdlet 動態參數](./provider-cmdlet-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="212c6-149">For a list of cmdlet parameters that can be used to add dynamic parameter, and the methods used to implement them, see [Provider cmdlet dynamic parameters](./provider-cmdlet-dynamic-parameters.md).</span></span>

## <a name="provider-capabilities"></a><span data-ttu-id="212c6-150">提供者功能</span><span class="sxs-lookup"><span data-stu-id="212c6-150">Provider capabilities</span></span>

<span data-ttu-id="212c6-151">[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉定義了提供者可支援的一些功能，。</span><span class="sxs-lookup"><span data-stu-id="212c6-151">The [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration defines a number of capabilities that providers can support.</span></span> <span data-ttu-id="212c6-152">這些包括使用萬用字元、篩選項目和支援交易的能力。</span><span class="sxs-lookup"><span data-stu-id="212c6-152">These include the ability to use wildcards, filter items, and support transactions.</span></span> <span data-ttu-id="212c6-153">若要指定提供者的功能，請加入 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉的值清單（與邏輯作業結合）。 `OR` [Cmdletproviderattribute. Providercapabilities \*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) 屬性 (您的提供者類別之屬性的第二個參數（) attribute）的第二個參數（property），以及您的提供者類別 [之屬性](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="212c6-153">To specify capabilities for a provider, add a list of values of the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration, combined with a logical `OR` operation, as the [System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities\*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) property (the second parameter of the attribute) of the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute for your provider class.</span></span> <span data-ttu-id="212c6-154">例如，下列屬性會指定提供者支援[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 
 **ShouldProcess** 和[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 
 **交易** 功能的交易功能。（& a）</span><span class="sxs-lookup"><span data-stu-id="212c6-154">For example, the following attribute specifies that the provider supports the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)
**ShouldProcess** and [System.Management.Automation.Provider.ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)
**Transactions** capabilities.</span></span>

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a><span data-ttu-id="212c6-155">提供者 Cmdlet 說明</span><span class="sxs-lookup"><span data-stu-id="212c6-155">Provider cmdlet help</span></span>

<span data-ttu-id="212c6-156">撰寫提供者時，您可以針對所支援的提供者 Cmdlet，執行自己的說明。</span><span class="sxs-lookup"><span data-stu-id="212c6-156">When writing a provider, you can implement your own Help for the provider cmdlets that you support.</span></span>
<span data-ttu-id="212c6-157">這包括針對每個提供者 Cmdlet 的單一說明主題，或多個說明主題版本的說明主題，以瞭解提供者 Cmdlet 會根據動態參數的使用方式，以不同的方式運作。</span><span class="sxs-lookup"><span data-stu-id="212c6-157">This includes a single help topic for each provider cmdlet or multiple versions of a help topic for cases where the provider cmdlet acts differently based on the use of dynamic parameters.</span></span> <span data-ttu-id="212c6-158">若要支援提供者 Cmdlet 特定的說明，您的提供者必須執行 [ICmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) 介面。</span><span class="sxs-lookup"><span data-stu-id="212c6-158">To support provider cmdlet-specific help, your provider must implement the [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) interface.</span></span>

<span data-ttu-id="212c6-159">Windows PowerShell 引擎會呼叫 [ICmdletprovidersupportshelp. Gethelpmaml \*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) 方法，以顯示提供者 Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="212c6-159">The Windows PowerShell engine calls the [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml\*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) method to display the Help topic for your provider cmdlets.</span></span> <span data-ttu-id="212c6-160">引擎會提供使用者在執行 Cmdlet 時指定的 Cmdlet 名稱 `Get-Help` ，以及使用者的目前路徑。</span><span class="sxs-lookup"><span data-stu-id="212c6-160">The engine provides the name of the cmdlet that the user specified when running the `Get-Help` cmdlet and the current path of the user.</span></span>
<span data-ttu-id="212c6-161">如果您的提供者針對不同的磁片磁碟機執行相同提供者 Cmdlet 的不同版本，則需要目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="212c6-161">The current path is required if your provider implements different versions of the same provider cmdlet for different drives.</span></span> <span data-ttu-id="212c6-162">方法必須傳回包含 Cmdlet 說明之 XML 的字串。</span><span class="sxs-lookup"><span data-stu-id="212c6-162">The method must return a string that contains the XML for the cmdlet Help.</span></span>

<span data-ttu-id="212c6-163">說明檔的內容是使用 PSMAML XML 撰寫的。</span><span class="sxs-lookup"><span data-stu-id="212c6-163">The content for the Help file is written using PSMAML XML.</span></span> <span data-ttu-id="212c6-164">這是用來撰寫獨立 Cmdlet 之說明內容的相同 XML 架構。</span><span class="sxs-lookup"><span data-stu-id="212c6-164">This is the same XML schema that is used for writing Help content for stand-alone cmdlets.</span></span> <span data-ttu-id="212c6-165">將自訂 Cmdlet 說明的內容新增至專案下提供者的說明檔 `CmdletHelpPaths` 。</span><span class="sxs-lookup"><span data-stu-id="212c6-165">Add the content for your custom cmdlet Help to the Help file for your provider under the `CmdletHelpPaths` element.</span></span> <span data-ttu-id="212c6-166">下列範例顯示 `command` 單一提供者 Cmdlet 的元素，並顯示您指定提供者的提供者 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="212c6-166">The following example shows the `command` element for a single provider cmdlet, and it shows how you specify the name of the provider cmdlet that your provider.</span></span> <span data-ttu-id="212c6-167">支援</span><span class="sxs-lookup"><span data-stu-id="212c6-167">supports</span></span>

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a><span data-ttu-id="212c6-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="212c6-168">See Also</span></span>

[<span data-ttu-id="212c6-169">Windows PowerShell 提供者功能</span><span class="sxs-lookup"><span data-stu-id="212c6-169">Windows PowerShell Provider Functionality</span></span>](./provider-types.md)

[<span data-ttu-id="212c6-170">提供者 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="212c6-170">Provider Cmdlets</span></span>](./provider-cmdlets.md)

[<span data-ttu-id="212c6-171">撰寫 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="212c6-171">Writing a Windows PowerShell Provider</span></span>](./writing-a-windows-powershell-provider.md)
