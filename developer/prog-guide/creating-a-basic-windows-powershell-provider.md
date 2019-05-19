---
title: 建立基本的 Windows PowerShell 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 5ebc22067b20f0e1d35d31d5f33e599f50cb7564
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855074"
---
# <a name="creating-a-basic-windows-powershell-provider"></a><span data-ttu-id="36eec-102">建立基本的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="36eec-102">Creating a Basic Windows PowerShell Provider</span></span>

<span data-ttu-id="36eec-103">本主題是起始點，以了解如何建立 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="36eec-103">This topic is the starting point for learning how to create a Windows PowerShell provider.</span></span> <span data-ttu-id="36eec-104">此處所述的基本提供者會提供方法來啟動和停止提供者，與此提供者不能用來存取資料存放區，或取得或設定資料存放區中的資料，雖然它提供所需的基本功能所有的提供者。</span><span class="sxs-lookup"><span data-stu-id="36eec-104">The basic provider described here provides methods for starting and stopping the provider, and although this provider does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

<span data-ttu-id="36eec-105">前面提過，所述的基本提供者這裡實作方法來啟動和停止提供者。</span><span class="sxs-lookup"><span data-stu-id="36eec-105">As mentioned previously, the basic provider described here implements methods for starting and stopping the provider.</span></span> <span data-ttu-id="36eec-106">Windows PowerShell 執行階段呼叫這些方法來初始化，並取消初始化提供者。</span><span class="sxs-lookup"><span data-stu-id="36eec-106">The Windows PowerShell runtime calls these methods to initialize and uninitialize the provider.</span></span>

> [!NOTE]
> <span data-ttu-id="36eec-107">您可以在 Windows PowerShell 所提供的 AccessDBSampleProvider01.cs 檔案中找到此提供者的範例。</span><span class="sxs-lookup"><span data-stu-id="36eec-107">You can find a sample of this provider in the AccessDBSampleProvider01.cs file provided by Windows PowerShell.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="36eec-108">定義 Windows PowerShell 提供者類別</span><span class="sxs-lookup"><span data-stu-id="36eec-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="36eec-109">建立 Windows PowerShell 提供者的第一個步驟是定義它的.NET 類別。</span><span class="sxs-lookup"><span data-stu-id="36eec-109">The first step in creating a Windows PowerShell provider is to define its .NET class.</span></span> <span data-ttu-id="36eec-110">此基本提供者會定義一個叫做類別`AccessDBProvider`衍生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="36eec-110">This basic provider defines a class called `AccessDBProvider` that derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class.</span></span>

<span data-ttu-id="36eec-111">建議您將放在您提供者類別`Providers`API 命名空間，比方說，xxx 的命名空間。PowerShell.Providers。</span><span class="sxs-lookup"><span data-stu-id="36eec-111">It is recommended that you place your provider classes in a `Providers` namespace of your API namespace, for example, xxx.PowerShell.Providers.</span></span> <span data-ttu-id="36eec-112">此提供者使用`Microsoft.Samples.PowerShell.Provider`命名空間，在其中執行所有的 Windows PowerShell 提供者範例。</span><span class="sxs-lookup"><span data-stu-id="36eec-112">This provider uses the `Microsoft.Samples.PowerShell.Provider` namespace, in which all Windows PowerShell provider samples run.</span></span>

> [!NOTE]
> <span data-ttu-id="36eec-113">Windows PowerShell 提供者的類別必須明確標示為公用。</span><span class="sxs-lookup"><span data-stu-id="36eec-113">The class for a Windows PowerShell provider must be explicitly marked as public.</span></span> <span data-ttu-id="36eec-114">未標示為公用的類別會預設為內部，並且將找不到 Windows PowerShell 執行階段。</span><span class="sxs-lookup"><span data-stu-id="36eec-114">Classes not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="36eec-115">以下是此基本提供者的類別定義：</span><span class="sxs-lookup"><span data-stu-id="36eec-115">Here is the class definition for this basic provider:</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

<span data-ttu-id="36eec-116">直接在類別定義之前，您必須宣告[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性，且 [CmdletProvider()] 的語法。</span><span class="sxs-lookup"><span data-stu-id="36eec-116">Right before the class definition, you must declare the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute, with the syntax [CmdletProvider()].</span></span>

<span data-ttu-id="36eec-117">您可以設定屬性的關鍵字，以進一步在必要時在類別宣告。</span><span class="sxs-lookup"><span data-stu-id="36eec-117">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="36eec-118">請注意， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)此宣告的屬性包括兩個參數。</span><span class="sxs-lookup"><span data-stu-id="36eec-118">Notice that the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute declared here includes two parameters.</span></span> <span data-ttu-id="36eec-119">第一個屬性參數會指定預設的易記名稱的提供者，使用者之後可以修改。</span><span class="sxs-lookup"><span data-stu-id="36eec-119">The first attribute parameter specifies the default-friendly name for the provider, which the user can modify later.</span></span> <span data-ttu-id="36eec-120">第二個參數指定命令處理期間提供者會公開 Windows PowerShell 執行階段的 Windows PowerShell 定義功能。</span><span class="sxs-lookup"><span data-stu-id="36eec-120">The second parameter specifies the Windows PowerShell-defined capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="36eec-121">所定義的提供者功能的可能值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="36eec-121">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="36eec-122">因為這是基底提供者時，它會支援任何功能。</span><span class="sxs-lookup"><span data-stu-id="36eec-122">Because this is a base provider, it supports no capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="36eec-123">Windows PowerShell 提供者的完整的名稱包括組件名稱和其他屬性取決於 Windows PowerShell 提供者註冊時。</span><span class="sxs-lookup"><span data-stu-id="36eec-123">The fully qualified name of the Windows PowerShell provider includes the assembly name and other attributes determined by Windows PowerShell upon registration of the provider.</span></span>

## <a name="defining-provider-specific-state-information"></a><span data-ttu-id="36eec-124">定義提供者專屬的狀態資訊</span><span class="sxs-lookup"><span data-stu-id="36eec-124">Defining Provider-Specific State Information</span></span>

<span data-ttu-id="36eec-125">[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基底類別及所有衍生的類別會視為無狀態，因為 Windows PowerShell 執行階段會建立只有所需的提供者執行個體。</span><span class="sxs-lookup"><span data-stu-id="36eec-125">The [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class and all derived classes are considered stateless because the Windows PowerShell runtime creates provider instances only as required.</span></span> <span data-ttu-id="36eec-126">因此，如果您的提供者的提供者特定資料，需要完整控制和維護狀態，它必須衍生的類別[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)類別。</span><span class="sxs-lookup"><span data-stu-id="36eec-126">Therefore, if your provider requires full control and state maintenance for provider-specific data, it must derive a class from the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) class.</span></span> <span data-ttu-id="36eec-127">您的衍生的類別應該定義需要維護狀態，以便在 Windows PowerShell 執行階段呼叫時，就可存取的提供者特定資料成員[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法來初始化提供者。</span><span class="sxs-lookup"><span data-stu-id="36eec-127">Your derived class should define the members necessary to maintain the state so that the provider-specific data can be accessed when the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="36eec-128">Windows PowerShell 提供者也可以維護連接為基礎的狀態。</span><span class="sxs-lookup"><span data-stu-id="36eec-128">A Windows PowerShell provider can also maintain connection-based state.</span></span> <span data-ttu-id="36eec-129">如需有關維護連線狀態的詳細資訊，請參閱[建立 PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="36eec-129">For more information about maintaining connection state, see [Creating a PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

## <a name="initializing-the-provider"></a><span data-ttu-id="36eec-130">初始化提供者</span><span class="sxs-lookup"><span data-stu-id="36eec-130">Initializing the Provider</span></span>

<span data-ttu-id="36eec-131">若要初始化提供者，Windows PowerShell 執行階段會呼叫[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)啟動 Windows PowerShell 時的方法。</span><span class="sxs-lookup"><span data-stu-id="36eec-131">To initialize the provider, the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method when Windows PowerShell is started.</span></span> <span data-ttu-id="36eec-132">大部分的情況下，您的提供者可以使用這個方法，只會傳回的預設實作[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件，描述您的提供者。</span><span class="sxs-lookup"><span data-stu-id="36eec-132">For the most part, your provider can use the default implementation of this method, which simply returns the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that describes your provider.</span></span> <span data-ttu-id="36eec-133">不過，在您要新增額外的初始化資訊的情況下，您應該實作您自己[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法會傳回的修改的版本[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)傳遞至您的提供者的物件。</span><span class="sxs-lookup"><span data-stu-id="36eec-133">However, in the case where you want to add additional initialization information, you should implement your own [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method that returns a modified version of the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that is passed to your provider.</span></span> <span data-ttu-id="36eec-134">一般情況下，此方法應傳回提供[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件傳遞給它或已修改[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件包含其他的初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="36eec-134">In general, this method should return the provided [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object passed to it or a modified [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that contains other initialization information.</span></span>

<span data-ttu-id="36eec-135">此基本提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="36eec-135">This basic provider does not override this method.</span></span> <span data-ttu-id="36eec-136">不過，下列程式碼會顯示這個方法的預設實作：</span><span class="sxs-lookup"><span data-stu-id="36eec-136">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

<span data-ttu-id="36eec-137">提供者可以維護提供者專屬資訊的狀態，如中所述[定義提供者特有資料狀態](#defining-provider-specific-state-information)。</span><span class="sxs-lookup"><span data-stu-id="36eec-137">The provider can maintain the state of provider-specific information as described in [Defining Provider-specific Data State](#defining-provider-specific-state-information).</span></span> <span data-ttu-id="36eec-138">在此情況下，您的實作必須覆寫[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法，以傳回衍生的類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="36eec-138">In this case, your implementation must override the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to return an instance of the derived class.</span></span>

## <a name="start-dynamic-parameters"></a><span data-ttu-id="36eec-139">啟動 動態參數</span><span class="sxs-lookup"><span data-stu-id="36eec-139">Start Dynamic Parameters</span></span>

<span data-ttu-id="36eec-140">提供者實作的[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法可能會需要額外的參數。</span><span class="sxs-lookup"><span data-stu-id="36eec-140">Your provider implementation of the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method might require additional parameters.</span></span> <span data-ttu-id="36eec-141">在此情況下，提供者應該覆寫[System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters)方法，並傳回的物件具有屬性和欄位的剖析屬性類似於cmdlet 類別或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="36eec-141">In this case, the provider should override the [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) method and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="36eec-142">此基本提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="36eec-142">This basic provider does not override this method.</span></span> <span data-ttu-id="36eec-143">不過，下列程式碼會顯示這個方法的預設實作：</span><span class="sxs-lookup"><span data-stu-id="36eec-143">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a><span data-ttu-id="36eec-144">未初始化的提供者</span><span class="sxs-lookup"><span data-stu-id="36eec-144">Uninitializing the Provider</span></span>

<span data-ttu-id="36eec-145">若要釋出 Windows PowerShell 提供者所使用的資源，您的提供者必須實作自己[System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop)方法。</span><span class="sxs-lookup"><span data-stu-id="36eec-145">To free resources that the Windows PowerShell provider uses, your provider should implement its own [System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) method.</span></span> <span data-ttu-id="36eec-146">停止初始化工作階段關閉提供者的 Windows PowerShell 執行階段會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="36eec-146">This method is called by the Windows PowerShell runtime to uninitialize the provider at the close of a session.</span></span>

<span data-ttu-id="36eec-147">此基本提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="36eec-147">This basic provider does not override this method.</span></span> <span data-ttu-id="36eec-148">不過，下列程式碼會顯示這個方法的預設實作：</span><span class="sxs-lookup"><span data-stu-id="36eec-148">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a><span data-ttu-id="36eec-149">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="36eec-149">Code Sample</span></span>

<span data-ttu-id="36eec-150">完整的範例程式碼，請參閱[AccessDbProviderSample01 程式碼範例](./accessdbprovidersample01-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="36eec-150">For complete sample code, see [AccessDbProviderSample01 Code Sample](./accessdbprovidersample01-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="36eec-151">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="36eec-151">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="36eec-152">一旦您的 Windows PowerShell 提供者註冊使用 Windows PowerShell 之後，您可以藉由在命令列上執行受支援的 cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="36eec-152">Once your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="36eec-153">此基本提供者，請執行新的殼層，並使用`Get-PSProvider`cmdlet 來擷取提供者的清單，並確保有 AccessDb 提供者。</span><span class="sxs-lookup"><span data-stu-id="36eec-153">For this basic provider, run the new shell and use the `Get-PSProvider` cmdlet to retrieve the list of providers and ensure that the AccessDb provider is present.</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="36eec-154">會出現下列輸出：</span><span class="sxs-lookup"><span data-stu-id="36eec-154">The following output appears:</span></span>

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a><span data-ttu-id="36eec-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36eec-155">See Also</span></span>

[<span data-ttu-id="36eec-156">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="36eec-156">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="36eec-157">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="36eec-157">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)