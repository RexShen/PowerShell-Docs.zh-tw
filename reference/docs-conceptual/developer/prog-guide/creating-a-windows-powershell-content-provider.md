---
title: 建立 Windows PowerShell 內容提供者
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
ms.openlocfilehash: 2d48c18cb41dcca372b1e12e1f3abc4c3f5e4bee
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870722"
---
# <a name="creating-a-windows-powershell-content-provider"></a><span data-ttu-id="11bbe-102">建立 Windows PowerShell 內容提供者</span><span class="sxs-lookup"><span data-stu-id="11bbe-102">Creating a Windows PowerShell Content Provider</span></span>

<span data-ttu-id="11bbe-103">本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以運算元據存放區中的專案內容。</span><span class="sxs-lookup"><span data-stu-id="11bbe-103">This topic describes how to create a Windows PowerShell provider that enables the user to manipulate the contents of the items in a data store.</span></span> <span data-ttu-id="11bbe-104">因此，可以操作專案內容的提供者稱為 Windows PowerShell 內容提供者。</span><span class="sxs-lookup"><span data-stu-id="11bbe-104">As a consequence, a provider that can manipulate the contents of items is referred to as a Windows PowerShell content provider.</span></span>

> [!NOTE]
> <span data-ttu-id="11bbe-105">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的原始程式檔（AccessDBSampleProvider06.cs）。</span><span class="sxs-lookup"><span data-stu-id="11bbe-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="11bbe-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="11bbe-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="11bbe-107">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="11bbe-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="11bbe-108">如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="11bbe-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="define-the-windows-powershell-content-provider-class"></a><span data-ttu-id="11bbe-109">定義 Windows PowerShell 內容提供者類別</span><span class="sxs-lookup"><span data-stu-id="11bbe-109">Define the Windows PowerShell Content Provider Class</span></span>

<span data-ttu-id="11bbe-110">Windows PowerShell 內容提供者必須建立一個支援[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面的 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="11bbe-110">A Windows PowerShell content provider must create a .NET class that supports the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span> <span data-ttu-id="11bbe-111">以下是本節所述之專案提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="11bbe-111">Here is the class definition for the item provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33
"AccessDBProviderSample06.cs")]

<span data-ttu-id="11bbe-112">請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="11bbe-112">Note that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="11bbe-113">第一個參數會為 Windows PowerShell 所使用的提供者指定易記的名稱。</span><span class="sxs-lookup"><span data-stu-id="11bbe-113">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="11bbe-114">第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="11bbe-114">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="11bbe-115">對於此提供者，並未新增 Windows PowerShell 特有的功能。</span><span class="sxs-lookup"><span data-stu-id="11bbe-115">For this provider, there are no added Windows PowerShell specific capabilities.</span></span>

## <a name="define-functionality-of-base-class"></a><span data-ttu-id="11bbe-116">定義基類的功能</span><span class="sxs-lookup"><span data-stu-id="11bbe-116">Define Functionality of Base Class</span></span>

<span data-ttu-id="11bbe-117">如[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)中所述， [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別衍生自數個其他提供不同提供者功能的類別。</span><span class="sxs-lookup"><span data-stu-id="11bbe-117">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="11bbe-118">因此，Windows PowerShell 內容提供者通常會定義這些類別所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="11bbe-118">A Windows PowerShell content provider, therefore, typically defines all of the functionality provided by those classes.</span></span>

<span data-ttu-id="11bbe-119">如需如何執行功能來新增會話特定初始化資訊以及釋放提供者所使用之資源的詳細資訊，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="11bbe-119">For more information about how to implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="11bbe-120">不過，大部分的提供者（包括這裡所述的提供者）都可以使用 Windows PowerShell 所提供的這項功能的預設執行。</span><span class="sxs-lookup"><span data-stu-id="11bbe-120">However, most providers, including the provider described here, can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="11bbe-121">若要存取資料存放區，提供者必須實作為[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的方法。</span><span class="sxs-lookup"><span data-stu-id="11bbe-121">To access the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="11bbe-122">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="11bbe-122">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="11bbe-123">若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="11bbe-123">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="11bbe-124">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="11bbe-124">For more information about implementing these methods, see [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="11bbe-125">若要在多層式資料存放區上工作，提供者必須執行[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="11bbe-125">To work on multi-layer data stores, the provider must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="11bbe-126">如需有關如何執行這些方法的詳細資訊，請參閱[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="11bbe-126">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

<span data-ttu-id="11bbe-127">若要支援遞迴命令、嵌套容器和相對路徑，提供者必須執行[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基類。</span><span class="sxs-lookup"><span data-stu-id="11bbe-127">To support recursive commands, nested containers, and relative paths, the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="11bbe-128">此外，此 Windows PowerShell 內容提供者可以將[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面附加至[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基類，因此必須執行該類別所提供的方法，才能進行此程式。</span><span class="sxs-lookup"><span data-stu-id="11bbe-128">In addition, this Windows PowerShell content provider can attaches [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface to the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class, and must therefore implement the methods provided by that class.</span></span> <span data-ttu-id="11bbe-129">如需詳細資訊，請參閱執行這些方法，請參閱實[作為流覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="11bbe-129">For more information, see implementing those methods, see [Implement a Navigation Windows PowerShell Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

## <a name="implementing-a-content-reader"></a><span data-ttu-id="11bbe-130">執行內容讀取程式</span><span class="sxs-lookup"><span data-stu-id="11bbe-130">Implementing a Content Reader</span></span>

<span data-ttu-id="11bbe-131">若要從專案讀取內容，提供者必須執行衍生自[Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)的內容讀取器類別。</span><span class="sxs-lookup"><span data-stu-id="11bbe-131">To read content from an item, a provider must implements a content reader class that derives from [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).</span></span>
<span data-ttu-id="11bbe-132">此提供者的內容讀取器允許存取資料表中的資料列內容。</span><span class="sxs-lookup"><span data-stu-id="11bbe-132">The content reader for this provider allows access to the contents of a row in a data table.</span></span> <span data-ttu-id="11bbe-133">內容讀取器類別會定義**讀取**方法，以從指定的資料列抓取資料，並傳回代表該資料的清單、移動內容讀取器的**搜尋**方法、關閉內容讀取器的**關閉**方法，以及**Dispose**方法。</span><span class="sxs-lookup"><span data-stu-id="11bbe-133">The content reader class defines a **Read** method that retrieves the data from the indicated row and returns a list representing that data, a **Seek** method that moves the content reader, a **Close** method that closes the content reader, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241
"AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a><span data-ttu-id="11bbe-134">執行內容寫入器</span><span class="sxs-lookup"><span data-stu-id="11bbe-134">Implementing a Content Writer</span></span>

<span data-ttu-id="11bbe-135">若要將內容寫入專案，提供者必須執行衍生自[Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)的內容寫入器類別。</span><span class="sxs-lookup"><span data-stu-id="11bbe-135">To write content to an item, a provider must implement a content writer class derives from [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).</span></span>
<span data-ttu-id="11bbe-136">內容寫入器類別會定義**寫入**方法，以寫入指定的資料列內容、移動內容寫入器的**搜尋**方法、關閉內容寫入器的**Close**方法，以及**Dispose**方法。</span><span class="sxs-lookup"><span data-stu-id="11bbe-136">The content writer class defines a **Write** method that writes the specified row content, a **Seek** method that moves the content writer, a **Close** method that closes the content writer, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a><span data-ttu-id="11bbe-137">正在抓取內容讀取器</span><span class="sxs-lookup"><span data-stu-id="11bbe-137">Retrieving the Content Reader</span></span>

<span data-ttu-id="11bbe-138">若要從專案取得內容，提供者必須執行[IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)以支援 `Get-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="11bbe-138">To get content from an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) to support the `Get-Content` cmdlet.</span></span> <span data-ttu-id="11bbe-139">這個方法會傳回位於指定路徑之專案的內容讀取器。</span><span class="sxs-lookup"><span data-stu-id="11bbe-139">This method returns the content reader for the item located at the specified path.</span></span> <span data-ttu-id="11bbe-140">然後，可以開啟 reader 物件來讀取內容。</span><span class="sxs-lookup"><span data-stu-id="11bbe-140">The reader object can then be opened to read the content.</span></span>

<span data-ttu-id="11bbe-141">以下是此提供者的這個方法的[IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)的執行程式。</span><span class="sxs-lookup"><span data-stu-id="11bbe-141">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) for this method for this provider.</span></span>

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a><span data-ttu-id="11bbe-142">執行 GetContentReader 的相關事項</span><span class="sxs-lookup"><span data-stu-id="11bbe-142">Things to Remember About Implementing GetContentReader</span></span>

<span data-ttu-id="11bbe-143">下列條件可能適用于[IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)的執行程式：</span><span class="sxs-lookup"><span data-stu-id="11bbe-143">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span></span>

- <span data-ttu-id="11bbe-144">定義 provider 類別時，Windows PowerShell 內容提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="11bbe-144">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="11bbe-145">在這些情況下， [IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法的執行必須確保傳遞至方法的路徑符合指定之功能的需求。</span><span class="sxs-lookup"><span data-stu-id="11bbe-145">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="11bbe-146">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="11bbe-146">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="11bbe-147">根據預設，除非[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`，否則，此方法的覆寫不應抓取使用者所隱藏之物件的讀取器。</span><span class="sxs-lookup"><span data-stu-id="11bbe-147">By default, overrides of this method should not retrieve a reader for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="11bbe-148">如果路徑代表使用者所隱藏的專案，而[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為 `false`，則應該撰寫錯誤。</span><span class="sxs-lookup"><span data-stu-id="11bbe-148">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a><span data-ttu-id="11bbe-149">將動態參數附加至 Get Content Cmdlet</span><span class="sxs-lookup"><span data-stu-id="11bbe-149">Attaching Dynamic Parameters to the Get-Content Cmdlet</span></span>

<span data-ttu-id="11bbe-150">`Get-Content` Cmdlet 可能需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="11bbe-150">The `Get-Content` cmdlet might require additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="11bbe-151">為了提供這些動態參數，Windows PowerShell 內容提供者必須執行[IcontentCmdletprovider. Getcontentreaderdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="11bbe-151">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span> <span data-ttu-id="11bbe-152">這個方法會在指定的路徑上抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="11bbe-152">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="11bbe-153">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="11bbe-153">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="11bbe-154">這個 Windows PowerShell 容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="11bbe-154">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="11bbe-155">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="11bbe-155">However, the following code is the default implementation of this method.</span></span>

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a><span data-ttu-id="11bbe-156">正在抓取內容寫入器</span><span class="sxs-lookup"><span data-stu-id="11bbe-156">Retrieving the Content Writer</span></span>

<span data-ttu-id="11bbe-157">若要將內容寫入專案，提供者必須執行[IcontentCmdletprovider. Getcontentwriter \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) ，以支援 `Set-Content` 和 `Add-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="11bbe-157">To write content to an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) to support the `Set-Content` and `Add-Content` cmdlets.</span></span> <span data-ttu-id="11bbe-158">這個方法會傳回位於指定路徑之專案的內容寫入器。</span><span class="sxs-lookup"><span data-stu-id="11bbe-158">This method returns the content writer for the item located at the specified path.</span></span>

<span data-ttu-id="11bbe-159">以下是這個方法的[IcontentCmdletprovider. Getcontentwriter \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)的執行方式。</span><span class="sxs-lookup"><span data-stu-id="11bbe-159">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) for this method.</span></span>

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a><span data-ttu-id="11bbe-160">執行 GetContentWriter 的相關事項</span><span class="sxs-lookup"><span data-stu-id="11bbe-160">Things to Remember About Implementing GetContentWriter</span></span>

<span data-ttu-id="11bbe-161">下列條件可能適用于您的[IcontentCmdletprovider. Getcontentwriter \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)的執行方式：</span><span class="sxs-lookup"><span data-stu-id="11bbe-161">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span></span>

- <span data-ttu-id="11bbe-162">定義 provider 類別時，Windows PowerShell 內容提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="11bbe-162">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="11bbe-163">在這些情況下， [IcontentCmdletprovider. Getcontentwriter \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法的執行必須確保傳遞至方法的路徑符合指定之功能的需求。</span><span class="sxs-lookup"><span data-stu-id="11bbe-163">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="11bbe-164">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="11bbe-164">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="11bbe-165">根據預設，除非[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`，否則此方法的覆寫不應抓取使用者所隱藏之物件的寫入器。</span><span class="sxs-lookup"><span data-stu-id="11bbe-165">By default, overrides of this method should not retrieve a writer for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="11bbe-166">如果路徑代表使用者所隱藏的專案，而[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為 `false`，則應該撰寫錯誤。</span><span class="sxs-lookup"><span data-stu-id="11bbe-166">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a><span data-ttu-id="11bbe-167">將動態參數附加至新增內容和設定內容 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="11bbe-167">Attaching Dynamic Parameters to the Add-Content and Set-Content Cmdlets</span></span>

<span data-ttu-id="11bbe-168">`Add-Content` 和 `Set-Content` Cmdlet 可能需要新增執行時間的其他動態參數。</span><span class="sxs-lookup"><span data-stu-id="11bbe-168">The `Add-Content` and `Set-Content` cmdlets might require additional dynamic parameters that are added a runtime.</span></span> <span data-ttu-id="11bbe-169">為了提供這些動態參數，Windows PowerShell 內容提供者必須執行[IcontentCmdletprovider. Getcontentwriterdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="11bbe-169">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="11bbe-170">這個方法會在指定的路徑上抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="11bbe-170">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="11bbe-171">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="11bbe-171">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlets.</span></span>

<span data-ttu-id="11bbe-172">這個 Windows PowerShell 容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="11bbe-172">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="11bbe-173">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="11bbe-173">However, the following code is the default implementation of this method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a><span data-ttu-id="11bbe-174">清除內容</span><span class="sxs-lookup"><span data-stu-id="11bbe-174">Clearing Content</span></span>

<span data-ttu-id="11bbe-175">您的內容提供者會執行[IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以支援 `Clear-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="11bbe-175">Your content provider implements the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method in support of the `Clear-Content` cmdlet.</span></span> <span data-ttu-id="11bbe-176">這個方法會移除指定路徑中的專案內容，但保留專案不變。</span><span class="sxs-lookup"><span data-stu-id="11bbe-176">This method removes the contents of the item at the specified path, but leaves the item intact.</span></span>

<span data-ttu-id="11bbe-177">以下是此提供者的[IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法的執行。</span><span class="sxs-lookup"><span data-stu-id="11bbe-177">Here is the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method for this provider.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a><span data-ttu-id="11bbe-178">執行 ClearContent 的相關事項</span><span class="sxs-lookup"><span data-stu-id="11bbe-178">Things to Remember About Implementing ClearContent</span></span>

<span data-ttu-id="11bbe-179">下列條件可能適用于[IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)的執行程式：</span><span class="sxs-lookup"><span data-stu-id="11bbe-179">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span></span>

- <span data-ttu-id="11bbe-180">定義 provider 類別時，Windows PowerShell 內容提供者可能會從[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉中宣告 ExpandWildcards、Filter、Include 或 Exclude 的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="11bbe-180">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="11bbe-181">在這些情況下， [IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法的執行必須確保傳遞至方法的路徑符合指定之功能的需求。</span><span class="sxs-lookup"><span data-stu-id="11bbe-181">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="11bbe-182">若要這麼做，方法應該存取適當的屬性，例如[Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性（property），請將它加入。</span><span class="sxs-lookup"><span data-stu-id="11bbe-182">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="11bbe-183">根據預設，除非[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為 `true`，否則此方法的覆寫不應清除使用者隱藏的物件內容。</span><span class="sxs-lookup"><span data-stu-id="11bbe-183">By default, overrides of this method should not clear the contents of objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="11bbe-184">如果路徑代表使用者所隱藏的專案，而[Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為 `false`，則應該撰寫錯誤。</span><span class="sxs-lookup"><span data-stu-id="11bbe-184">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

- <span data-ttu-id="11bbe-185">您的 IcontentCmdletprovider 必須先呼叫[Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，然後在對資料存放區進行任何變更之前，先驗證它的傳回[值，然後再執行。](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)</span><span class="sxs-lookup"><span data-stu-id="11bbe-185">Your implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and verify its return value before making any changes to the data store.</span></span> <span data-ttu-id="11bbe-186">這個方法是用來在對資料存放區進行變更（例如清除內容）時，確認作業的執行。</span><span class="sxs-lookup"><span data-stu-id="11bbe-186">This method is used to confirm execution of an operation when a change is made to the data store, such as clearing content.</span></span> <span data-ttu-id="11bbe-187">[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會將要變更的資源名稱傳送給使用者，而 Windows PowerShell 執行時間會處理任何命令列設定或喜好設定變數來決定要顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="11bbe-187">The [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) method sends the name of the resource to be changed to the user, with the Windows PowerShell runtime handling any command-line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="11bbe-188">呼叫[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回 `true`，則[IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法應會呼叫 system.servicemodel. Cmdletprovider [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ShouldContinue 方法（.........）。</span><span class="sxs-lookup"><span data-stu-id="11bbe-188">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="11bbe-189">這個方法會將訊息傳送給使用者，以允許意見反應來驗證作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="11bbe-189">This method sends a message to the user to allow feedback to verify if the operation should be continued.</span></span> <span data-ttu-id="11bbe-190">呼叫[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允許額外檢查是否有潛在危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="11bbe-190">The call to [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) allows an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a><span data-ttu-id="11bbe-191">將動態參數附加至 Clear 內容 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="11bbe-191">Attaching Dynamic Parameters to the Clear-Content Cmdlet</span></span>

<span data-ttu-id="11bbe-192">`Clear-Content` Cmdlet 可能需要在執行時間新增額外的動態參數。</span><span class="sxs-lookup"><span data-stu-id="11bbe-192">The `Clear-Content` cmdlet might require additional dynamic parameters that are added at runtime.</span></span> <span data-ttu-id="11bbe-193">為了提供這些動態參數，Windows PowerShell 內容提供者必須執行[IcontentCmdletprovider. Clearcontentdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="11bbe-193">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="11bbe-194">這個方法會在指定的路徑中抓取專案的參數。</span><span class="sxs-lookup"><span data-stu-id="11bbe-194">This method retrieves the parameters for the item at the indicated path.</span></span> <span data-ttu-id="11bbe-195">這個方法會在指定的路徑上抓取專案的動態參數，並傳回具有屬性和欄位的物件，而此物件具有與 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件類似的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="11bbe-195">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="11bbe-196">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="11bbe-196">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="11bbe-197">這個 Windows PowerShell 容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="11bbe-197">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="11bbe-198">不過，下列程式碼是這個方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="11bbe-198">However, the following code is the default implementation of this method.</span></span>

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a><span data-ttu-id="11bbe-199">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="11bbe-199">Code Sample</span></span>

<span data-ttu-id="11bbe-200">如需完整的範例程式碼，請參閱[AccessDbProviderSample06 程式碼範例](./accessdbprovidersample06-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="11bbe-200">For complete sample code, see [AccessDbProviderSample06 Code Sample](./accessdbprovidersample06-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="11bbe-201">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="11bbe-201">Defining Object Types and Formatting</span></span>

<span data-ttu-id="11bbe-202">撰寫提供者時，可能需要將成員加入至現有的物件或定義新的物件。</span><span class="sxs-lookup"><span data-stu-id="11bbe-202">When writing a provider, it may be necessary to add members to existing objects or define new objects.</span></span> <span data-ttu-id="11bbe-203">完成此動作時，您必須建立類型檔案，Windows PowerShell 可以使用此檔案來識別物件的成員，以及定義如何顯示物件的格式檔案。</span><span class="sxs-lookup"><span data-stu-id="11bbe-203">When this is done, you must create a Types file that Windows PowerShell can use to identify the members of the object and a Format file that defines how the object is displayed.</span></span> <span data-ttu-id="11bbe-204">如需詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="11bbe-204">For more information, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="11bbe-205">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="11bbe-205">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="11bbe-206">請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="11bbe-206">See [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="11bbe-207">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="11bbe-207">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="11bbe-208">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="11bbe-208">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="11bbe-209">例如，測試範例內容提供者。</span><span class="sxs-lookup"><span data-stu-id="11bbe-209">For example, test the sample content provider.</span></span>

<span data-ttu-id="11bbe-210">使用 `Get-Content` Cmdlet，以 `Path` 參數所指定的路徑，抓取資料庫資料表中指定專案的內容。</span><span class="sxs-lookup"><span data-stu-id="11bbe-210">Use the `Get-Content` cmdlet to retrieve the contents of specified item in the database table at the path specified by the `Path` parameter.</span></span> <span data-ttu-id="11bbe-211">`ReadCount` 參數會指定要讀取之已定義內容讀取器的專案數（預設為1）。</span><span class="sxs-lookup"><span data-stu-id="11bbe-211">The `ReadCount` parameter specifies the number of items for the defined content reader to read (default 1).</span></span> <span data-ttu-id="11bbe-212">使用下列命令專案，Cmdlet 會從資料表中抓取兩個數據列（專案），並顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="11bbe-212">With the following command entry, the cmdlet retrieves two rows (items) from the table and displays their contents.</span></span> <span data-ttu-id="11bbe-213">請注意，下列範例輸出會使用虛構的 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="11bbe-213">Note that the following example output uses a fictitious Access database.</span></span>

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```Output
ID        : 1
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
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a><span data-ttu-id="11bbe-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11bbe-214">See Also</span></span>

[<span data-ttu-id="11bbe-215">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="11bbe-215">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="11bbe-216">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="11bbe-216">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

<span data-ttu-id="11bbe-217">[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="11bbe-217">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

[<span data-ttu-id="11bbe-218">執行流覽 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="11bbe-218">Implement a Navigation Windows PowerShell provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

<span data-ttu-id="11bbe-219">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="11bbe-219">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="11bbe-220">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="11bbe-220">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="11bbe-221">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="11bbe-221">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
