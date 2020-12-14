---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 Windows PowerShell 內容提供者
description: 建立 Windows PowerShell 內容提供者
ms.openlocfilehash: 7890f0ab8d1cc7f29bdc077b342bae950cfa7827
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645368"
---
# <a name="creating-a-windows-powershell-content-provider"></a><span data-ttu-id="ef41e-103">建立 Windows PowerShell 內容提供者</span><span class="sxs-lookup"><span data-stu-id="ef41e-103">Creating a Windows PowerShell Content Provider</span></span>

<span data-ttu-id="ef41e-104">本主題說明如何建立 Windows PowerShell 提供者，讓使用者能夠運算元據存放區中的專案內容。</span><span class="sxs-lookup"><span data-stu-id="ef41e-104">This topic describes how to create a Windows PowerShell provider that enables the user to manipulate the contents of the items in a data store.</span></span> <span data-ttu-id="ef41e-105">因此，可操作專案內容的提供者稱為 Windows PowerShell 內容提供者。</span><span class="sxs-lookup"><span data-stu-id="ef41e-105">As a consequence, a provider that can manipulate the contents of items is referred to as a Windows PowerShell content provider.</span></span>

> [!NOTE]
> <span data-ttu-id="ef41e-106">您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此提供者的 c # 原始程式檔 (AccessDBSampleProvider06.cs) 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-106">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ef41e-107">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="ef41e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="ef41e-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="ef41e-109">如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ef41e-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="define-the-windows-powershell-content-provider-class"></a><span data-ttu-id="ef41e-110">定義 Windows PowerShell 內容提供者類別</span><span class="sxs-lookup"><span data-stu-id="ef41e-110">Define the Windows PowerShell Content Provider Class</span></span>

<span data-ttu-id="ef41e-111">Windows PowerShell 的內容提供者必須建立支援 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面的 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="ef41e-111">A Windows PowerShell content provider must create a .NET class that supports the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span> <span data-ttu-id="ef41e-112">以下是本節所述之專案提供者的類別定義。</span><span class="sxs-lookup"><span data-stu-id="ef41e-112">Here is the class definition for the item provider described in this section.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="32-33":::

<span data-ttu-id="ef41e-113">請注意，在此類別定義中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="ef41e-113">Note that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="ef41e-114">第一個參數會指定 Windows PowerShell 所使用之提供者的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="ef41e-114">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="ef41e-115">第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="ef41e-115">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="ef41e-116">對於此提供者，沒有新增 Windows PowerShell 的特定功能。</span><span class="sxs-lookup"><span data-stu-id="ef41e-116">For this provider, there are no added Windows PowerShell specific capabilities.</span></span>

## <a name="define-functionality-of-base-class"></a><span data-ttu-id="ef41e-117">定義基類的功能</span><span class="sxs-lookup"><span data-stu-id="ef41e-117">Define Functionality of Base Class</span></span>

<span data-ttu-id="ef41e-118">如 [設計您的 Windows PowerShell 提供](./designing-your-windows-powershell-provider.md)者所述， [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別衍生自數個提供不同提供者功能的其他類別。</span><span class="sxs-lookup"><span data-stu-id="ef41e-118">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="ef41e-119">因此，Windows PowerShell 內容提供者，通常會定義這些類別所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="ef41e-119">A Windows PowerShell content provider, therefore, typically defines all of the functionality provided by those classes.</span></span>

<span data-ttu-id="ef41e-120">如需如何執行新增會話特定初始化資訊，以及釋出提供者所用資源之功能的詳細資訊，請參閱 [建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ef41e-120">For more information about how to implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="ef41e-121">不過，大部分的提供者（包括此處所述的提供者）可以使用 Windows PowerShell 所提供的這項功能的預設執行。</span><span class="sxs-lookup"><span data-stu-id="ef41e-121">However, most providers, including the provider described here, can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="ef41e-122">若要存取資料存放區，提供者必須在 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 基類的方法中執行。</span><span class="sxs-lookup"><span data-stu-id="ef41e-122">To access the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="ef41e-123">如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ef41e-123">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="ef41e-124">若要運算元據存放區的專案，例如取得、設定和清除專案，提供者必須執行 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="ef41e-124">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="ef41e-125">如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ef41e-125">For more information about implementing these methods, see [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="ef41e-126">若要處理多層式資料存放區，提供者必須執行 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 基類所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="ef41e-126">To work on multi-layer data stores, the provider must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="ef41e-127">如需有關如何執行這些方法的詳細資訊，請參閱 [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ef41e-127">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

<span data-ttu-id="ef41e-128">為了支援遞迴命令、嵌套的容器和相對路徑，提供者必須執行 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 基類。</span><span class="sxs-lookup"><span data-stu-id="ef41e-128">To support recursive commands, nested containers, and relative paths, the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="ef41e-129">此外，這個 Windows PowerShell 內容提供者可將 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面附加至 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 基類，因此必須執行該類別所提供的方法，才能執行。」。</span><span class="sxs-lookup"><span data-stu-id="ef41e-129">In addition, this Windows PowerShell content provider can attaches [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface to the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class, and must therefore implement the methods provided by that class.</span></span> <span data-ttu-id="ef41e-130">如需詳細資訊，請參閱實作為這些方法的詳細資訊，請參閱 [執行導覽 Windows PowerShell 提供者](./creating-a-windows-powershell-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ef41e-130">For more information, see implementing those methods, see [Implement a Navigation Windows PowerShell Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

## <a name="implementing-a-content-reader"></a><span data-ttu-id="ef41e-131">執行內容讀取程式</span><span class="sxs-lookup"><span data-stu-id="ef41e-131">Implementing a Content Reader</span></span>

<span data-ttu-id="ef41e-132">若要從專案讀取內容，提供者必須執行衍生自 [Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)的內容讀取者類別。</span><span class="sxs-lookup"><span data-stu-id="ef41e-132">To read content from an item, a provider must implements a content reader class that derives from [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).</span></span>
<span data-ttu-id="ef41e-133">此提供者的內容讀取器允許存取資料表中的資料列內容。</span><span class="sxs-lookup"><span data-stu-id="ef41e-133">The content reader for this provider allows access to the contents of a row in a data table.</span></span> <span data-ttu-id="ef41e-134">內容讀取器類別會定義 **讀取** 方法，該方法會從指定的資料列抓取資料，並傳回代表該資料的清單、移動內容讀取器的 **Seek** 方法、關閉內容讀取器的 **關閉** 方法，以及 **處置** 方法。</span><span class="sxs-lookup"><span data-stu-id="ef41e-134">The content reader class defines a **Read** method that retrieves the data from the indicated row and returns a list representing that data, a **Seek** method that moves the content reader, a **Close** method that closes the content reader, and a **Dispose** method.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="2115-2241":::

## <a name="implementing-a-content-writer"></a><span data-ttu-id="ef41e-135">執行內容寫入器</span><span class="sxs-lookup"><span data-stu-id="ef41e-135">Implementing a Content Writer</span></span>

<span data-ttu-id="ef41e-136">若要將內容寫入至專案，提供者必須執行從 [Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)衍生的內容寫入器類別。</span><span class="sxs-lookup"><span data-stu-id="ef41e-136">To write content to an item, a provider must implement a content writer class derives from [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).</span></span>
<span data-ttu-id="ef41e-137">內容寫入器類別會定義 **寫入** 方法，以寫入指定的資料列內容、移動內容寫入器的 **Seek** 方法、關閉內容寫入器的 **Close** 方法，以及 **Dispose** 方法。</span><span class="sxs-lookup"><span data-stu-id="ef41e-137">The content writer class defines a **Write** method that writes the specified row content, a **Seek** method that moves the content writer, a **Close** method that closes the content writer, and a **Dispose** method.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="2250-2394":::

## <a name="retrieving-the-content-reader"></a><span data-ttu-id="ef41e-138">正在抓取內容讀取器</span><span class="sxs-lookup"><span data-stu-id="ef41e-138">Retrieving the Content Reader</span></span>

<span data-ttu-id="ef41e-139">若要從專案取得內容，提供者必須執行 [IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 以支援 `Get-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef41e-139">To get content from an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) to support the `Get-Content` cmdlet.</span></span> <span data-ttu-id="ef41e-140">這個方法會傳回位於指定路徑之專案的內容讀取器。</span><span class="sxs-lookup"><span data-stu-id="ef41e-140">This method returns the content reader for the item located at the specified path.</span></span> <span data-ttu-id="ef41e-141">然後可以開啟讀取器物件來讀取內容。</span><span class="sxs-lookup"><span data-stu-id="ef41e-141">The reader object can then be opened to read the content.</span></span>

<span data-ttu-id="ef41e-142">以下是適用于此提供者之這個方法的 [IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 的實作為。</span><span class="sxs-lookup"><span data-stu-id="ef41e-142">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) for this method for this provider.</span></span>

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1829-1846":::

#### <a name="things-to-remember-about-implementing-getcontentreader"></a><span data-ttu-id="ef41e-143">執行 GetContentReader 的注意事項</span><span class="sxs-lookup"><span data-stu-id="ef41e-143">Things to Remember About Implementing GetContentReader</span></span>

<span data-ttu-id="ef41e-144">下列情況可能適用于 [IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)的實作為：</span><span class="sxs-lookup"><span data-stu-id="ef41e-144">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span></span>

- <span data-ttu-id="ef41e-145">定義提供者類別時，Windows PowerShell 內容提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="ef41e-145">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="ef41e-146">在這些情況下，IcontentCmdletprovider 的執行必須確定傳遞至方法的路徑符合指定之功能的需求，才能執行此 [程式](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-146">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="ef41e-147">若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include \* properties. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 \* 屬性）。</span><span class="sxs-lookup"><span data-stu-id="ef41e-147">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="ef41e-148">根據預設，除非 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則，此方法的覆寫不應針對使用者所隱藏的物件，取得讀取 `true` 器。</span><span class="sxs-lookup"><span data-stu-id="ef41e-148">By default, overrides of this method should not retrieve a reader for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="ef41e-149">如果路徑代表隱藏于使用者和 Cmdletprovider 中的專案，則應該撰寫錯誤。 [Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 會設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-149">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a><span data-ttu-id="ef41e-150">將動態參數附加至 Get-Content Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef41e-150">Attaching Dynamic Parameters to the Get-Content Cmdlet</span></span>

<span data-ttu-id="ef41e-151">`Get-Content`Cmdlet 可能需要在執行時間動態指定的其他參數。</span><span class="sxs-lookup"><span data-stu-id="ef41e-151">The `Get-Content` cmdlet might require additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="ef41e-152">若要提供這些動態參數，Windows PowerShell 內容提供者必須執行 [IcontentCmdletprovider. Getcontentreaderdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 方法。</span><span class="sxs-lookup"><span data-stu-id="ef41e-152">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span> <span data-ttu-id="ef41e-153">這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。</span><span class="sxs-lookup"><span data-stu-id="ef41e-153">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="ef41e-154">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef41e-154">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="ef41e-155">此 Windows PowerShell 容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="ef41e-155">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="ef41e-156">但是，下列程式碼是此方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="ef41e-156">However, the following code is the default implementation of this method.</span></span>

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1853-1856":::

## <a name="retrieving-the-content-writer"></a><span data-ttu-id="ef41e-157">正在抓取內容寫入器</span><span class="sxs-lookup"><span data-stu-id="ef41e-157">Retrieving the Content Writer</span></span>

<span data-ttu-id="ef41e-158">若要將內容寫入至專案，提供者必須執行 [IcontentCmdletprovider. Getcontentwriter \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 以支援 `Set-Content` 和 `Add-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef41e-158">To write content to an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) to support the `Set-Content` and `Add-Content` cmdlets.</span></span> <span data-ttu-id="ef41e-159">這個方法會傳回位於指定路徑之專案的內容寫入器。</span><span class="sxs-lookup"><span data-stu-id="ef41e-159">This method returns the content writer for the item located at the specified path.</span></span>

<span data-ttu-id="ef41e-160">以下是適用于此方法的 [IcontentCmdletprovider. Getcontentwriter \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 的實作為。</span><span class="sxs-lookup"><span data-stu-id="ef41e-160">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) for this method.</span></span>

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1863-1880":::

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a><span data-ttu-id="ef41e-161">執行 GetContentWriter 的注意事項</span><span class="sxs-lookup"><span data-stu-id="ef41e-161">Things to Remember About Implementing GetContentWriter</span></span>

<span data-ttu-id="ef41e-162">下列情況可能適用于您的 [IcontentCmdletprovider. Getcontentwriter \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)的執行：</span><span class="sxs-lookup"><span data-stu-id="ef41e-162">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span></span>

- <span data-ttu-id="ef41e-163">定義提供者類別時，Windows PowerShell 內容提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="ef41e-163">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="ef41e-164">在這些情況下，IcontentCmdletprovider 的執行必須確定傳遞至方法的路徑符合指定之功能的需求，才能執行此 [程式](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-164">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="ef41e-165">若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include \* properties. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 \* 屬性）。</span><span class="sxs-lookup"><span data-stu-id="ef41e-165">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="ef41e-166">根據預設，除非 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則，此方法的覆寫不應針對使用者隱藏的物件取得寫入 `true` 器。</span><span class="sxs-lookup"><span data-stu-id="ef41e-166">By default, overrides of this method should not retrieve a writer for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="ef41e-167">如果路徑代表隱藏于使用者和 Cmdletprovider 中的專案，則應該撰寫錯誤。 [Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 會設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-167">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a><span data-ttu-id="ef41e-168">將動態參數附加至 Add-Content 和 Set-Content Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef41e-168">Attaching Dynamic Parameters to the Add-Content and Set-Content Cmdlets</span></span>

<span data-ttu-id="ef41e-169">`Add-Content`和 `Set-Content` Cmdlet 可能需要加入執行時間的額外動態參數。</span><span class="sxs-lookup"><span data-stu-id="ef41e-169">The `Add-Content` and `Set-Content` cmdlets might require additional dynamic parameters that are added a runtime.</span></span> <span data-ttu-id="ef41e-170">若要提供這些動態參數，Windows PowerShell 內容提供者必須執行 [IcontentCmdletprovider. Getcontentwriterdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="ef41e-170">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="ef41e-171">這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。</span><span class="sxs-lookup"><span data-stu-id="ef41e-171">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="ef41e-172">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef41e-172">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlets.</span></span>

<span data-ttu-id="ef41e-173">此 Windows PowerShell 容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="ef41e-173">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="ef41e-174">但是，下列程式碼是此方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="ef41e-174">However, the following code is the default implementation of this method.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1887-1890":::

## <a name="clearing-content"></a><span data-ttu-id="ef41e-175">清除內容</span><span class="sxs-lookup"><span data-stu-id="ef41e-175">Clearing Content</span></span>

<span data-ttu-id="ef41e-176">您的內容提供者在支援 Cmdlet 時，會執行 [IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 方法 `Clear-Content` 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-176">Your content provider implements the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method in support of the `Clear-Content` cmdlet.</span></span> <span data-ttu-id="ef41e-177">這個方法會在指定的路徑移除專案的內容，但不會讓專案保持不變。</span><span class="sxs-lookup"><span data-stu-id="ef41e-177">This method removes the contents of the item at the specified path, but leaves the item intact.</span></span>

<span data-ttu-id="ef41e-178">以下是此提供者的 [IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 方法的執行方式。</span><span class="sxs-lookup"><span data-stu-id="ef41e-178">Here is the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method for this provider.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1775-1812":::

#### <a name="things-to-remember-about-implementing-clearcontent"></a><span data-ttu-id="ef41e-179">執行 ClearContent 的注意事項</span><span class="sxs-lookup"><span data-stu-id="ef41e-179">Things to Remember About Implementing ClearContent</span></span>

<span data-ttu-id="ef41e-180">下列情況可能適用于 [IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)的實作為：</span><span class="sxs-lookup"><span data-stu-id="ef41e-180">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span></span>

- <span data-ttu-id="ef41e-181">定義提供者類別時，Windows PowerShell 內容提供者可能會從 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉宣告 ExpandWildcards、篩選、包含或排除的提供者功能。</span><span class="sxs-lookup"><span data-stu-id="ef41e-181">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="ef41e-182">在這些情況下，IcontentCmdletprovider 的執行必須確定傳遞至方法的路徑符合指定之功能的需求，才能執行此 [程式](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-182">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="ef41e-183">若要這樣做，方法應該存取適當的屬性，例如 [Cmdletprovider。 Exclude \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) [Cmdletprovider. Include \* properties. Include \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties. （包含 \* 屬性）。</span><span class="sxs-lookup"><span data-stu-id="ef41e-183">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="ef41e-184">根據預設，除非 [Cmdletprovider. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 屬性設為，否則，此方法的覆寫不應清除使用者隱藏的物件內容 `true` 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-184">By default, overrides of this method should not clear the contents of objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="ef41e-185">如果路徑代表隱藏于使用者和 Cmdletprovider 中的專案，則應該撰寫錯誤。 [Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 會設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-185">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

- <span data-ttu-id="ef41e-186">您的 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 應該會在對資料存放區進行任何變更之前，先呼叫 [Cmdletprovider.. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 並驗證其傳回值的方法，才能執行。</span><span class="sxs-lookup"><span data-stu-id="ef41e-186">Your implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and verify its return value before making any changes to the data store.</span></span> <span data-ttu-id="ef41e-187">當變更資料存放區（例如清除內容）時，會使用這個方法來確認作業的執行。</span><span class="sxs-lookup"><span data-stu-id="ef41e-187">This method is used to confirm execution of an operation when a change is made to the data store, such as clearing content.</span></span> <span data-ttu-id="ef41e-188">[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法會傳送要變更給使用者的資源名稱，並以 Windows PowerShell 執行時間處理任何命令列設定或喜好設定變數，以決定應該顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="ef41e-188">The [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) method sends the name of the resource to be changed to the user, with the Windows PowerShell runtime handling any command-line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="ef41e-189">呼叫 Cmdletprovider 之後， [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) `true` 會傳回， [IcontentCmdletprovider.. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 方法應該呼叫 [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ，以呼叫 system.object.. \* 方法來呼叫. 管理方法。</span><span class="sxs-lookup"><span data-stu-id="ef41e-189">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="ef41e-190">這個方法會將訊息傳送給使用者，以允許意見反應確認作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="ef41e-190">This method sends a message to the user to allow feedback to verify if the operation should be continued.</span></span> <span data-ttu-id="ef41e-191">對 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 的呼叫，可允許額外檢查可能有危險的系統修改。</span><span class="sxs-lookup"><span data-stu-id="ef41e-191">The call to [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) allows an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a><span data-ttu-id="ef41e-192">將動態參數附加至 Clear-Content Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef41e-192">Attaching Dynamic Parameters to the Clear-Content Cmdlet</span></span>

<span data-ttu-id="ef41e-193">此 `Clear-Content` Cmdlet 可能需要在執行時間新增的額外動態參數。</span><span class="sxs-lookup"><span data-stu-id="ef41e-193">The `Clear-Content` cmdlet might require additional dynamic parameters that are added at runtime.</span></span> <span data-ttu-id="ef41e-194">若要提供這些動態參數，Windows PowerShell 內容提供者必須執行 [IcontentCmdletprovider. Clearcontentdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 方法來處理這些參數。</span><span class="sxs-lookup"><span data-stu-id="ef41e-194">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="ef41e-195">這個方法會在指定的路徑上，抓取專案的參數。</span><span class="sxs-lookup"><span data-stu-id="ef41e-195">This method retrieves the parameters for the item at the indicated path.</span></span> <span data-ttu-id="ef41e-196">這個方法會在指定的路徑上抓取專案的動態參數，並傳回物件，該物件具有剖析屬性的屬性和欄位，類似于 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件。</span><span class="sxs-lookup"><span data-stu-id="ef41e-196">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="ef41e-197">Windows PowerShell 執行時間會使用傳回的物件，將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef41e-197">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="ef41e-198">此 Windows PowerShell 容器提供者不會執行此方法。</span><span class="sxs-lookup"><span data-stu-id="ef41e-198">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="ef41e-199">但是，下列程式碼是此方法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="ef41e-199">However, the following code is the default implementation of this method.</span></span>

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1819-1822":::

## <a name="code-sample"></a><span data-ttu-id="ef41e-200">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="ef41e-200">Code Sample</span></span>

<span data-ttu-id="ef41e-201">如需完整的範例程式碼，請參閱 [AccessDbProviderSample06 程式碼範例](./accessdbprovidersample06-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ef41e-201">For complete sample code, see [AccessDbProviderSample06 Code Sample](./accessdbprovidersample06-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="ef41e-202">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="ef41e-202">Defining Object Types and Formatting</span></span>

<span data-ttu-id="ef41e-203">撰寫提供者時，可能需要將成員新增至現有的物件，或定義新的物件。</span><span class="sxs-lookup"><span data-stu-id="ef41e-203">When writing a provider, it may be necessary to add members to existing objects or define new objects.</span></span> <span data-ttu-id="ef41e-204">完成這項操作之後，您必須建立一個類型檔案，Windows PowerShell 可以用來識別物件的成員，以及定義如何顯示物件的格式檔案。</span><span class="sxs-lookup"><span data-stu-id="ef41e-204">When this is done, you must create a Types file that Windows PowerShell can use to identify the members of the object and a Format file that defines how the object is displayed.</span></span> <span data-ttu-id="ef41e-205">如需詳細資訊，請參閱 [擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="ef41e-205">For more information, see [Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="ef41e-206">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="ef41e-206">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="ef41e-207">瞭解 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="ef41e-207">See [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="ef41e-208">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="ef41e-208">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="ef41e-209">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="ef41e-209">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="ef41e-210">例如，測試範例內容提供者。</span><span class="sxs-lookup"><span data-stu-id="ef41e-210">For example, test the sample content provider.</span></span>

<span data-ttu-id="ef41e-211">您 `Get-Content` 可以使用 Cmdlet，在參數所指定的路徑上，取得資料庫資料表中指定專案的內容 `Path` 。</span><span class="sxs-lookup"><span data-stu-id="ef41e-211">Use the `Get-Content` cmdlet to retrieve the contents of specified item in the database table at the path specified by the `Path` parameter.</span></span> <span data-ttu-id="ef41e-212">`ReadCount`參數會指定已定義內容讀取器要讀取 (預設值 1) 的專案數目。</span><span class="sxs-lookup"><span data-stu-id="ef41e-212">The `ReadCount` parameter specifies the number of items for the defined content reader to read (default 1).</span></span> <span data-ttu-id="ef41e-213">使用下列命令輸入，Cmdlet 會從資料表中抓取兩個數據列 (專案) ，並顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="ef41e-213">With the following command entry, the cmdlet retrieves two rows (items) from the table and displays their contents.</span></span> <span data-ttu-id="ef41e-214">請注意，下列範例輸出會使用虛構的 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ef41e-214">Note that the following example output uses a fictitious Access database.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef41e-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef41e-215">See Also</span></span>

[<span data-ttu-id="ef41e-216">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="ef41e-216">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="ef41e-217">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="ef41e-217">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

<span data-ttu-id="ef41e-218">[擴充物件類型和格式化](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ef41e-218">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

[<span data-ttu-id="ef41e-219">執行流覽 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="ef41e-219">Implement a Navigation Windows PowerShell provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

<span data-ttu-id="ef41e-220">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ef41e-220">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="ef41e-221">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ef41e-221">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="ef41e-222">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="ef41e-222">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
