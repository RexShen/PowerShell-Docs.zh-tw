---
title: 建立 Windows PowerShell 內容提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: d7e237514b4db4bce3366836d3b6e0cd340bf107
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855010"
---
# <a name="creating-a-windows-powershell-content-provider"></a><span data-ttu-id="effb1-102">建立 Windows PowerShell 內容提供者</span><span class="sxs-lookup"><span data-stu-id="effb1-102">Creating a Windows PowerShell Content Provider</span></span>

<span data-ttu-id="effb1-103">本主題描述如何建立 Windows PowerShell 提供者，可讓使用者管理的資料存放區中的項目內容。</span><span class="sxs-lookup"><span data-stu-id="effb1-103">This topic describes how to create a Windows PowerShell provider that enables the user to manipulate the contents of the items in a data store.</span></span> <span data-ttu-id="effb1-104">如此一來，可以操作項目的內容提供者被指 Windows PowerShell 內容提供者。</span><span class="sxs-lookup"><span data-stu-id="effb1-104">As a consequence, a provider that can manipulate the contents of items is referred to as a Windows PowerShell content provider.</span></span>

> [!NOTE]
> <span data-ttu-id="effb1-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此提供者的原始程式檔 (AccessDBSampleProvider06.cs)。</span><span class="sxs-lookup"><span data-stu-id="effb1-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="effb1-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="effb1-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="effb1-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="effb1-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="effb1-108">如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="effb1-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="define-the-windows-powershell-content-provider-class"></a><span data-ttu-id="effb1-109">定義 Windows PowerShell 內容提供者類別</span><span class="sxs-lookup"><span data-stu-id="effb1-109">Define the Windows PowerShell Content Provider Class</span></span>

<span data-ttu-id="effb1-110">Windows PowerShell 內容提供者必須建立一個支援的.NET 類別[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面。</span><span class="sxs-lookup"><span data-stu-id="effb1-110">A Windows PowerShell content provider must create a .NET class that supports the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span> <span data-ttu-id="effb1-111">以下是這一節所述的項目提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="effb1-111">Here is the class definition for the item provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

<span data-ttu-id="effb1-112">請注意，在此類別定義中， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="effb1-112">Note that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="effb1-113">第一個參數會指定使用 Windows powershell 提供者的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="effb1-113">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="effb1-114">第二個參數指定命令處理期間提供者會公開 Windows PowerShell 執行階段的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="effb1-114">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="effb1-115">此提供者中，沒有新增的 Windows PowerShell 的特定功能。</span><span class="sxs-lookup"><span data-stu-id="effb1-115">For this provider, there are no added Windows PowerShell specific capabilities.</span></span>

## <a name="define-functionality-of-base-class"></a><span data-ttu-id="effb1-116">定義基底類別的功能</span><span class="sxs-lookup"><span data-stu-id="effb1-116">Define Functionality of Base Class</span></span>

<span data-ttu-id="effb1-117">中所述[設計您 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)，則[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別衍生自所提供的其他幾項類別不同的提供者的功能。</span><span class="sxs-lookup"><span data-stu-id="effb1-117">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="effb1-118">Windows PowerShell 內容提供者，因此，通常會定義所有的這些類別所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="effb1-118">A Windows PowerShell content provider, therefore, typically defines all of the functionality provided by those classes.</span></span>

<span data-ttu-id="effb1-119">如需如何實作功能，說明如何加入工作階段特定的初始化資訊，以及用於釋放提供者所使用的資源的詳細資訊，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="effb1-119">For more information about how to implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="effb1-120">不過，大部分的提供者，包括此處描述的提供者可以使用這項功能所提供的 Windows PowerShell 的預設實作。</span><span class="sxs-lookup"><span data-stu-id="effb1-120">However, most providers, including the provider described here, can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="effb1-121">若要存取資料存放區，提供者必須實作的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="effb1-121">To access the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="effb1-122">如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="effb1-122">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="effb1-123">若要操作的資料存放區，例如開始、 設定和清除項目，項目的提供者必須實作所提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="effb1-123">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="effb1-124">如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="effb1-124">For more information about implementing these methods, see [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="effb1-125">若要在多層資料存放區中工作，提供者必須實作所提供的方法[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="effb1-125">To work on multi-layer data stores, the provider must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="effb1-126">如需有關如何實作這些方法的詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="effb1-126">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

<span data-ttu-id="effb1-127">若要支援遞迴命令，巢狀的容器和相對路徑，提供者必須實作[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="effb1-127">To support recursive commands, nested containers, and relative paths, the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="effb1-128">此外，此 Windows PowerShell 內容提供者可以附加[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基底類別，並因此必須實作該類別所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-128">In addition, this Windows PowerShell content provider can attaches [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface to the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class, and must therefore implement the methods provided by that class.</span></span> <span data-ttu-id="effb1-129">如需詳細資訊，請參閱 < 實作這些方法，請參閱 <<c0> [ 實作的瀏覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="effb1-129">For more information, see implementing those methods, see [Implement a Navigation Windows PowerShell Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

## <a name="implementing-a-content-reader"></a><span data-ttu-id="effb1-130">實作內容的讀取器</span><span class="sxs-lookup"><span data-stu-id="effb1-130">Implementing a Content Reader</span></span>

<span data-ttu-id="effb1-131">若要讀取項目的內容，提供者必須實作內容的讀取器類別衍生自[System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)。</span><span class="sxs-lookup"><span data-stu-id="effb1-131">To read content from an item, a provider must implements a content reader class that derives from [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).</span></span> <span data-ttu-id="effb1-132">此提供者的內容讀取器資料表中的資料允許存取資料列的內容。</span><span class="sxs-lookup"><span data-stu-id="effb1-132">The content reader for this provider allows access to the contents of a row in a data table.</span></span> <span data-ttu-id="effb1-133">內容的讀取器類別會定義**讀取**方法，從指定的資料列擷取資料，並傳回表示該資料，清單**搜尋**方法，它會將內容的讀取器， **關閉**關閉之內容的讀取器的方法和**處置**方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-133">The content reader class defines a **Read** method that retrieves the data from the indicated row and returns a list representing that data, a **Seek** method that moves the content reader, a **Close** method that closes the content reader, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a><span data-ttu-id="effb1-134">實作內容的寫入器</span><span class="sxs-lookup"><span data-stu-id="effb1-134">Implementing a Content Writer</span></span>

<span data-ttu-id="effb1-135">若要寫入項目中的內容，提供者必須實作的內容寫入器類別衍生自[System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)。</span><span class="sxs-lookup"><span data-stu-id="effb1-135">To write content to an item, a provider must implement a content writer class derives from [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).</span></span> <span data-ttu-id="effb1-136">內容的寫入器類別會定義**撰寫**寫入指定的資料列內容，方法**Seek**方法，它會將內容寫入器，**關閉**關閉的方法內容的寫入器，以及**處置**方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-136">The content writer class defines a **Write** method that writes the specified row content, a **Seek** method that moves the content writer, a **Close** method that closes the content writer, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a><span data-ttu-id="effb1-137">擷取內容的讀取器</span><span class="sxs-lookup"><span data-stu-id="effb1-137">Retrieving the Content Reader</span></span>

<span data-ttu-id="effb1-138">若要取得內容項目，提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)支援`Get-Content`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="effb1-138">To get content from an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) to support the `Get-Content` cmdlet.</span></span> <span data-ttu-id="effb1-139">這個方法會傳回位於指定路徑的項目內容的讀取器。</span><span class="sxs-lookup"><span data-stu-id="effb1-139">This method returns the content reader for the item located at the specified path.</span></span> <span data-ttu-id="effb1-140">然後，讀取器物件可以開啟來讀取內容。</span><span class="sxs-lookup"><span data-stu-id="effb1-140">The reader object can then be opened to read the content.</span></span>

<span data-ttu-id="effb1-141">以下是實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)這個方法，此提供者。</span><span class="sxs-lookup"><span data-stu-id="effb1-141">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) for this method for this provider.</span></span>

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a><span data-ttu-id="effb1-142">有關實作 GetContentReader 的注意事項</span><span class="sxs-lookup"><span data-stu-id="effb1-142">Things to Remember About Implementing GetContentReader</span></span>

<span data-ttu-id="effb1-143">在下列情況可能適用於實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span><span class="sxs-lookup"><span data-stu-id="effb1-143">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span></span>

- <span data-ttu-id="effb1-144">Windows PowerShell 內容提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="effb1-144">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="effb1-145">在這些情況下，實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法必須確定傳遞給方法的路徑符合指定需求功能。</span><span class="sxs-lookup"><span data-stu-id="effb1-145">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="effb1-146">若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。</span><span class="sxs-lookup"><span data-stu-id="effb1-146">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="effb1-147">根據預設，會覆寫這個方法不應該擷取除非隱藏使用者物件的讀取器[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="effb1-147">By default, overrides of this method should not retrieve a reader for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="effb1-148">應該寫入錯誤，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="effb1-148">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a><span data-ttu-id="effb1-149">將動態參數附加至 Get-content Cmdlet</span><span class="sxs-lookup"><span data-stu-id="effb1-149">Attaching Dynamic Parameters to the Get-Content Cmdlet</span></span>

<span data-ttu-id="effb1-150">`Get-Content` Cmdlet 可能需要在執行階段動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="effb1-150">The `Get-Content` cmdlet might require additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="effb1-151">若要提供這些動態參數，Windows PowerShell 內容提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-151">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span> <span data-ttu-id="effb1-152">這個方法會擷取動態參數所指出的路徑處的項目，並傳回物件，此物件具有屬性與欄位類似於 cmdlet 類別屬性的剖析或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="effb1-152">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="effb1-153">Windows PowerShell 執行階段會使用傳回的物件，將參數新增至 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="effb1-153">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="effb1-154">此 Windows PowerShell 容器提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-154">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="effb1-155">不過，下列程式碼是這個方法的預設實作。</span><span class="sxs-lookup"><span data-stu-id="effb1-155">However, the following code is the default implementation of this method.</span></span>

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a><span data-ttu-id="effb1-156">擷取內容的寫入器</span><span class="sxs-lookup"><span data-stu-id="effb1-156">Retrieving the Content Writer</span></span>

<span data-ttu-id="effb1-157">若要寫入項目中的內容，提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)支援`Set-Content`和`Add-Content`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="effb1-157">To write content to an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) to support the `Set-Content` and `Add-Content` cmdlets.</span></span> <span data-ttu-id="effb1-158">這個方法會傳回位於指定路徑的項目內容的寫入器。</span><span class="sxs-lookup"><span data-stu-id="effb1-158">This method returns the content writer for the item located at the specified path.</span></span>

<span data-ttu-id="effb1-159">以下是實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)這個方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-159">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) for this method.</span></span>

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a><span data-ttu-id="effb1-160">有關實作 GetContentWriter 的注意事項</span><span class="sxs-lookup"><span data-stu-id="effb1-160">Things to Remember About Implementing GetContentWriter</span></span>

<span data-ttu-id="effb1-161">在下列情況可能適用於您實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span><span class="sxs-lookup"><span data-stu-id="effb1-161">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span></span>

- <span data-ttu-id="effb1-162">Windows PowerShell 內容提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="effb1-162">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="effb1-163">在這些情況下，實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法必須確定傳遞給方法的路徑符合指定需求功能。</span><span class="sxs-lookup"><span data-stu-id="effb1-163">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="effb1-164">若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。</span><span class="sxs-lookup"><span data-stu-id="effb1-164">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="effb1-165">根據預設，會覆寫這個方法不應該擷取除非隱藏使用者物件的寫入器[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="effb1-165">By default, overrides of this method should not retrieve a writer for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="effb1-166">應該寫入錯誤，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="effb1-166">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a><span data-ttu-id="effb1-167">將動態參數附加至 Add-content 和 Set-content Cmdlet</span><span class="sxs-lookup"><span data-stu-id="effb1-167">Attaching Dynamic Parameters to the Add-Content and Set-Content Cmdlets</span></span>

<span data-ttu-id="effb1-168">`Add-Content`和`Set-Content`cmdlet 可能需要加入執行階段的其他動態參數。</span><span class="sxs-lookup"><span data-stu-id="effb1-168">The `Add-Content` and `Set-Content` cmdlets might require additional dynamic parameters that are added a runtime.</span></span> <span data-ttu-id="effb1-169">若要提供這些動態參數，Windows PowerShell 內容提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)處理這些方法參數。</span><span class="sxs-lookup"><span data-stu-id="effb1-169">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="effb1-170">這個方法會擷取動態參數所指出的路徑處的項目，並傳回物件，此物件具有屬性與欄位類似於 cmdlet 類別屬性的剖析或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="effb1-170">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="effb1-171">Windows PowerShell 執行階段會使用傳回的物件，將參數新增至 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="effb1-171">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlets.</span></span>

<span data-ttu-id="effb1-172">此 Windows PowerShell 容器提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-172">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="effb1-173">不過，下列程式碼是這個方法的預設實作。</span><span class="sxs-lookup"><span data-stu-id="effb1-173">However, the following code is the default implementation of this method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a><span data-ttu-id="effb1-174">清除內容</span><span class="sxs-lookup"><span data-stu-id="effb1-174">Clearing Content</span></span>

<span data-ttu-id="effb1-175">您的內容提供者會實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)支援的方法`Clear-Content`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="effb1-175">Your content provider implements the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method in support of the `Clear-Content` cmdlet.</span></span> <span data-ttu-id="effb1-176">這個方法會移除在指定的路徑、 項目的內容，但會保留項目。</span><span class="sxs-lookup"><span data-stu-id="effb1-176">This method removes the contents of the item at the specified path, but leaves the item intact.</span></span>

<span data-ttu-id="effb1-177">以下是實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)此提供者的方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-177">Here is the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method for this provider.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a><span data-ttu-id="effb1-178">有關實作 ClearContent 的注意事項</span><span class="sxs-lookup"><span data-stu-id="effb1-178">Things to Remember About Implementing ClearContent</span></span>

<span data-ttu-id="effb1-179">在下列情況可能適用於實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span><span class="sxs-lookup"><span data-stu-id="effb1-179">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span></span>

- <span data-ttu-id="effb1-180">Windows PowerShell 內容提供者時定義的提供者類別，可能會從宣告提供者的功能 ExpandWildcards、 篩選、 Include 或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="effb1-180">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="effb1-181">在這些情況下，實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法必須確定傳遞給方法的路徑符合指定需求功能。</span><span class="sxs-lookup"><span data-stu-id="effb1-181">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="effb1-182">若要這樣做，方法應該存取適當的屬性，例如， [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)屬性。</span><span class="sxs-lookup"><span data-stu-id="effb1-182">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="effb1-183">根據預設，覆寫這個方法不應清除的物件，除非使用者隱藏的內容[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="effb1-183">By default, overrides of this method should not clear the contents of objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="effb1-184">應該寫入錯誤，若路徑代表會對使用者隱藏的項目和[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="effb1-184">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

- <span data-ttu-id="effb1-185">您實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)並確認它的傳回值之前對資料存放區中的任何變更。</span><span class="sxs-lookup"><span data-stu-id="effb1-185">Your implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and verify its return value before making any changes to the data store.</span></span> <span data-ttu-id="effb1-186">這個方法用來變更資料存放區，例如清除內容時，請確認執行作業。</span><span class="sxs-lookup"><span data-stu-id="effb1-186">This method is used to confirm execution of an operation when a change is made to the data store, such as clearing content.</span></span> <span data-ttu-id="effb1-187">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會傳送給使用者，以處理任何命令列設定或喜好設定，Windows PowerShell 執行階段變更資源的名稱在決定應該要顯示的內容變數。</span><span class="sxs-lookup"><span data-stu-id="effb1-187">The [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) method sends the name of the resource to be changed to the user, with the Windows PowerShell runtime handling any command-line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="effb1-188">若要在呼叫之後[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)會傳回`true`，則[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法應該呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-188">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="effb1-189">這個方法會將訊息傳送給使用者，以允許確認是否應該繼續執行作業的意見反應。</span><span class="sxs-lookup"><span data-stu-id="effb1-189">This method sends a message to the user to allow feedback to verify if the operation should be continued.</span></span> <span data-ttu-id="effb1-190">若要在呼叫[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允許額外的檢查，如有潛在危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="effb1-190">The call to [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) allows an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a><span data-ttu-id="effb1-191">附加至 Clear-content Cmdlet 的動態參數</span><span class="sxs-lookup"><span data-stu-id="effb1-191">Attaching Dynamic Parameters to the Clear-Content Cmdlet</span></span>

<span data-ttu-id="effb1-192">`Clear-Content` Cmdlet 可能需要在執行階段加入的其他動態參數。</span><span class="sxs-lookup"><span data-stu-id="effb1-192">The `Clear-Content` cmdlet might require additional dynamic parameters that are added at runtime.</span></span> <span data-ttu-id="effb1-193">若要提供這些動態參數，Windows PowerShell 內容提供者必須實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)處理這些方法參數。</span><span class="sxs-lookup"><span data-stu-id="effb1-193">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="effb1-194">這個方法會擷取位於指定路徑的項目參數。</span><span class="sxs-lookup"><span data-stu-id="effb1-194">This method retrieves the parameters for the item at the indicated path.</span></span> <span data-ttu-id="effb1-195">這個方法會擷取動態參數所指出的路徑處的項目，並傳回物件，此物件具有屬性與欄位類似於 cmdlet 類別屬性的剖析或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="effb1-195">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="effb1-196">Windows PowerShell 執行階段會使用傳回的物件，將參數新增至 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="effb1-196">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="effb1-197">此 Windows PowerShell 容器提供者未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="effb1-197">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="effb1-198">不過，下列程式碼是這個方法的預設實作。</span><span class="sxs-lookup"><span data-stu-id="effb1-198">However, the following code is the default implementation of this method.</span></span>

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a><span data-ttu-id="effb1-199">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="effb1-199">Code Sample</span></span>

<span data-ttu-id="effb1-200">完整的範例程式碼，請參閱[AccessDbProviderSample06 程式碼範例](./accessdbprovidersample06-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="effb1-200">For complete sample code, see [AccessDbProviderSample06 Code Sample](./accessdbprovidersample06-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="effb1-201">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="effb1-201">Defining Object Types and Formatting</span></span>

<span data-ttu-id="effb1-202">當撰寫提供者，它可能需要將成員加入至現有的物件，或定義新的物件。</span><span class="sxs-lookup"><span data-stu-id="effb1-202">When writing a provider, it may be necessary to add members to existing objects or define new objects.</span></span> <span data-ttu-id="effb1-203">完成時，您必須建立 Windows PowerShell 可以用來識別物件的成員類型檔案與格式檔案，定義物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="effb1-203">When this is done, you must create a Types file that Windows PowerShell can use to identify the members of the object and a Format file that defines how the object is displayed.</span></span> <span data-ttu-id="effb1-204">如需詳細資訊，請參閱 <<c0> [ 延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="effb1-204">For more information, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="effb1-205">建置 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="effb1-205">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="effb1-206">請參閱[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="effb1-206">See [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="effb1-207">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="effb1-207">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="effb1-208">當您的 Windows PowerShell 提供者已向 Windows PowerShell 時，您可以藉由在命令列上執行受支援的 cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="effb1-208">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="effb1-209">例如，測試範例的內容提供者。</span><span class="sxs-lookup"><span data-stu-id="effb1-209">For example, test the sample content provider.</span></span>

<span data-ttu-id="effb1-210">使用`Get-Content`cmdlet 來擷取所指定路徑上的資料庫資料表中的指定項目的內容`Path`參數。</span><span class="sxs-lookup"><span data-stu-id="effb1-210">Use the `Get-Content` cmdlet to retrieve the contents of specified item in the database table at the path specified by the `Path` parameter.</span></span> <span data-ttu-id="effb1-211">`ReadCount`參數會指定定義內容的讀取器讀取 （預設值 1） 的項目數。</span><span class="sxs-lookup"><span data-stu-id="effb1-211">The `ReadCount` parameter specifies the number of items for the defined content reader to read (default 1).</span></span> <span data-ttu-id="effb1-212">下列命令項目，此 cmdlet 會從資料表中擷取兩個資料列 （項目），並顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="effb1-212">With the following command entry, the cmdlet retrieves two rows (items) from the table and displays their contents.</span></span> <span data-ttu-id="effb1-213">請注意，下列範例輸出會使用虛構的 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="effb1-213">Note that the following example output uses a fictitious Access database.</span></span>

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
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

## <a name="see-also"></a><span data-ttu-id="effb1-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="effb1-214">See Also</span></span>

[<span data-ttu-id="effb1-215">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="effb1-215">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="effb1-216">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="effb1-216">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="effb1-217">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="effb1-217">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="effb1-218">實作瀏覽 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="effb1-218">Implement a Navigation Windows PowerShell provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

[<span data-ttu-id="effb1-219">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="effb1-219">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="effb1-220">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="effb1-220">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="effb1-221">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="effb1-221">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
